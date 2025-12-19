---
title: "Derin Öğrenme ile Perinefrik Yağ Kalınlığından MAP Skoru Hesaplama"
date: 2025-06-20
cover:
    image: "/images/map_kapak.jpg" # Kapak resmi yolu
    alt: "Map Skor"         # Alternatif metin
    caption: "Map Skoru Hesaplama" # Altta yazacak
    relative: true
# weight: 1
# aliases: ["/first"]
tags: ["Derin Öğrenme","Görüntü İşleme"]
categories: ["Derin Öğrenme"]
author: "Esra Cüm"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Bu proje, lisans bitirme projesi kapsamında Ondokuz Mayıs Üniversitesi Dr. Öğr. Üyesi Oğuz Emre Kural ve üroloji alanında rehberlik eden Dr. Emre Fatih Karadeli ile birlikte geliştirilmiştir. "
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: false
ShowRssButtonInSectionTermList: true

---

## Giriş 
Bu projede U-Net tabanlı böbrek segmentasyonu ve görüntü işleme yöntemleriyle perinefrik yağ kalınlığı ve stranding otomatik ölçülmüş, MAP skoru hesaplanmıştır. Geliştirilen sistem; cerrahi planlamada hızlı, doğru ve güvenilir bir klinik karar desteği sunmaktadır.

## Proje Konusu 
Böbrek tümörü ameliyatlarında, ameliyat zorluğunu belirleyen MAP (Mayo Adhesive Probability) skorunun hızlı ve doğru şekilde elde edilmesi amaçlanmıştır. Bu kapsamda, böbrek çevresindeki perinefrik yağ kalınlığı ve stranding (yapışık yağ dokusu yoğunluğu) parametreleri görüntü işleme ve derin öğrenme yöntemleriyle otomatik olarak hesaplanmıştır.

## Proje Detayları 
### Böbrek Segmentasyonu
Böbrek segmentasyonu için *U-Net modeli* kullanılmıştır.
![Böbrek Segmentasyonu](/images/map_skoru.jpg)


Proje kapsamında, BT (Bilgisayarlı Tomografi) görüntüleri üzerinde derin öğrenme ve görüntü işleme yöntemleri kullanılarak cerrahi planlama süreçlerini iyileştiren bir sistem geliştirilmiştir. Modelin eğitiminde kullanılan veri seti ise Radiant DICOM uygulaması üzerinden elle hazırlanmış olup toplam 473 görüntüden oluşmaktadır.

Stranding (yapışık yağ dokusu yoğunluğu) eşiğinin belirlenmesinde ise görüntü kontrastını artırmak için *CLAHE* yöntemi uygulanmış ve stranding hesabında otomatik eşikleme için *Otsu*, *Yen*, *Triangle* ve *Mean* gibi farklı yöntemler kıyaslanmıştır.

![Stranding Hesaplama](/images/stranding.jpg)

Perinefrik yağ kalınlığının ölçümünde Z-skoruna dayalı fonksiyonlar kullanılarak bölgesel yoğunluk analizleri yapılmıştır.

## Elde Edilen Sonuçlar
Yağ kalınlığı ölçümlerinde uzmanların elle yaptığı değerlendirmelerle *%89* oranında uyum sağlanırken stranding skorlamasında *%77* oranında örtüşme elde edilmiştir. 
![Model Sonuçları](/images/model_sonuc.jpg)

> ⚠️ Ölçümdeki sapmalar, farklı BT cihazları, tarama protokolleri ve görüntü format dönüşümlerinden kaynaklanmaktadır. Gelecekte, DICOM formatında daha fazla veri kullanılması, görüntülerin JPG yerine DICOM formatında işlenmesi gelişmiş model mimarileri (U-Net++, Attention U-Net gibi) ile segmentasyon doğruluğunun arttırılması planlanmaktadır. Geliştirilen sistem, cerrahi planlama sürecinde hızlı ve doğru karar verilmesini sağlayarak ameliyat başarısını artırmaya önemli katkılar sunmaktadır. 
>
Bu sonuçlar, geliştirilen yöntemin klinik kullanıma yönelik umut verici bir potansiyele sahip olduğunu göstermektedir.




