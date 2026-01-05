---
title: "C++ ve OpenCV ile Gerçek Zamanlı Nesne Algılama"
date: 2026-01-05
description: "Yüksek performanslı C++ ve OpenCV kullanarak geliştirilen gerçek zamanlı nesne algılama sistemi."
tags: ["C++", "OpenCV", "Object Detection", "Computer Vision"]
categories: ["Projects", "Computer Vision"]
cover:
    image: "images/object_detect.jpg" 
    
---

## Proje Hakkında

Bu proje, görüntü işleme süreçlerinde performansın kritik olduğu durumlar için **C++** ve **OpenCV** kütüphanesi kullanılarak geliştirilmiştir. Python tabanlı çözümlere göre daha düşük gecikme süresi (latency) ve daha yüksek FPS değerleri sunarak gerçek zamanlı analiz yapabilmektedir.

Özellikle İHA sistemleri gibi kısıtlı donanım kaynaklarına sahip platformlarda nesne algılama süreçlerini optimize etmek amacıyla tasarlanmıştır.


## Proje Demosu

Aşağıdaki videoda sistemin gerçek zamanlı çalışma performansını ve algılama hassasiyetini izleyebilirsiniz:

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe src="https://www.youtube.com/embed/gc_lxAZrdpk?start=19" 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
    allowfullscreen 
    title="Object Detect GCS Demo">
  </iframe>
</div>
---



## Teknik Detaylar ve Teknolojiler

* **Dil:** C++
* **Kütüphane:** OpenCV (Open Computer Vision Library)
* **Derleme Sistemi:** CMake
* **Algoritma:** [Buraya kullandığın algoritmayı ekle: örn. YOLOv8, Haar Cascade veya MobileNet-SSD]

## Öne Çıkan Özellikler

* **Gerçek Zamanlı Performans:** C++ sayesinde optimize edilmiş kare işleme hızı.
* **Çoklu Nesne Algılama:** Aynı anda birden fazla sınıfı (insan, araç vb.) tanıma yeteneği.
* **Görüntü İşleme Hattı (Pipeline):** Ham görüntünün alınması, ön işlemesi (preprocessing) ve sonuçların görselleştirilmesi.

---

## Kaynak Kodları

Projenin tüm kaynak kodlarına ve teknik dökümantasyonuna GitHub üzerinden ulaşabilirsiniz:

👉 [GitHub: object-detect-cpp](https://github.com/esracum/object-detect-cpp)

---