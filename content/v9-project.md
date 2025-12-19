---
title: "Hezarfen İHA - Yer Kontrol İstasyonu (GCS)"
date: 2025-07-19

cover:
    image: "/images/gcs.jpg" 
    alt: "Hezarfen Yer Kontrol İstasyonu Arayüzü"
    caption: "Python ve PyQt5 ile Geliştirilmiş GCS Arayüzü"
    relative: true

tags: ["Python", "PyQt5", "OpenCV", "İHA", "Drone", "Telemetri", "UDP/Serial", "Haberleşme"]
categories: ["Masaüstü Uygulama", "Havacılık ve Savunma", "Yapay Zeka"]
author: "Esra Cüm"

showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Hezarfen Takımı İHA'ları için Python ve PyQt5 ile geliştirilmiş; canlı telemetri takibi, video aktarımı ve görev planlama özelliklerine sahip profesyonel Yer Kontrol İstasyonu (GCS)."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true
disableShare: false
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: false
ShowRssButtonInSectionTermList: true

---

## Proje Demosu

Yer Kontrol İstasyonunun canlı uçuş sırasındaki performansını, arayüzünü ve telemetri akışını aşağıdaki videodan inceleyebilirsiniz:

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe src="https://www.youtube.com/embed/Lvr-rLc-65Q" 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
    allowfullscreen 
    title="Hezarfen GCS Demo">
  </iframe>
</div>

---

## ⚡ Proje Hakkında

**Hezarfen Takımı** için geliştirdiğimiz bu proje, İnsansız Hava Araçlarının (İHA) yerden güvenli ve etkili bir şekilde yönetilmesini sağlayan kapsamlı bir **Yer Kontrol İstasyonu (Ground Control Station - GCS)** yazılımıdır.

Tamamen **Python** ve **PyQt5** kullanılarak geliştirilen bu masaüstü uygulaması; pilot ve yer ekibine aracın durumu hakkında anlık bilgi sağlar, canlı görüntü aktarımı yapar ve karmaşık görev planlamalarının sahada uygulanmasına olanak tanır.

## Kullanılan Teknolojiler

Projenin altyapısında aşağıdaki teknolojiler kullanılmıştır:

* **Arayüz (GUI):** Python & PyQt5
* **Görüntü İşleme/Aktarım:** OpenCV
* **Haberleşme:** UDP ve Seri İletişim (Serial Communication) protocols
* **Harita Entegrasyonu:** Harita tabanlı GPS takibi kütüphaneleri

---

## Kişisel Katkılarım ve Sorumluluklarım

Bu projenin geliştirilme sürecinde, özellikle kullanıcı arayüzünün inşası, veri görselleştirme ve haberleşme altyapısının entegrasyonu konularında aktif rol aldım.

### 1. Arayüz Geliştirme (UI/UX)
* **PyQt5** kullanılarak, pilotun ihtiyaç duyduğu tüm verilere hızlıca ulaşabileceği, modern, duyarlı ve kullanıcı dostu bir masaüstü arayüzü tasarlandı ve kodlandı.

### 2. Gerçek Zamanlı Telemetri Görselleştirme
* İHA'dan gelen anlık telemetri verileri (Hız, İrtifa, Yön/Pusula, Konum, Batarya Durumu vb.) işlenerek arayüz üzerindeki göstergelerde (gauge) ve grafiklerde **canlı olarak** görselleştirildi.

### 3. Canlı Kamera Akışı ve OpenCV Entegrasyonu
* İHA üzerindeki kameradan gelen görüntü sinyali, **OpenCV** kütüphanesi kullanılarak işlendi ve GCS arayüzüne gecikmesiz (low-latency) olarak entegre edildi.

### 4. Haberleşme Altyapısı (Backend)
* Yer istasyonu ile hava aracı arasındaki kritik veri akışını sağlamak için hem **Seri (Serial)** hem de **UDP** tabanlı sağlam bir iletişim altyapısı kuruldu.

### 5. Harita, GPS ve Görev Planlama
* **Harita Entegrasyonu:** İHA'nın anlık konumu harita üzerinde canlı olarak takip edilebilir hale getirildi.
* **Rota Planlama:** Kullanıcının harita üzerinde noktalar (waypoints) belirleyerek görev rotası oluşturmasını ve bu rotayı araca yüklemesini sağlayan modül geliştirildi.

### 6. Veri Kaydı (Data Logging)
* Uçuş sonrası analizler için kritik önem taşıyan tüm telemetri ve görev verilerinin anlık olarak yerel diske kaydedilmesi (logging) sağlandı.