# SSLWithFORMFallback8
Yet another SSLWithFORMFallback class, this time for Tomcat 8

To compile:

        javac -classpath "${TOMCAT}/lib/*" SSLWithFORMFallback8.java

To install:

        cd ${WEBINF}/classes
        mkdir -p org/apache/catalina/authenticator 
        install SSLWithFORMFallback8.class -D ${WEBINF}/classes/org/apache/catalina/authenticator

To actually use this is still a work in progress.  Here is my current status.

1. Change the authentication method in your webapp's web.xml file from FORM to CLIENT-CERT.
2. Add the new valve to the context.xml file.
3. Change the Connector in the server.xml file to specify client authentication.  In my case, I
changed clientAuth from "false" to "want" and added these attributes:

        secure="true" SSLVerifyClient="require" SSLEngine="on"
        truststoreFile="conf/piv-truststore" truststorePass="changeit"

Using "want" specifies that authentication is option.  If set to "true" then
the authentication process aborts if no card is provided.  Unfortunately, I'm
still missing something as I don't get the login form when the smartcard is absent.
