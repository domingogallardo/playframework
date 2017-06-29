# Play Framework 

Docker image which provides sbt needed to launch Play applications

Includes: 

- OS: Alpine 3.4
- Java: Oracle Java 8
- Sbt version: 0.13.15
- Git
- Play Framework: 2.6.0
- Based on image: anapsix/alpine-java:8_jdk

The image contains the ivy2 and sbt dependencies for Play Framework 2.6.0. They are located in /root/.ivy2 and /root/.sbt directories. 

This image is not meant to be used for another version of Play. If you try to compile or run a Play project configured for another version it will donwload all the dependiencies new dependencies in the container. You can look and change the play version for the project in the `project/plugins.sbt` file.

## Volume

Exports a volume on `/code` in which you have to mount the Play 2.6.0 project directory.

## Run command

```
docker run --rm  -it -v "/path/to/my/play/project/:/code" -p 80:9000 domingogallardo/playframework
```

This launch the sbt console, where you can enter any sbt command: `compile`, `run` or `test`.

The exported port 9000 is the default play port. In the command is mapped to the default 80 port of the host machine so you can test your play app on `localhost` without telling any port.

### Happy coding! ;)
