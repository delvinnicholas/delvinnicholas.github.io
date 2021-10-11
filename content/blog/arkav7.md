---
title: "Arkavidia7.0"
date: 2021-10-11T23:45:25+07:00
slug: ""
description: "Write-Up CTF Arkavidia7.0"
keywords: [CTF]
draft: true
tags: [CTF, OSINT]
math: false
toc: false
---
## Tim Bo3d1
- **Kristian Anwar**
- **Delvin Nicholas**

Pada lomba ini, saya berkesempatan mengerjakan soal **OSINT-1** dan **Sad and Lonely**, sedangkan Kristian mengerjakan soal **KawaiiMetal**.

- **OSINT-1**\
Deskripsi soal : `Pada tanggal 9 Agustus 2019, sebuah artikel ilmiah dipublikasikan pada jurnal Computing and Software for Big Science. Salah satu penulis dari artikel ilmiah tersebut pernah menjadi narasumber pada suatu podcast. Sekitar tiga bulan setelah artikel tersebut dipublikasikan (1 Nov 2019), penulis ini mengunjungi suatu tempat di belahan bumi selatan. Cari tahu nama tempat tersebut.`
Solusi :\
Berdasarkan hint, kita dapat mencari di Google, jurnal "Computing and Software for Big Science" dan mendapatkan link pada researchgate.net. <img src="/images/arkav7/researchgate.png" />
Pada halaman tersebut, kita dapat melihat terdapat banyak author.
<img src="/images/arkav7/res2.png" />
Lalu dicoba mencari secara manual dengan keyword `“name” podcast` karena berdasarkan hint, target pernah mengisi suatu podcast. Jika sudah mendapat nama, kami lalu mencoba mencari nama serta melihat media sosial yang dipakai.
Hingga akhirnya kami menemukan “Mario Lassnig”, dan mendapatkan twitter nya.
<img src="/images/arkav7/mario.png" />
Terdapat tweet pada 1 November 2019 yang menyebut bahwa dia berkunjung ke tempat yang bernama @PawseyCentre, dan kemudian didapat nama dari tempat tersebut yaitu Pawsey Supercomputing Centre.
<img src="/images/arkav7/twtmario.png" />
<img src="/images/arkav7/paws.png" />
`FLAG : Arkav7{pawsey_supercomputing_centre}`

- **Sad and Lonely**
Deskripsi soal : `You are going to need a help from someone`\
Solusi :\
Pada discord arkavidia terdapat bot dengan role “Sad and Lonely :(“. Kemudian kita mendapat hint informasi bahwa bot tersebut merupakan versi 1.2. 
<img src="/images/arkav7/s2.png" /> Kemudian kita men-DM dengan command "help" dan menemukan pilihan "about". Kita mendapatkan sebuah link github. <img src="/images/arkav7/s3.png" />Dan pada link github terdapat informasi bahwa code pada github tersebut merupakan versi 1.3.<img src="/images/arkav7/s4.png" />
Kemudian kita mencoba command “wish me luck” yang dihapus pada versi 1.3, dan mendapatkan flag nya.\
`FLAG : Arkav7{th4nkz_d753bca330e52ec2abbb76306cf8456d}`

**KawaiiMetal**
Diberikan sebuah attachment berupa .zip dan .zip tersebut berisikan 4 gambar : 
- Babymetal.jpg
- Moa-metal.png
- Su-metal.jpg
- Yui-metal.jpg

Pertama kali, kami mencoba command file dan exiftool keempat gambar tersebut namun tidak mendapatkan sesuatu yang menarik >:v\
Lalu, saat menggunakan command binwalk Babymetal,jpg dan ditemukan adanya file .zip didalam gambar tersebut.
<img src="/images/arkav7/b1.png"/>
Dengan tools foremost, hidden file tersebut berhasil di ekstrak dengan nama 00000219.zip dan untuk meng unzip file nya diperlukan sebuah password. Password tersebut kami rasa berada diantara ketiga file gambar lainnya.
Terdapat 2 hint yang ditemukan dari tiap gambar kecuali Su-metal.jpg: 
- Moa-metal.png\
Hint, hint:
Every hidden messages you see are encoded with base64\
- Yui-metal.jpg\
Hint, hint:
U3RyaW5ncyBhbmQgZ3JlcCB3aXRoIHRoZSByZWdleCAiPSQiIGlzIGJlZXh0cmVtZWx5IHVzZWZ1bA==

Setelah didecode dengan base64:
Strings and grep with the regex "=$" is beextremely useful.\
Dari Hint Moa-metal.png, ditemukan banyak base64 yang ada di Su-metal.jpg. Dan string base64 yang aHR0cHM6Ly9wYXN0ZWJpbi5jb20vcHpSM01mYWc= didecode menjadi sebuah link : https://pastebin.com/pzR3Mfag.\
Isi link tersebut terdapat sebuah fake flag  : bruh{This_is_n0t_the_Fl4G}
Dan sebuah password dari 00000219.zip yaitu road_of_resistance.\
`Note : Road of Resistance juga lagunya babymetal.`\
Setelah meng unzip file tersebut, terdapat sebuah file flag.flac yang membuat confused saat dicek dengan audacity. Namun, saya baru ingat jika soal ini mirip dengan soal yang ada di picoCTF 2019 yaitu m00nwalk dan kebetulan saya pernah solve lewat Writeup AllanBlog dong (Link : https://tcode2k16.github.io/blog/posts/picoctf-2019-writeup/forensics/).\
Dengan menggunakan tools RX-SSTV, file tersebut berhasil didecode dengan flag didalamnya. Sebelumnya saya tidak berterimakasih dengan adanya tips yang ada di Su-metal.jpg, (Protip: Cover your ears when u find the flag and don't open random sound files willy-nilly) karena saya sedang menggunakan headphone >:v
<img src="/images/arkav7/b2.jpg"/>
`FLAG : : Arkav7{Gimm3_Ch0c0lat3}`
