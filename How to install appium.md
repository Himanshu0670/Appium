# How to install and setup Appium on Windows

## [Youtube 📺](https://www.youtube.com/watch?v=NSMBSQdR314&list=PLnNg6KqJ3HGjH1qaJ50FoUmXPGnXbQZu7&index=2) 
### Pre-Requisities :-

- Install [Java (JDK)](https://www.oracle.com/java/technologies/downloads/#jdk23-windows)
- Install [Eclipse](https://www.eclipse.org/downloads/)
- Maven plugin for Eclipse (Internal plugin for eclipse) maven plugin is insalled by default in Eclipse 
- TestNG plugin for Eclipse (Internal plugin for eclipse)
- Selenium Jars (for web elements testing)

### Android Tools :-

- [Node Js](https://nodejs.org/en/download)
- [Android Studio](https://developer.android.com/studio) (IDE, Generate virtual devices)
- Appium Server
- [Appium GUI](https://github.com/appium/appium-desktop/releases/tag/v1.22.3-4)
- [Appium Inspector](https://github.com/appium/appium-inspector/releases) 
- Appium Client Library (.jar files or as a maven dependency in eclipse IDE)

### How to install java

- First install [Java (JDK)](https://www.oracle.com/java/technologies/downloads/#jdk23-windows)
- Go to Advanced system settings 
- Set the environment variables as:
   - JAVE_HOME = (Path of java)
   - PATH = `%JAVA_HOME%\bin` & `%JAVA_HOME%\lib`
- To check java install or not open command prompt & type = `java --version`
- NOTE: Set path on both User variables & System variables. 

### How to install Node Js

- First install [Node Js](https://nodejs.org/en/download)
- Go to Advanced system settings 
- Set the environment variables as:
   - NODE_HOME = (Path of nodejs)
   - PATH = `C:\Users\himan\AppData\Roaming\npm` & `C:\Program Files\nodejs\` 
- NOTE: Set path on both User variables & System variables. 

### How to install Android Studio

- First install [Android Studio](https://developer.android.com/studio)
- Go to Advanced system settings 
- Set the environment variables as:
   - ANDROID_HOME = `C:\Users\himan\AppData\Local\Android\Sdk`
   - PATH = `C:\Users\himan\AppData\Local\Android\Sdk\platform-tools` , `%ANDROID_HOME%\build-tools` & `%ANDROID_HOME%\platforms`  

### How to install Appium server

- Before installing appium server Node.js should be installed.
- NPM version should be >= 8
- Open command prompt & type
    - `npm install -g appium` (to install appium)
    - `appiun -v` (verify appium version)
    - `appium` (start appium server)
    - `appium driver install uiautomator2` (to install uiautomator2)
