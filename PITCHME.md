## Android and Xposed Framework
*XDA Developers*<br />
![conflogo](/images/kszwbimzbc2wnlor7say.jpg)
![xdalogo](/images/XDA_Logo_reversed.png)

---
## What is Xposed
- Developed by XDA Senior Recognized Developer rovo89
- System patch allowing user apps to hook into any Android JAVA call, any application <!-- .element: class="fragment" -->
- Requires patched system, including dalvik, Zygote, etc. <!-- .element: class="fragment" -->
- Allows hooking all types of apps, included system and Play Store apps <!-- .element: class="fragment" -->
- Allows replacing resources to affect look and layout - on the fly <!-- .element: class="fragment" -->

Note:
Xposed is a system patch that allows user applications to hook into any Android java call in any application. It requires a patched system, including dalvik, Zygote etc. Due to the way it's implemented, it allows hooking all types of apps, including system and playstore apps. Furthermore, it allows replacing resources in apps to change the way they look and are layouted.

+++
### Getting Started with Xposed
- Deciding what to change
- Look at raw code of the app <!-- .element: class="fragment" -->
  - Apktool (https://ibotpeaches.github.io/Apktool/) <!-- .element: class="fragment" -->
  - Dex2jar (https://github.com/pxb1988/dex2jar) <!-- .element: class="fragment" -->
  - Java Decompiler Online (http://www.javadecompilers.com/apk) <!-- .element: class="fragment" -->
  - If dealing with mostly stock Android package, e.g. SystemUI, see https://android.googlesource.com/ for hints <!-- .element: class="fragment" -->
- Now start writing code <!-- .element: class="fragment" -->

Note:
The hardest part of writing an Xposed Module is actually finding the right place to change the application. Now, if the application is open source, this is no issue, but what do you do when it's a proprietary application or a system application? The solution has multiple steps:

+++
### Getting the apk
- Requires ADB setup and working in your Android terminal
- Get exact package name <!-- .element: class="fragment" -->
  - use ADB shell if not known

+++
```
$ adb shell pm list packages
$ adb shell pm path com.android.systemui
package:/system/priv-app/SystemUI/SystemUI.apk
$ adb pull /system/priv-app/SystemUI/SystemUI.apk
```

Note:
For those who aren't familiar with the process, getting the APK from an android device is rather simple First make sure you have ADB setup and available in your favourite commandline terminal. If you don't know the exact package name of the target application, there are some steps to perform to find the package and then pull it.

+++
### Decompiling
- Decompile using favorite decompiler previously listed
  - Apktool (https://ibotpeaches.github.io/Apktool/)
  - Dex2jar (https://github.com/pxb1988/dex2jar)
  - Java Decompiler Online (http://www.javadecompilers.com/apk)

+++
### Hooking
- Xposed presents a few ways to hook:
  - `beforeHookedMethod`
    - called before the real function
    - allows modifying e.g. arguments passed, changing objects etc.
  - `afterHookedMethod`
    - called after the real function
    - allows affecting objects after the real code has been run, modify return value of function etc.
  - `replaceHookedMethod`
    - completely replaces the real function and allows to completely replace functionality

Note:
Xposed has a few different ways to hook functions:

beforeHookedMethod is called before the real function is called and allows modifying e.g. arguments passed, changing objects etc.
afterHookedMethod is called after the real function is called and allows affect objects after the real code has been run, modify return value of function etc.
replaceHookedMethod which completely replaces the real function and allows to completely replace functionality.

---
## Resources
- Introductory Repo: http://bit.ly/xposedIntro
- Settings Demo: http://bit.ly/Xposed-SampleSettings
- Clock Demo: http://bit.ly/XposedClockDemo

---
## Q&A
![xdalogo](/images/XDA_Logo_reversed.png)
