# hacep-ci-image
This project is used to quickly prototype using kafka to replace AMQ and DataGrid in hacep project:
https://github.com/redhat-italy/hacep

This repository contains an image to rapidly run jvm playground hacep project for continuous integration.

I made it for integration tests, so that I can change the AMQ and DataGrid, without regression on specifications.


##Build the image
```shell
mvn clean docker:build
```

##Build the image
```shell
mvn clean docker:run
```

You can then check localhost:8161 for the AMQ console. 

##Testing the image
Follow the instructions in: https://github.com/redhat-italy/hacep/tree/master/hacep-examples/hacep-perf-client
