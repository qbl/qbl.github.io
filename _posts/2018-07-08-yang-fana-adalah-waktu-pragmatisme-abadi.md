---
layout: post
title: Yang Fana adalah Waktu, Pragmatisme Abadi
description: 
categories:
  - Books
tags:
  - Book Review
  - The Pragmatic Programmer
  - Software Engineering
---

Sudah sekitar tujuh bulan terakhir saya *banting setir*. Setelah delapan tahun lebih menyebut diri sendiri sebagai seorang *Ruby programmer*, pada awal Januari tahun ini saya beralih menjadi seorang *system engineer*. Salah satu dampak utama dari alih profesi ini, saya harus belajar banyak hal baru. Bagaimana tidak, ketika pertama kali mendapat *brief* tentang peran baru saya ini, barangkali sekitar 80% teknologi yang diucapkan pada *brief* tersebut belum pernah saya gunakan secara profesional.

Tiap orang tentu punya cara yang berbeda dalam mempelajari sesuatu. Bagi saya, cara yang sejauh ini terbukti efektif buat diri sendiri adalah dengan membaca beberapa buku tentang topik yang sedang saya pelajari. Untuk mempelajari tentang Kubernetes, misalnya, saya membaca dua judul buku, "Kubernetes: Up and Running" dan "Kubernetes in Action". Belajar dari beberapa buku memberi saya perspektif yang lebih beragam mengenai satu topik. Konsep semacam *namespace* pada *container*, misal yang lain, terasa lebih mudah dan lebih komprehensif untuk dipahami ketika saya mempelajarinya dari beberapa sumber.

Salah satu *rule of thumb* yang saya pegang dalam mencari buku bacaan untuk mempelajari sebuah topik adalah tidak menggunakan buku yang terbit lebih lampau dari tiga tahun lalu. Aturan ini menjadi relevan teruma ketika topik yang dipelajari adalah teknologi informasi. Pasalnya, perkembangan teknologi informasi memang relatif cepat. Jika kita menggunakan buku yang tidak *up to date*, besar kemungkinan ada perubahan pada teknologi yang kita pelajari yang belum terdokumentasikan di buku tersebut.

Sebagai contoh spesifik, kalau hari ini kita mempelajari *framework* Ruby on Rails dari buku "Agile Development Method with Rails 4" terbitan tahun 2013, kita akan menemukan beberapa kendala karena versi Rails yang diulas pada buku tersebut masih Rails 4 sementara versi Rails *default* yang bisa kita unduh dari situs resmi Rails saat ini adalah Rails 5.1. Beberapa fitur baru yang ada di Rails 5.1 tentu tidak akan kita temui pada buku tersebut. Sementara beberapa fitur yang sudah *deprecated* pada Rails 5.1 barangkali masih diulas di sana.

Oleh karena itu, rasanya tak keliru kalau saya katakan sangat sulit untuk menulis sebuah buku tentang teknologi informasi yang bersifat teknis sekaligus tetap relevan dalam waktu yang lama. Buku semacam "Agile Development Method with Rails" menyiasatinya dengan perbaruan terus menerus. Edisi terakhir "Agile Development Method with Rails 5.1" dirilis pada November 2017 lalu, hanya berjarak sekitar satu tahun dari "Agile Development with Rails 5" yang dirilis pada September 2016.

***

Satu dari sedikit buku yang berhasil melawan kutukan keusangan adalah buku The Pragmatic Programmer karya David Thomas dan Andrew Hunt. Dipublikasikan pertama kali pada Oktober 1999, The Pragmatic Programmer masih terasa relevan bagi saya saat ini. Hampir dua puluh tahun sejak terbitan perdananya, apa-apa yang ditulis oleh Thomas dan Hunt di The Pragmatic Programmer masih beresonansi dengan masalah yang kita temui di industri teknologi informasi hari-hari ini.

Saya ambil contoh prinsip *don't repeat yourself* atau DRY. Secara verbatim, prinsip ini didefinisikan oleh Thomas dan Hunt di The Pragmatic Programmer dengan redaksi sebagai berikut, *"every piece of knowledge must have a single, unambiguous, authoritative representation within a system"*. Salah satu penerapan awal dari prinsip ini adalah dengan melakukan otomasi terhadap dokumentasi kode. Dalam perkembangannya, prinsip ini menjadi salah satu faktor yang mendorong lahirnya disiplin Infrastructure as Code dan *declarative programming*.

Apa yang membuat The Pragmatic Programmer tak lekang waktu? Saya kira salah satunya adalah karena pola pikir kedua penulisnya yang memandang bahwa ilmu, pengetahuan, dan pengalaman seorang *programmer* harus dikelola selayaknya portofolio investasi finansial. Thomas dan Hunt secara eksplisit menyebutnya sebagai "portofolio pengetahuan". 

Layaknya seorang investor finansial, menurut Thomas dan Hunt, seorang *programmer* yang baik harus berinvestasi secara reguler. Implikasinya, seorang *programmer* harus senantiasa mempelajari hal baru, melakukan diversifikasi teknologi yang dipelajarinya, dan mengelola resiko investasi dengan baik. Mempelajari teknologi *cutting edge*, misalnya, bisa dikategorikan sebagai investasi *high risk* yang harus diimbangi dengan mempelajari lebih dalam teknologi yang lebih *mature* dan memang digunakan dalam pekerjaan kita sehari-hari. Thomas dan Hunt bahkan merinci beberapa langkah kongkret yang perlu dilakukan oleh seorang *programmer* untuk memperkaya portofolio pengetahuannya. Langkah-langkah tersebut di antaranya: mempelajari minimal satu bahasa pemrograman setiap tahun, membaca satu buku teknis setiap satu kuartal, membaca buku-buku non teknis, dan berjejaring dengan komunitas teknologi.

Dengan pola pikir di atas, saya kira tak mengherankan jika Thomas dan Hunt berhasil menuliskan prinsip-prinsip fundamental yang cenderung terus relevan dengan permasalahan yang ditemui oleh para *programmer* hingga hari ini, meski mungkin dalam bentuk yang sedikit berbeda. Prinsip meminimalisir *coupling* antar tiap bagian dalam kode kita, misalnya, di masa The Pragmatic Programmer ditulis barangkali baru dipraktekkan dalam bentuk penerapan Law of Demeter ketika menulis fungsi atau *method*. Namun prinsip yang sama, saya duga, menjadi salah satu fondasi bagi lahirnya arsitektur seperti MVC dan *microservices* di kemudian hari.

***

Awal bulan lalu saya mengambil mata kuliah tentang Cloud Computing dari University of Illinois melalui platform *e-learning* Coursera. Sebagai proyek akhir mata kuliah ini, siswa ditugaskan untuk mengimplementasikan Gossip Protocol dengan menggunakan bahasa C++. Gossip Protocol adalah sebuah prosedur komunikasi untuk mendistribusikan informasi secara cepat pada sebuah *distributed system*. Tugas tadi menarik karena ketika saya mulai mengambil mata kuliah ini, pada saat yang bersamaan saya sedang mengerjakan beberapa tugas kantor yang berkaitan dengan Consul. Bagi kawan-kawan yang belum familiar, Consul adalah sebuah *service discovery tools* yang biasa digunakan pada sistem dengan arsitektur *microservices*. Nah, [Consul dibangun dengan menggunakan Gossip Protocol](https://www.consul.io/docs/internals/gossip.html) untuk mengelola keanggotaan sebuah *service* pada *cluster* dan untuk melakukan *broadcast* pesan ke seluruh *cluster*.

Ketika mengambil mata kuliah ini, saya menyadari panjangnya jalan yang dibutuhkan untuk mengubah konsep akademis seperti Gossip Protocol menjadi sebuah *tools* yang diadopsi secara luas oleh industri seperti Consul. Hal yang sama juga saya temui pada [Raft Protocol yang menjadi basis dari *tools* bernama etcd](https://github.com/coreos/etcd/tree/master/raft) yang kemudian menjadi salah satu komponen penting dalam membuat sebuah *cluster* Kubernetes. Perlu *craftmanship* dan *mastery* pada pemrograman dan *software engineering* untuk bisa menciptakan *tools* semacam ini.

Kembali ke buku The Pragmatic Programmer, sejujurnya saya agak khawatir *review* pendek ini gagal menjadi duta yang representatif bagi buku ini. Penyebabnya, masih banyak poin penting yang belum saya singgung pada tulisan yang singkat ini. Hampir setiap gagasan utama yang diulas di The Pragmatic Programmer bisa dibahas secara panjang lebar dalam satu atau bahkan beberapa tulisan tersendiri.

Kalau ada satu saja poin yang tak boleh tertinggal dari *review* ini, barangkali adalah poin berikut: pada buku The Pragmatic Programmer, Thomas dan Hunt memaparkan dengan lengkap apa-apa yang menurut keduanya perlu bagi seorang yang ingin membangun *mastery* dan *craftmanship* di bidang pemrograman maupun *software engineering* secara umum. Dalam delapan bab, Thomas dan Hunt membahas mulai dari filosofi, pola pikir, pendekatan, hingga *tools* yang perlu dimiliki oleh seorang *pragmatic programmer*.

Pada akhirnya, kalau ada kawan-kawan yang berkecimpung di bidang pemrograman atau *software engineering* secara umum, saya sangat merekomendasikan untuk paling tidak pernah satu kali khatam membaca The Pragmatic Programmer. Sejauh ini gagasan-gagasan pada The Pragmatic Programmer telah menginspirasi saya untuk melakukan beberapa hal dalam upaya mengembangkan diri secara personal dan profesional, tentunya saya berharap kawan-kawan mendapatkan inspirasi yang sama.

