# SSLWithFORMFallback8
Yet another SSLWithFORMFallback class, this time for Tomcat 8

To compile:

        javac -classpath "${TOMCAT}/lib/*" SSLWithFORMFallback8.java

To install:

        cd ${WEBINF}/classes
        mkdir -p org/apache/catalina/authenticator 
        install SSLWithFORMFallback8.class -D ${WEBINF}/classes/org/apache/catalina/authenticator
