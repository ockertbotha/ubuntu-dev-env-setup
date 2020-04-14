# Creating a new Spring Boot (Docker) Project
The steps to creating a new Spring Docker Project project in my current Ubuntu dev environment.

## Note:
This requires several tools to be installed and the steps here will be combination
of those in the following guides:
 - Spring Boot: https://spring.io/guides/gs/spring-boot-docker/
 - VS Code: https://code.visualstudio.com/docs/java/java-spring-boot   

## Prerequisites:
Please check that the following are installed before you continue:
 - Java Development Kit (JDK) 1.8
 - Apache Maven 3.0 or later

 Also the following VS Code extensions:
 - Java Extension Pack (https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack)
 - Spring Boot Tools (https://marketplace.visualstudio.com/items?itemName=Pivotal.vscode-spring-boot)
 - Spring Initializr (https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-spring-initializr)
 - Spring Boot Dashboard (https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-spring-boot-dashboard)


## 1. Create the project using VS Code: Spring Initializr
Open the Command Palette (ctrl+shift+p) and type *Spring Initializr* to start
the wizard and enter the following specific values or accept the defaults:
```
Language: Java
```
```
Group Id: org.springframework
```
```
Artifact Id: my-spring-boot-docker
```
```
Dependencies: Spring Boot DevTools
```

For location select your projects folder
```
Generate into: <projects folder>
```
With the values mentioned here this will generation your project into:
```
..\<projects folder>\my-spring-boot-docker
```

## 2. A quick refactor
Pick-up from here.
