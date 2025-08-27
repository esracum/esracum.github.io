---
title: "Derin Öğrenme ile Perinefrik Yağ Kalınlığından MAP Skoru Hesaplama"
date: 2024-11-30
cover:
    image: "/images/map_skoru.jpg" # Kapak resmi yolu
    alt: "VTOL İHA Projesi"         # Alternatif metin
    caption: "TEKNOFEST VTOL İHA Projesi" # Altta yazacak
    relative: true
# weight: 1
# aliases: ["/first"]
tags: ["GitHub Pages","HUGO"]
categories: ["Open-Source"]
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
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
ShowCodeCopyButtons: true
---

## Giriş 
## Proje Konusu 
 Böbrek tümörü ameliyatlarında, ameliyat zorluğunu belirleyen MAP (Mayo Adhesive Probability) skorunu hızlı ve doğru şekilde elde etmek amacıyla böbrek çevresindeki perinefrik yağ dokusunun kalınlığı ve stranding (yapışık yağ dokusu yoğunluğu) parametreleri otomatik olarak hesaplanmıştır.

## Proje Detayları 
# Böbrek Segmentasyonu
Böbrek segmentasyonu için *U-Net modeli* kullanılmıştır.
> ![Böbrek Segmentasyonu](/images/map_skoru.jpg)


Proje kapsamında, BT (Bilgisayarlı Tomografi ) görüntüleri üzerinde derin öğrenme ve görüntü işleme yöntemleri kullanılarak cerrahi planlama süreçlerini iyileştiren bir sistem geliştirilmiştir. Model eğitiminde kullanılan veri seti elle hazırlanmıştır. Stranding (yapışık yağ dokusu yoğunluğu) eşiğinin belirlenmesinde ise görüntü kontrastını artırmak için *CLAHE* yöntemi uygulanmış ve stranding hesabında otomatik eşikleme için *Otsu*, *Yen*, *Triangle* ve *Mean* gibi farklı yöntemler kıyaslanmıştır. Perinefrik yağ uzunluğunun tespitinde Z-skora dayalı fonksiyonlar kullanılarak bölgesel yoğunluk analizleri gerçekleştirilmiştir.

## Elde Edilen Sonuçlar
Yağ kalınlığı ölçümlerinde uzmanların elle yaptığı değerlendirmelerle *%89* oranında uyum sağlanırken stranding skorlamasında *%77* oranında örtüşme elde edilmiştir. 

> ⚠️ Ölçümdeki sapmalar, farklı BT cihazları, tarama protokolleri ve görüntü format dönüşümlerinden kaynaklanmaktadır. Gelecekte, DICOM formatında daha fazla veri kullanılması, görüntülerin JPG yerine DICOM formatında işlenmesi gelişmiş model mimarileri (U-Net++, Attention U-Net gibi) ile segmentasyon doğruluğunun arttırılması planlanmaktadır. Geliştirilen sistem, cerrahi planlama sürecinde hızlı ve doğru karar verilmesini sağlayarak ameliyat başarısını artırmaya önemli katkılar sunmaktadır. 




