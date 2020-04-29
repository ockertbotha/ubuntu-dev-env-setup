#Install and configure Java
In the past I have recommended using https://github.com/asdf-vm/asdf to manage Java versions, but this time around going to broadly follow instructions from: https://linuxize.com/post/install-java-on-ubuntu-18-04/

## 1. Installing OpenJDK 8
```
sudo apt update
sudo apt install openjdk-8-jdk
```

## 2. Set the default Java version
```
sudo update-alternatives --config java
```
Follow the instructions to change it.

## 3. Set the JAVA_HOME Environment Variable
Note the Java installation paths from:
```
sudo update-alternatives --config java
```

Update the environment file:
```
sudo nano /etc/environment
```

Add the path for your preferred Java install to the end:
```
JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"
```

Reload the environment file into the current session:
```
source /etc/environment
```

Verify the configuration and installation:
```
echo $JAVA_HOME
java -version
```

## 4. Uninstall Java (If you ever need to)
```
sudo apt remove openjdk-8-jdk
```
Obviously update your JAVA_HOME if needed.

## 5. Install Apache Maven
```
sudo apt update
```

```
sudo apt install maven
```

```
mvn -version
```
