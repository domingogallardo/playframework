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

This image is not meant to be used for another version of Play. If you try to compile or run a Play project configured for another version it will donwload all the new dependencies in the container. This takes a lot of time and is useless, because the next time the container is created, all the dependencies have disapeared and the process has to begin again.

You can look and change the play version of a project in the `project/plugins.sbt` file.

## Volume

Exports a volume on `/code` in which you have to mount the Play 2.6.0 project directory.


## Run commands

The CMD in the Dockerfile launch the sbt command. The run command launch the sbt console in the container, where you can enter any sbt command: `compile`, `run`, `test`, `clean`:

```
docker run --rm  -it -v "/path/to/my/play/project/:/code" -p 80:9000 domingogallardo/playframework
```

The exported port 9000 is the default play port. In the command is mapped to the default 80 port of the host machine so you can test your play app on `localhost` without telling any port.

You can also launch an explicit sbt command in the container. 

For instance, to execute the tests:

```
docker run --rm -v "/path/to/my/play/project/:/code" domingogallardo/playframework sbt test
```

Or to run the application:

```
docker run --rm -it -v "/path/to/my/play/project/:/code" -p 80:9000 domingogallardo/playframework sbt run
```


### Happy coding! ;)
