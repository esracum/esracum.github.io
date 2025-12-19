---
title: "NLP Tabanlı Akıllı Kitap Öneri Sistemi"
date: 2025-12-19

# weight: 1
# aliases: ["/first"]

cover:
    image: "image: "/images/ai_book.jpg"" # Kapak görseli varsa yolu buraya yazın
    alt: "Book Recommendation System"
    caption: "NLP Powered Recommendation Engine"
    relative: true

tags: ["Python", "NLP", "Machine Learning", "Gradio", "Vector DB", "LLM", "Google Gemini API"]
categories: ["Veri Bilimi", "Doğal Dil İşleme", "Yapay Zeka"]
author: "Esra Cüm"

showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Kullanıcı sorgularını hem anlamsal hem de duygusal bağlamda analiz ederek (Semantic & Sentiment Analysis) en uygun kitapları öneren uçtan uca NLP projesi."
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

Sistemin arayüzünü, duygusal analiz yeteneklerini ve kitap öneri performansını aşağıdaki videodan izleyebilirsiniz:

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe src="https://www.youtube.com/embed/x3Nod9s0los" 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
    allowfullscreen 
    title="YouTube Video">
  </iframe>
</div>

---

## Proje Hakkında

Bu proje, **Doğal Dil İşleme (NLP)** tekniklerini kullanarak uçtan uca geliştirilmiş akıllı bir Kitap Öneri Sistemidir. 

Standart anahtar kelime aramalarının ötesine geçerek, kullanıcıların sorgularını hem **anlamsal (semantic)** hem de **duygusal (sentiment)** bağlamda analiz eder. Örneğin, kullanıcı *"Bana hüzünlü ama umut veren bir hikaye bul"* dediğinde, sistem sadece kelimelere değil, cümlenin taşıdığı duyguya da odaklanarak en uygun eşleşmeyi sağlar.

## Proje Aşamaları ve Teknik Detaylar

Proje, veri hazırlığından son kullanıcı arayüzüne kadar 5 ana teknik aşamadan oluşmaktadır:

### 1. Veri Hazırlığı ve Temizleme (ETL)
* **Veri Seti:** Kaggle üzerinden alınan "7k-books-with-metadata" seti kullanıldı.
* **İşlem:** Eksik veriler temizlendi, gereksiz sütunlar çıkarıldı ve korelasyon analizleri (heatmap) yapıldı. Kitap açıklamaları NLP modellerinin daha iyi işleyebilmesi için optimize edildi.

### 2. Zero-Shot Metin Sınıflandırma
* **Amaç:** Kitapların karmaşık ve dağınık kategorilerini; "Çocuk Kurgu", "Yetişkin Kurgu", "Kurgu Dışı" gibi daha basit ve anlaşılır üst kümelere indirgemek.
* **Model:** `facebook/bart-large-mnli` (Zero-Shot Classification tekniği ile).

### 3. Duygu Analizi (Sentiment Analysis)
* **Amaç:** Kullanıcıların ruh haline göre (örn: "neşeli bir kitap") arama yapabilmesini sağlamak. Kitap açıklamaları 6 temel duyguya göre etiketlendi: *Anger, Fear, Joy, Sadness, Surprise, Neutral*.
* **Model:** Hugging Face üzerinden `j-hartmann/emotion-english-distilroberta-base`.

### 4. Vektör Arama (Vector Search & RAG)
* **Amaç:** Metinlerin anlamsal olarak aranabilmesi için vektör veritabanı mimarisi kuruldu.
* **Embedding:** Google Generative AI Embeddings (`models/text-embedding-004`).
* **Veritabanı:** LangChain entegrasyonu ile **ChromaDB** kullanılarak veriler depolandı ve sorgulandı.

### 5. Kullanıcı Arayüzü (UI)
* **Araç:** Tüm arka plan süreçleri (modeller, veritabanı sorguları), **Gradio** ile geliştirilen modern ve interaktif bir web arayüzünde birleştirildi.

##  Kurulum ve Kullanım

Projeyi yerel makinenizde çalıştırmak için aşağıdaki adımları izleyebilirsiniz.

### 1. Repoyu Klonlayın

```bash
git clone [https://github.com/esracum/repo-adi.git](https://github.com/esracum/repo-adi.git)
cd repo-adi
```

### 2. Gerekli Kütüphaneleri Yükleyin
```bash
pip install -r requirements.txt
```

### 3. API Anahtarını Ayarlayın
```bash
GOOGLE_API_KEY=google_api_anahtariniz
```

### 4. Uygulamayı Başlatın
```bash
python dashboard.py
```