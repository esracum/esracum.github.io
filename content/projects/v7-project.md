---
title: "Agentic AI Coding Agent"
date: 2025-11-30

# weight: 1
# aliases: ["/first"]

cover:
    image: "/images/agentic_ai.jpg" # Kapak görseli varsa yolu buraya yazın (örn: /images/agent.jpg)
    alt: "Agentic AI"
    caption: "Autonomous Coding Agent"
    relative: true

tags: ["Python", "GenAI", "LLM", "Agentic AI", "Google Gemini API"]
categories: ["Yapay Zeka", "Otonom Ajanlar"]
author: "Esra Cüm"

showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Herhangi bir hazır framework kullanılmadan, tamamen Python ve Gemini Flash API ile sıfırdan geliştirilmiş; kod yazan, çalıştıran ve kendi hatasını düzelten otonom ajan."
canonicalURL: "[https://canonical.url/to/page](https://canonical.url/to/page)"
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

Ajanın kod yazma, hata alma ve kendi hatasını düzeltme sürecini aşağıdaki videodan izleyebilirsiniz:

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe src="https://www.youtube.com/embed/sLF7sKF_63M" 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
    allowfullscreen 
    title="YouTube Video">
  </iframe>
</div>

---

## Proje Hakkında

Bu proje, standart LLM’lerin "sadece metin/yanıt üretme" sınırını aşıp doğrudan eyleme geçen **Agentic AI** (Ajan Tabanlı Yapay Zeka) konseptinin bir uygulamasıdır. 

**LangChain veya CrewAI gibi hazır frameworkler kullanılmadan**, tamamen saf **Python** ve **Google Gemini Flash API** kullanılarak sıfırdan inşa edilmiştir.

Statik bir modelden, otonom problem çözen bir ajana geçiş deneyimi sunan bu sistem; **Function Calling** ve **Iteration** mimarisini kullanarak klasik "sor-cevapla" yapısını tamamen değiştirmektedir.

## Temel Özellikler

Bu ajan sadece kod üretmez; ürettiği kodu yerel ortamda çalıştırır, hataları analiz eder ve kendi kendini düzelterek (Self-Correction) görevi tamamlar.

* ✅ **Execution (Çalıştırma):** Kodu sadece yazmakla kalmaz, izole ortamda (subprocess) bilfiil çalıştırır ve çıktıyı analiz eder.
* ✅ **Self-Correction (Otonom Hata Düzeltme):** Hata aldığında durmaz. `stderr` çıktısını okur, hatanın nedenini anlar ve kendi yazdığı kodu onarana kadar döngüyü sürdürür.
* ✅ **Local File Integration (Yerel Entegrasyon):** Yerel dizindeki dosyaları okuyup proje bağlamını anlayarak dosyalar üzerinde doğrudan değişiklik ve düzenleme yapar.
* ✅ **From Scratch Mimari:** Framework bağımlılığı olmadan, saf Python mantığı ile `Prompt Engineering` ve `Function Calling` yapıları manuel olarak kurgulanmıştır.

## Nasıl Çalışır? (The Loop)

Ajan, kendisine verilen bir görevi yerine getirmek için aşağıdaki "Otonom Döngü"yü izler:

1.  **Analiz:** Kullanıcı isteğini ve proje bağlamını (dosyalar) anlar.
2.  **Planlama & Kodlama:** Gemini Flash API üzerinden gerekli Python kodunu oluşturur.
3.  **Çalıştırma (Execution):** Oluşturulan kodu sistemde güvenli bir şekilde çalıştırır.
4.  **Doğrulama (Verification):**
    * **Başarılı:** Sonucu kullanıcıya sunar.
    * **Hata:** Hata mesajını analiz eder, çözüm üretir ve **2. adıma** geri döner.

## Kurulum ve Kullanım

Projeyi yerel makinenizde çalıştırmak için aşağıdaki adımları izleyebilirsiniz.

### 1. Repoyu Klonlayın

```bash
git clone https://github.com/esracum/repo-adi.git
cd repo-adi 

```

### 2. Gerekli Paketleri Yükleyin
Sanal ortam (venv veya uv) kullanmanız önerilir.
```bash
pip install -r requirements.txt

```


### 3. Gerekli Paketleri Yükleyin
Proje ana dizininde .env dosyası oluşturun ve Google Gemini API anahtarınızı ekleyin:
```bash
GEMINI_API_KEY=api_anahtariniz

```

### 4. Çalıştırma
Ajanı başlatmak için main.py dosyasını çalıştırın:
```bash
# Standart Python ile:
python main.py

# Veya uv kullanıyorsanız:
uv run main.py

```

