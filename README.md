# docker

**Docker build scripts for ClefOS**

Files to build Docker containers for ClefOS 7.x

## Images


* __ansible__ - Simple IT Automation

* __base__ - ClefOS (CentOS Clone) Base Image

* __golang__ - GO Programming Language Development Environment

* __hadoop-openshift__ - Hadoop for use with OpenShift

* __hello-nodejs__ - A simple Hello World program in Node.js

* __httpd__ - Apache Webserver

* __java__ - IBM Java SDK

* __mariadb__ - A community-developed fork of the MySQL relational database management system

* __mongodb__ - A free and open-source cross-platform document-oriented database program

* __nginx__ - A free, open-source, high-performance HTTP server, reverse proxy, and IMAP/POP3 proxy server

* __nodejs__ - A JavaScript runtime built on Chrome's V8 JavaScript engine

* __registry__ - Docker registry

* __tomcat__ - An open source implementation of the Java Servlet, JavaServer Pages, Java Expression Language and Java WebSocket technologies

* __wildfly__ - Formerly known as JBoss AS, or simply JBoss, is an application server

* __wordpress__ - A free and open-source content management system (CMS) based on PHP and MySQL. Uses an external database


## Special Requirements

There are additional files required that you will need to supply in the following directories:

* `java` - IBM Java SDK self-installer - see the README in that directory

  * Note, `dummy-java-1.8-0.el7.noarch.rpm` is used to register the presence of the Java SDK as the installation of the IBM SDK is not via an RPM. Consequently, packages (such as tomcat) which check for the presence of the JDK when installed would fail. This RPM will register itself as providing: java-1.8.0 and java-devel-1.8.0.

* `nodejs` - IBM Node.js SDK self-installer - see the README in that directory

