---
title: Objection
---
![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/Android/images/objection.png?raw=true)

by Or Levy 

![alt text](https://raw.githubusercontent.com/ImLevys/ImLevys.github.io/210227953ae032e4c68ca06862be39ca408c63cc/Android/images/reference.svg)

[Objection Wiki](https://github.com/sensepost/objection/wiki) 

[Objection Tutotrial by hacktricks](https://book.hacktricks.xyz/mobile-apps-pentesting/android-app-pentesting/frida-tutorial/objection-tutorial)

<h2 style="color:#000000">Installation</h2>

```bash
pip3 install objection
```

<h2 style="color:#000000">Run</h2>

```bash
1. run frida-server on device
2. objection --gadget <app> explore  (start objection)
```

<h2 style="color:#000000">Commands</h2>

<h4 style="color:#008B8B">Path information</h4>

```bash
env
```

<h4 style="color:#008B8B">disable SSL Pinning</h4>

```bash
android sslpinning disable
```

<h4 style="color:#008B8B">disable root detection</h4>

```bash
android root disable
```

<h4 style="color:#008B8B">Simulate a rooted Android environment</h4>

```bash
android root simulate
```

<h4 style="color:#008B8B">Exec Command</h4>

```bash
android shell_exec whoami 
```

<h4 style="color:#008B8B">Screenshot</h4>

```bash
android ui screenshot /tmp/screenshot 
```

<h4 style="color:#008B8B">List activities</h4>

```bash
android hooking list activities
```

<h4 style="color:#008B8B">List services</h4>

```bash
android hooking list services
```

<h4 style="color:#008B8B">List receivers</h4>

```bash
android hooking list receivers 
```

<h4 style="color:#008B8B">Getting current activity</h4>

```bash
android hooking get current_activity 
```

<h4 style="color:#008B8B">Search Classes</h4>

```bash
android hooking search classes <package.name>
```

<h4 style="color:#008B8B">Search Methods of a Class</h4>

```bash
android hooking search methods <package.name <activity.name> 
```

<h2 style="color:#000000">Hooking Commands</h2>

<h4 style="color:#008B8B">try to dump all possible information each time the function is called</h4>

```bash
android hooking watch class_method <package>.<activity>.<function> --dump-args --dump-backtrace --dump-return
```
<h4 style="color:#008B8B"> try to dump all possible information each time the class is called</h4>

```bash 
android hooking watch class <package>.<activity> --dump-args --dump-backtrace --dump-return
```

<h4 style="color:#008B8B">Changing boolean return value of a function</h4>

```bash
android hooking set return_value <package>.<activity>.<function> <true/false> 
```

<h4 style="color:#008B8B">allow users to view materials while the app is minimized</h4>

```bash
android ui FLAG_SECURE false
```

<h2 style="color:#000000">Keystore/Intents</h2>

```bash
android keystore list
android intent launch_service
android intent launch_activity <package>.<activity> (launch an activity 
	can be exploit if android:exported="true")
```


<h2 style="color:#000000">Memory</h2>

```bash
memory list modules (process in the memory)
memory list exports <process> (export a process)
memory search 4141 –string (search string in the memory)
memory write <address> <string> --string (write to the memory process)
```

<h2 style="color:#000000">SQLite</h2>

```bash
sqlite (interact with sqlite db)
```





