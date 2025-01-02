## Mobile Testing

### Mobile Web App :- 
Web apps rely on web browsers as their user interface. They need the internet to perform tasks. The best
thing about web apps is that they can run on various devices like computers, phones, and tablets. Additionally,
they can adjust to the screen size.
                                    
### Native App :-
A native app is developed specifically for one platform.It can be installed through an application store(such as Google play store or Apple app store)
Example: WhatsApp, Facebook These app can be use all the system application's(the app which comes by default with your mobile). 

### Hybrid App :-
Hybrid apps combine elements from the web and native apps. They are built using a wide range of front-end
technologies. In other words, developers don't have to maintain or create a separate code base for Android
and iOS, meaning that developers can write the mobile app code once and make it work on multiple
platforms.
Example: Gmail, Twitter, Instagram, WhatsApp, Facebook.

### What is Mobile Testing :-
Mobile testing is the process by which applications for modern mobile devices are
tested for functionality, usability, performance etc.


## Approaches to Test the mobile application
 Mobile application testing can be automated or manual, and helps you ensure that the application you're
 delivering to users meets all business requirements as well as user expectations.
 
### Manual Testing :- 
Manual testing is a human process. The primary focus of manual testing is on the experience of the user. Manual
testing can take advantage of human intuitiveness to uncover unexpected errors, but can also be extremely time-
consuming.

### Automated Testing :-
Automated testing saves much of this time and is particularly effective on repetitive tests, but can miss less
obvious cases that manual testing might catch.

### What is APK :- 
APK stands for `Android Package Kit` or `Android Application Package` created
for the Android operating system. Android uses this file extension to distribute and
install apps. Therefore, an АРК contains all the elements an app requires to be
installed correctly.
The developer typically uses `Android Studio` to create an Android app. Once the
app is ready, Android Studio compiles the application and puts it into one container
as an APK. APKs can have any name with the file extension **.apk**.

Download dummy apk files:
- www.apkpure.com
- www.apk4fun.com

## Real Device Vs Simulator Vs Emulator Testing

### Real Device Testing :-
Testing performed on physical device i.e. your handset.Real device testing assures you that your application will work smoothly on customer handset.

### Simulator & Emulator Testing :-
Simulators & Emulators are not an actual devices. Simulators & Emulators are virtual devices. Virtual device are not real phones but they are software which gives functionalities as real phone (except few functionality like camera...)

- **Android virtual device are `Emulator`**
- **iOS virtual device are `Simulator`**

## Why Appium(Advantages)
- Cross platform: Android & iOS we can test native, hybrid & web app.
- Allow you to communicate with other apps, Ex: WhatsApp, (Majority of tools doesn't support this).
- No pre-compilation of your app.
- Support for built in app: alarm, phone, calendar etc.
- Any WebDriver compatible language is supported: java, obective C, Ruby,php, C#.

## Limitations of Appium
- For Android, no support for Android API level <17(for android v>4.1)if your mobile having less than 17 then we need to go for selendroid.
- Script execution is very slow on iOS & Android virtual devices.
- No support for toast messgage.
- No parallel execution directly.

# What is Appium
Appium is an open-source test automation tool that allows developers and testers to automate tests for mobile applications. Appium is mobile web, native & hybrid software application test automation tool developed and supported by [Sauce Labs](https://saucelabs.com/). It is open-source automation tool which is useful to automate Android & iOS platform apps.

## How to open virtual device using command prompt:
- Go to the follwing location: `C:\Users\himan\AppData\Local\Android\Sdk\emulator`
- Open command prompt on above location
- Run the following command: `emulator -avd devicename` ex `emulator -avd Pixel 6` 

## How to install apk on virtual device:

### Method 1 : Using Appium Inspector
1. First open the Appium server.
2. Open & run an virtual device on the Adnroid studio
3. Open command prompt & type: `adb devices`, this should list your virtual device. If it’s not listed, ensure the emulator is running and try again.
5. Open "Appium inspector"
6. Set remote path on "Appium inspector" for v1.22.3 as: `/wd/hub`
7. Set capabilities on "Appium inspector" as:
 ```
  {
  "platformName": "Android",
  "appium:automationName": "uiautomator2",
  "appium:deviceName": "Pixel 6",
  "appium:app": "path of the apk"
}  
 ```
8. Start the session & check the apk is installled or not in your running virtual device.

### Method 2 : Using Adb server("Android Debug Bridge" command line tool to communicate with your device) 
1. Open command prompt
2. Start server using command: `adb.exe start-server`
3. Open & run an virtual device on the Adnroid studio
4. If server is already started then to kill server: `adb.exe kill-server`
5. Go to apk file folder, run the command: `adb.exe install filename.apk`

### Method 3 : Drag & drop  
1. Open & run an virtual device on the Adnroid studio
2. Go to apk file folder 
3. Drag & drop that apk file to virtual device
-----

## What is appPackage & appActivity

- appPackage - The package name of the app you want to inspect.
- appActivity - The main activity of the app you want to inspect.This is used to start the app & bring it to the forground.

## How to find `appPackage` and `appActivity` in a app Real/Virtual device

There are two ways to find the `appPackage` and `appActivity` in a app Real/Virtual devices:-

- **Real device only you can download & install `Apk info` named app.**
- **Real/Virtual devices using adb (Android Debug Bridge) on Windows, follow these steps:**

1. Open command prompt & type:
`adb devices`
This should list your virtual device. If it’s not listed, ensure the emulator is running and try again.

2. To open shell type:
`adb shell`

3. Open the app make that in focus

4. To get `appPackage` and `appActivity` of focus device type:
`dumpsys window displays | grep -e 'mCurrentFocus'`

## What is Maven project in appium

A Maven project in Appium refers to an Appium-based test automation project that is managed using Maven, a build automation tool. In such a project, Maven is used to manage dependencies, build processes, and automate the execution of tests. Appium is a popular framework for automating mobile applications (both Android and iOS), and when combined with Maven, it helps ensure efficient management and execution of tests for mobile apps.

## Why we use Maven project in appium

Maven is often used in Appium projects for several key reasons:

### 1. Dependency Management:
Appium dependencies: Appium is a framework that relies on several dependencies (like Appium server, Appium client libraries, etc.). Maven handles these dependencies by downloading and managing them automatically. With Maven, you define all necessary dependencies in the pom.xml file, and it will resolve and download the correct versions.
This reduces the need for manually managing JAR files, making the setup and maintenance easier and more efficient.

### 2. Build Automation:
Automated Builds: Maven allows you to automate the building of your project. This includes compiling code, running tests, creating packages, and more. In Appium, this can help with automating the process of running your mobile tests as part of a CI/CD pipeline.
Consistent Builds: By using a standard build configuration, Maven ensures that the project can be built in the same way on any machine, ensuring consistency and reducing errors.

###3. Project Structure:
Standardized Directory Structure: Maven encourages a standardized directory layout for your project. This improves the organization of your files, especially when collaborating with teams or scaling the project. For example, your test scripts, resources, and libraries are neatly organized in Maven’s default directory structure.
Integration with Appium tests: In an Appium project, you typically have source code, resources like app files (APK or IPA), and test scripts. Maven makes it easier to structure and manage these components.

### 4. Version Control:
Version Management: Maven handles versioning of dependencies, ensuring that you're using the right versions of Appium and related libraries. If you're working with a team or multiple environments, Maven can lock the version of dependencies to avoid compatibility issues.
It helps ensure that everyone uses the same versions of Appium and related libraries, avoiding conflicts that might arise from different team members using different versions.

### 5. Plugins for Testing:
Maven provides plugins to run unit tests (such as JUnit or TestNG) and integration tests. You can configure Maven to automatically execute your Appium tests as part of the build process.
Maven Surefire Plugin is commonly used to run Appium tests within Maven, ensuring that tests are executed as part of the build lifecycle.
### 6. CI/CD Integration:
Maven easily integrates with Continuous Integration/Continuous Delivery (CI/CD) tools like Jenkins, Bamboo, or GitLab CI. This is especially useful for automated testing with Appium, as it helps ensure that tests run automatically when code changes are pushed, providing early feedback on code quality.
You can configure your CI pipeline to execute Maven commands, which in turn can run your Appium tests, helping to streamline testing in agile workflows.

### 7. Reporting:
With Maven, you can integrate reporting tools (like Surefire, JaCoCo, etc.) to generate detailed reports of your Appium tests. This is useful for monitoring the progress and results of your automated tests.

In summary:
Maven streamlines the process of managing dependencies, automating builds, and integrating with CI/CD tools in Appium projects. It provides an efficient way to handle complex test automation projects with Appium, ensuring consistency, ease of maintenance, and scalability.

