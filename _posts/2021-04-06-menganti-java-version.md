---
title:  "Menganti java version di ubuntu 20.04" 
permalink: /posts/2021/04/menganti-java-version-di-ubuntu-20.04 
date: 2021-04-05-15
---

# Menganti java version 11 ke 8 di ubuntu 20.04 

Karena gue sering setting apps di open source dan gue sering bermain di java enviroment. jadi kadang gue harus mengganti java enviroment gue di ubuntu. langkah-langkah sebagai berikut: 

1. Chek version di java dengan pengetikan perintah berikut. 
   
```bash
update-alternatives --list java
```
kemudian pada terminal lu, bakal muncul kaya gini, ini menandakan di komputer lu ada dua buah versi java. 
**output :**

```bash
/usr/lib/jvm/java-11-openjdk-amd64/bin/java
/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java
```

2. Habis itu lu set enviroment untuk versinya. 
    
```bash
update-alternatives --set java /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java
```

3. Langkah selanjutnya lu chek kemabali versi java lu. 

```bash
java -version
openjdk version "1.8.0_191"
OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-0ubuntu0.18.10.1-b12)
OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
```


git bray. mudah bukan bund :)