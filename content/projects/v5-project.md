---
title: "Fix Focus - Görüntü İşleme İle Dikkat Analizi"
date: 2025-03-19

cover:
    image: "/images/fix_focus.jpg" 
    alt: "Fix Focus Masaüstü Uygulaması"
    caption: "Görüntü İşleme ile Gerçek Zamanlı Dikkat Seviyesi Analizi"
    relative: true

tags: ["Python", "Görüntü İşleme", "OpenCV", "MediaPipe", "PyQt5"]
categories: ["Derin Öğrenme", "Yapay Zeka", "Masaüstü Uygulama"]
author: "Esra Cüm"

showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Yapay Zeka ve Teknoloji Akademisi Hackathon kapsamında geliştirilmiş, görüntü işleme teknikleriyle öğrenci dikkat seviyesini analiz eden masaüstü uygulaması."
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

Uygulamanın gerçek zamanlı çalışma performansını ve arayüz özelliklerini aşağıdaki videodan inceleyebilirsiniz:

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe src="https://www.youtube.com/embed/yd6RaqdLYCA" 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
    allowfullscreen 
    title="Fix Focus Demo">
  </iframe>
</div>

---

## Proje Tanımı

**Fix Focus**, modern eğitim ve çalışma hayatındaki en büyük sorunlardan biri olan "odak kaybı" problemini teknoloji ile çözmek için tasarlanmıştır. 

Yapay Zeka ve Teknoloji Akademisi Hackathon sürecinde geliştirilen bu masaüstü uygulaması, bilgisayar kamerasını kullanarak kullanıcının göz ve baş hareketlerini analiz eder. Gerçek zamanlı veri işleme teknikleri sayesinde, kullanıcının derse veya işe odaklanıp odaklanmadığını tespit ederek anlık geri bildirimler sunar.

##  Kullanılan Teknolojiler

Projenin altyapısında yüksek performanslı görüntü işleme ve arayüz kütüphaneleri kullanılmıştır:

* **Python:** Projenin ana geliştirme dili.
* **MediaPipe Face Mesh:** Google'ın geliştirdiği bu teknoloji ile yüz üzerindeki 468 landmark (nokta) tespit edilerek göz açıklığı ve kafa pozisyonu milisaniyeler içinde hesaplanır.
* **PyQt5:** Kullanıcı dostu, modern ve responsive bir masaüstü arayüzü (GUI) oluşturmak için kullanıldı.
* **Matplotlib & Pandas:** Anlık dikkat verilerinin görselleştirilmesi ve raporlanması süreçlerinde kullanıldı.

## Çalışma Prensibi

Sistem, webcam üzerinden alınan görüntüleri şu adımlarla işler:

1.  **Yüz Tespiti:** Görüntüdeki yüz algılanır ve landmark noktaları çıkarılır.
2.  **EAR (Eye Aspect Ratio) Analizi:** Gözlerin kapalılık oranı hesaplanarak kullanıcının uykulu olup olmadığı veya ekrana bakıp bakmadığı anlaşılır.
3.  **Pose Estimation (Poz Analizi):** Kafanın sağa, sola veya aşağı yönelimi analiz edilerek dikkat dağınıklığı tespit edilir.
4.  **Karar Mekanizması:** Belirlenen eşik değerler (threshold) aşıldığında sistem kullanıcıyı "Dikkatsiz" olarak etiketler.

##  Temel Özellikler

* **Gerçek Zamanlı Analiz:** Dikkat skoru ve uyarı sayısı anlık olarak ekranda güncellenir.
* **Akıllı Uyarı Sistemi:** Kullanıcı belirli bir süreden fazla dikkatsiz kaldığında sesli ve görsel uyarılar vererek odağı tekrar sağlar.
* **Grafiksel Takip:** Dikkat seviyesindeki değişimler dinamik grafiklerle zaman ekseninde gösterilir.
* **Veri Raporlama:** Oturum sonlandığında tüm dikkat verileri, analiz için `.csv` formatında otomatik olarak kaydedilir.
* **Kullanıcı Kontrolü:** Başlat/Durdur butonları, Dark/Light tema seçenekleri ve kamera seçimi gibi özelleştirmeler sunar.

## Kullanım Alanları

Fix Focus, dikkatin kritik olduğu birçok alanda pratik bir çözüm sunar:
* **Uzaktan Eğitim:** Öğrencilerin ders takibi ve verimliliğini artırmak.
* **Kurumsal Çalışma:** Odaklanma sorunu yaşayan çalışanlar için Pomodoro benzeri akıllı asistan desteği.
* **Kişisel Gelişim:** Bireylerin kendi odak sürelerini ölçmesi ve geliştirmesi.