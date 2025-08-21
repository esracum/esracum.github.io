---
title: "TEKNOFEST VTOL İHA Projesinde OpenCV Haar Cascade Yöntemiyle Orman Yangını Tespiti"
date: 2024-05-19
# weight: 1
# aliases: ["/first"]
tags: ["GitHub Pages","HUGO"]
categories: ["Open-Source"]
author: "Esra Cüm"
cover:
    image: "\\images\\vtol-proje.jpg" # resmin yolu
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



