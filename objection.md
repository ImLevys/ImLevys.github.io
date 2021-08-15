title: Objection
---
![[objection.png]]
```ad-info
[Objection Wiki](https://github.com/sensepost/objection/wiki) 
[Objection Tutotrial by hacktricks](https://book.hacktricks.xyz/mobile-apps-pentesting/android-app-pentesting/frida-tutorial/objection-tutorial)
```

**Installation**
```bash
pip3 install objection
```
**Run**
```bash
1. run frida-server on device
2. objection --gadget <app> explore  (start objection)
```

**Commands**
information (like passwords or paths) could be find inside the environment
```bash
env
```
Attempts to disable SSL Pinning on Android devices
```bash
android sslpinning disable
```
Attempts to disable root detection on Android devices
```bash
android root disable
```
Attempts to simulate a rooted Android environment
```bash
android root simulate
```
Exec Command
```bash
android shell_exec whoami 
```
Screenshot
```bash
android ui screenshot /tmp/screenshot 
```
List activities
```bash
android hooking list activities
```
List services
```bash
android hooking list services
```
List receivers
```bash
android hooking list receivers 
```
Getting current activity
```bash
android hooking get current_activity 
```
Search Classes
```bash
android hooking search classes <package.name>
```
Search Methods of a Class
```bash
android hooking search methods <package.name <activity.name> 
```


**Hooking Commands**
try to dump all possible information each time the function is called
```bash
android hooking watch class_method <package>.<activity>.<function> --dump-args --dump-backtrace --dump-return
```
Changing boolean return value of a function
```bash
android hooking set return_value <package>.<activity>.<function> <true/false> 
```
allow users to view materials while the app is minimized
```bash
android ui FLAG_SECURE false
```

**Keystore/Intents**
```bash
android keystore list
android intent launch_service
android intent launch_activity <package>.<activity> (launch an activity 
	can be exploit if android:exported="true")
```


**Memory**
```bash
memory list modules (process in the memory)
memory list exports <process> (export a process)
memory search 4141 –string (search string in the memory)
memory write <address> <string> --string (write to the memory process)
```

**SQLite**
```bash
sqlite (interact with sqlite db)
```





