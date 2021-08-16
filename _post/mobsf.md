---
title: MobSF
---

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/Android/images/logo.png?raw=true)

![alt text](https://raw.githubusercontent.com/ImLevys/ImLevys.github.io/b9bf555a98ab16648985913a5b4774777a64cb72/Android/images/reference.svg)

[MobSF Wiki](https://mobsf.github.io/docs/#/)

<h2 style="color:#000000">Windows Installation</h2>

```batch
git clone https://github.com/MobSF/Mobile-Security-Framework-MobSF.git 
cd Mobile-Security-Framework-MobSF 
setup.bat
```

<h2 style="color:#000000">Run</h2>

```batch
run.bat 127.0.0.1:8000
```

<h2 style="color:#000000">Dynamic Analysis</h2>

![alt text](https://raw.githubusercontent.com/ImLevys/ImLevys.github.io/bc98cca12e1a119f045a20f77f79cd5e1c23f248/Android/images/mobsf_warning.svg)

<h4 style="color:#008B8B">Find Port of the device</h4>

```powershell
nox_adb devices
```

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/Android/images/config2.png?raw=true)

<h4 style="color:#008B8B">Open file:</h4>

```powershell
<user_home_dir>/.MobSF/config.py
```

<h4 style="color:#008B8B">Add the following parameters:</h4>

![alt text](https://raw.githubusercontent.com/ImLevys/ImLevys.github.io/2c2c8ab9f7795b2b3ca78cd60dcc18eb1e811317/Android/images/mobsf_info.svg)


![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/Android/images/config1.png?raw=true)


ADB_BINARY = PATH TO NOX ADB.exe
![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/Android/images/config0.png?raw=true)
