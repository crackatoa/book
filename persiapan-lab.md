# Persiapan Lab

Lab. ini menggunakan:

* Genymotion
* Android 5.1 API 22
* Frida 12.7.23
* ADB 

### Instalasi Frida

Instalasi dapat dilakukan dengan menggunakan pip,

```text
pip install frida-tools
```

atau dengan mengkompilasi source yang ada pada github frida.

{% embed url="https://github.com/frida/frida" %}

### Melakukan Koneksi dengan Frida 

Frida memakai sebuah agent untuk melakukan koneksi antara PC dengan Smartphone, dalam hal ini disebut dengan **frida-server**. Terdapat beberapa jenis **frida-server** yang disesuaikan dengan arsitektur CPU yang digunakan, untuk lebih lengkapnya, dapat dilihat di github resmi frida.

{% embed url="https://github.com/frida/frida/releases" caption="" %}

Untuk melihat device list yang telah terhubung, dapat menggunakan **frida-ls-devices**.

```text
[𝝺] frida-ls-devices 
Id                   Type    Name                  
-------------------  ------  ----------------------
local                local   Local System          
192.168.56.101:5555  usb     Unknown Google Nexus 4
tcp                  remote  Local TCP  
```

**frida-server** yang digunakan untuk emulator android adalah **frida-server-android-x86**. ****Upload **frida-server** ke dalam emulator menggunakan **adb** pada /data/local/tmp atau direktori yang dikehendaki. Set permission 755 pada file tersebut. Kemudian jalankan dalam background.

\\* frida-server yang digunakan adalah versi **frida-server-12.7.23-android-x86**

```text
adb push frida-server-android-x86 /data/local/tmp/
adb shell "chmod 755 /data/local/tmp/frida-server-android-x86"
adb shell "/data/local/tmp/frida-server-android-x86 &"
```

Untuk memastikan **frida-server** telah berjalan, dapat menggunakan **frida-ps**.

```text
[𝝺] frida-ps -U
 PID  Name
----  -----------------------------------------
 117  adbd
 915  android.process.acore
 315  batteryd
2659  com.android.defcontainer
3093  com.android.deskclock
2543  com.android.gallery3d
 730  com.android.inputmethod.latin
2705  com.android.keychain
```

Pada tahap ini, **frida-server** telah terhubung dan siap untuk digunakan.

