---
title: "Fix Focus - Görüntü işleme ile öğrenci dikkat seviyesini analiz eden bir masaüstü uygulaması"
date: 2025-03-19

# weight: 1
# aliases: ["/first"]
tags: ["Python","Görüntü İşleme"]
categories: ["Derin Öğrenme"]
author: "Esra Cüm"

showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Yapay Zeka ve Teknoloji Akademisi Hackathon kapsamında geliştirilmiş bir projedir."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true

---

## Giriş 
### Proje Tanımı

Bu proje, gerçek zamanlı kullanıcı dikkat analizi yapan bir dikkat takip sistemidir. Kullanıcıların dikkat durumunu tespit ederek uyarılar ve veriler sunar.

### Kullanılan Teknolojiler

**PyQt5:** Grafik arayüz geliştirme

**MediaPipe Face Mesh:** Yüz hatları algılama ve kafa pozisyonu analizi

### Çalışma Prensibi

Kamera görüntüsü canlı olarak izlenir ve yüz hatları analiz edilir. Kullanıcının dikkatli mi yoksa dikkatsiz mi olduğu belirlenir. Uzun süre dikkatsiz kalındığında sistem sesli ve görsel uyarı verir.

### Özellikler

Dikkat skoru ve uyarı sayısı: Anlık olarak gösterilir

Veri kaydı: Tüm veriler CSV formatında saklanır

Grafiksel analiz: Zamanla dikkat seviyesini gösterir

Kullanıcı kontrolü: Başlat/durdur butonları, tema seçimi ve oturum özet raporu

### Kullanım Alanları

Sistem, eğitim, uzaktan çalışma veya dikkat takibi gerektiren her ortamda pratik bir çözüm olarak kullanılabilir.