# Configure VS Code for Java
The steps to getting VS Code setup:

## 1. Follow official guides at:
https://code.visualstudio.com/docs/java/java-tutorial#_before-you-begin

https://code.visualstudio.com/docs/java/java-spring-boot

## 2. Additional settings:

### 2.1 Workspace settings
With user settings open, select *WORKSPACE* option, found next to
*USER* title of settings page. This adds new file to a project
root *.vscode/settings.json* where we add the following:
```
// .vscode/settings.json
{
  ...
  "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "java.home": "/usr/lib/jvm/java-8-openjdk-amd64",
    "files.exclude": {
        "**/.classpath": true,
        "**/.project": true,
        "**/.settings": true,
        "**/.factorypath": true
    },
  ...
}
```
