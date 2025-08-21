---
title: "Derin Öğrenme ile Perinefrik Yağ Kalınlığından MAP Skoru Hesaplama"
date: 2024-11-30
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
## Proje Konusu 
 Böbrek tümörü ameliyatlarında, ameliyat zorluğunu belirleyen MAP (Mayo Adhesive Probability) skorunu hızlı ve doğru şekilde elde etmek amacıyla böbrek çevresindeki perinefrik yağ dokusunun kalınlığı ve stranding (yapışık yağ dokusu yoğunluğu) parametreleri otomatik olarak hesaplanmıştır.

## Proje Detayları 
# Böbrek Segmentasyonu
Böbrek segmentasyonu için *U-Net modeli* kullanılmıştır.
![Böbrek Segmentasyonu](https://private-user-images.githubusercontent.com/91957149/480462588-c1204dc7-50e1-463b-984d-36df922be288.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTU3NzM3MjMsIm5iZiI6MTc1NTc3MzQyMywicGF0aCI6Ii85MTk1NzE0OS80ODA0NjI1ODgtYzEyMDRkYzctNTBlMS00NjNiLTk4NGQtMzZkZjkyMmJlMjg4LmpwZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MjElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODIxVDEwNTAyM1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWRjNTYyOTgxZDVlNTFjNDhjNGI1NDI5NGZmOTg0YjVjYjY0NzM1N2EzZDJlZTc0ODAxYzUwZmVkNDZjN2YzNzYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.IaCjWfzIldSXlly8U7fMXJsKdNlG8KwhIt3MO6kLaw0)

Proje kapsamında, BT (Bilgisayarlı Tomografi ) görüntüleri üzerinde derin öğrenme ve görüntü işleme yöntemleri kullanılarak cerrahi planlama süreçlerini iyileştiren bir sistem geliştirilmiştir. Model eğitiminde kullanılan veri seti elle hazırlanmıştır. Stranding (yapışık yağ dokusu yoğunluğu) eşiğinin belirlenmesinde ise görüntü kontrastını artırmak için *CLAHE* yöntemi uygulanmış ve stranding hesabında otomatik eşikleme için *Otsu*, *Yen*, *Triangle* ve *Mean* gibi farklı yöntemler kıyaslanmıştır. Perinefrik yağ uzunluğunun tespitinde Z-skora dayalı fonksiyonlar kullanılarak bölgesel yoğunluk analizleri gerçekleştirilmiştir.

## Elde Edilen Sonuçlar
Yağ kalınlığı ölçümlerinde uzmanların elle yaptığı değerlendirmelerle *%89* oranında uyum sağlanırken stranding skorlamasında *%77* oranında örtüşme elde edilmiştir. 

> ⚠️ Ölçümdeki sapmalar, farklı BT cihazları, tarama protokolleri ve görüntü format dönüşümlerinden kaynaklanmaktadır. Gelecekte, DICOM formatında daha fazla veri kullanılması, görüntülerin JPG yerine DICOM formatında işlenmesi gelişmiş model mimarileri (U-Net++, Attention U-Net gibi) ile segmentasyon doğruluğunun arttırılması planlanmaktadır. Geliştirilen sistem, cerrahi planlama sürecinde hızlı ve doğru karar verilmesini sağlayarak ameliyat başarısını artırmaya önemli katkılar sunmaktadır. 




