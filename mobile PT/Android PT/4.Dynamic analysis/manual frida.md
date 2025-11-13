
![[../../../attchments/Pasted image 20250206101339.png]]
![[../../../attchments/Pasted image 20250206101350.png]]go to lib

![[../../../attchments/Pasted image 20250206101405.png]]
in this case the artitechture is x86_64

![[../../../attchments/Pasted image 20250206101446.png]]

 ![[../../../attchments/Pasted image 20250206101745.png]]
 ![[../../../attchments/Pasted image 20250206101758.png]]
 ![[../../../attchments/Pasted image 20250206101815.png]]
 ![[../../../attchments/Pasted image 20250206101833.png]]
 ![[../../../attchments/Pasted image 20250206102313.png]]
 ![[../../../attchments/Pasted image 20250206102342.png]]
 ![[../../../attchments/Pasted image 20250206102409.png]]
 when you came to this directory look for an smali file that gets loded during the boot process
![[../../../attchments/Pasted image 20250206102513.png]]
in this case it is mainactivity.smali


![[../../../attchments/Pasted image 20250206102712.png]]
whenn we open the smali file we are looking for something like this method opublic consttructor

![[../../../attchments/Pasted image 20250206104420.png]]

![[../../../attchments/Pasted image 20250206104549.png]]
![[../../../attchments/Pasted image 20250206104842.png]]

```
$ keytool -genkey -v -keystore custom.keystore -alias mykeyaliasname -keyalg RSA -keysize 2048 -validity 10000
```

```
# sign the APK
$ jarsigner -sigalg SHA1withRSA -digestalg SHA1 -keystore demo.keystore -storepass kali123 repackaged.apk demokeys

# verify the signature you just created
$ jarsigner -verify repackaged.apk

# zipalign the APK
$ zipalign 4 repackaged.apk repackaged-final.apk
```

```

jarsigner -verify injured_patched.apk 

~/Android/Sdk/build-tools/35.0.1/zipalign 4 repackaged.apk repackaged-final.apk
```

