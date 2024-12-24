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
## How to find `appPackage` and `appActivity` in a app Real/Virtual device
To find the `appPackage` and `appActivity` in a app Real/Virtual devices using adb (Android Debug Bridge) on Windows, follow these steps:

1. Open command prompt & type:
`adb devices`
This should list your virtual device. If it’s not listed, ensure the emulator is running and try again.

2. To open shell type:
`adb shell`

3. Open the app make that in focus
  
4. To get `appPackage` and `appActivity` of focus device type:
`dumpsys window displays | grep -e 'mCurrentFocus'`
   
