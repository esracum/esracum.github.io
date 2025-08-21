---
title: "TEKNOFEST VTOL İHA Projesinde OpenCV Haar Cascade Yöntemiyle Orman Yangını Tespiti"
date: 2024-05-19
# weight: 1
# aliases: ["/first"]
tags: ["GitHub Pages","HUGO"]
categories: ["Open-Source"]
author: "Esra Cüm"
cover:
    image: "https://private-user-images.githubusercontent.com/91957149/480462588-c1204dc7-50e1-463b-984d-36df922be288.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTU3OTY1NjQsIm5iZiI6MTc1NTc5NjI2NCwicGF0aCI6Ii85MTk1NzE0OS80ODA0NjI1ODgtYzEyMDRkYzctNTBlMS00NjNiLTk4NGQtMzZkZjkyMmJlMjg4LmpwZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MjElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODIxVDE3MTEwNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTliMWFiZjZkYzhhMmUzZjBkZmRhODljZDgzZDE3YzJmYjIxMGJhNTg2MzMyMmJlMDMxODZjNmI5Y2UxYjYwZmUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.zuLiN_gq3iBiwtNehgu-JHcEAflcrsfh9sTjclwgpuQ" # resmin yolu
    alt: "VTOL İHA Projesi"
    caption: "TEKNOFEST VTOL İHA Projesi"
    relative: true

showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "ÇELEBİ İHA Takımı olarak geliştirdiğimiz VTOL İHA projesiyle 2023’te TEKNOFEST Uluslararası İnsansız Hava Araçları Yarışması’nda fi nale kaldık ve performans ödülü kazandık."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
ShowCodeCopyButtons: true
---

## Giriş 
## Kullanılan Teknolojiler ve Araçlar 
Python, Raspberry Pi, Pixhawk Cube Orange, OpenCV (Haar Cascade), Dronekit, ArduPilot SITL, VTOL İHA, Otonom Uçuş Yazılımı, Mission Planner, Gazebo Simülasyon Ortamı

## Proje Detayları 
# Proje Konusu
 Ormanlık alanlarda çıkan yangınları erken tespit etmek ve hızlı müdahaleyi sağlamak amacıyla sabit kanatlı dikey iniş-kalkış yapabilen otonom bir İHA geliştirilmiştir. Proje kapsamında görüntü işleme teknikleri ile yangın tespit edilen kritik bölgelerde uçaktan bırakılan yangın topu ile otonom müdahale sağlanmıştır. Böylece yangınlara hızlı müdahale edilerek zararların en aza indirilmesi hedefl enmiştir.

# Projeden Elde Ettiğim Çıkarımlar
 Haar Cascade yöntemi, yangının farklı görünümleri ve çevresel koşullar (duman, düşük ışık, hareketli alevler) nedeniyle yüksek doğruluk ve tutarlılık sağlamada yetersiz kaldı. Ayrıca, ışık parlamaları ve yansımaların alev olarak algılanması nedeniyle yanlış pozitif tespitler oluştu. OpenCV kütüphanesi ile yapılan basit renk tespiti yöntemleri belirli durumlarda yeterli olsa da yangın alevi gibi daha karmaşık nesnelerin tespiti için CNN tabanlı derin öğrenme modelleri ile özel eğitimler gerçekleştirilmelidir. Ayrıca internet üzerinde bulunan genel veri setleri projenin özel ihtiyaçlarını karşılamakta yetersiz kaldığından projenin gereksinimlerine uygun özelleştirilmiş veri setleri kullanılması gerekmektedir.

 # Projede Üstlendiğim Roller
 Model eğitimlerinin gerçekleştirilmesi, Raspberry Pi kullanılarak görüntü işleme ve otonom görev uçuşu yazılımının geliştirilmesi ile yer istasyonu tasarımının yapılması



