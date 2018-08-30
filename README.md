Dockerized SonarQube Code Scanner
====================================================

Why?
----
Currently all Sonar Scanners and plugins for scan are java 8 compatible. 
If you have Java 9 or 10 installed - given dockerized scanner may be used.


Install and Run
-------

1. Install docker and docker-compose
2. Execute command from Project/docker folder:  "docker-compose build"
3. Execute command from Project/docker folder:  "docker-compose up"

       Note that all  Sonar configurations are in <project>/pom.xml    