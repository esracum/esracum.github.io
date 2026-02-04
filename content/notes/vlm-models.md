
---
title: "Görsel ve Dilsel Temsillerin Vektör Uzayında Hizalanması: CLIP' Giriş"
date: 2026-02-03
cover:
    image: "" # Kapak resmi yolu
    alt: "CLIP"         # Alternatif metin
    caption: "Görsel ve metinsel verilerin ortak bir vektör uzayında hizalanmasını sağlayan CLIP" # Altta yazacak
    relative: true


tags: ["AI", "Computer Vision", "Deep Learning", "CLIP", "NLP"] 
categories: ["Artificial Intelligence"]
author: "Esra Cüm"

showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "OpenAI tarafından geliştirilen CLIP mimarisinin teknik analizi, zıtlıklı öğrenme (contrastive learning) prensipleri ve görsel-metinsel temsillerin vektör uzayı hizalaması."
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

# CLIP (Contrastive Language-Image Pre-training): Çok Modlu Temsil Öğrenimi
## CLIP Nedir ve Neden Önemlidir?
CLIP, görüntüleri metinle ilişkilendirerek nesne tanıma ve sınıflandırma yapar.  CLIP, görsel ve dil (metin) verilerini birleştiren çok modlu (multimodal) bir yapay zeka modelidir. İnternet ölçeğinde, resim ve resim altı yazılarından (caption) oluşan 400 milyonluk devasa bir veri seti üzerinde eğitilmiştir. Gerçek hayatta güvenlik (örn. maske tespiti), karmaşık sahne analizi (örn. sisli dağdaki balon) ve genel görsel sınıflandırma gibi alanlarda kullanılır.  CLIP doğrudan görsel arama (retrieval) sistemlerinde kullanılır. Kullanıcının yazdığı metni anlayıp veritabanındaki en alakalı görseli bulabilir; model kartında bu yetenek açıkça "retrieval and embedding tasks" olarak belirtilmiştir.

CLIP'in en önemli özelliği ve önemi, "Zero-Shot" (sıfır atış) yetenekleridir; yani model, belirli bir görev için özel eğitim verisine ihtiyaç duymadan birçok sınıflandırma işlemini yapabilir. Bu sayede geniş bir görsel anlayış sunar.

## 1. Model Kimlik Bilgileri ve Erişim
Geliştirici: OpenAI (Ocak 2021).

Lisans Modeli: Kaynak kod MIT Lisansı ile sunulurken, model ağırlıkları (weights) OpenAI’ın özel kullanım şartlarına tabidir. Ticari dağıtım kısıtlıdır.

Parametre Yapısı: CLIP, farklı "backbone" (omurga) seçeneklerine sahip bir model ailesidir. Endüstride sıkça referans verilen ViT-B/32 versiyonu yaklaşık 151 Milyon parametreden oluşur.

Eğitim Altyapısı: * En büyük ResNet tabanlı varyant: 256 V100 GPU ile ~18 gün.
En büyük ViT tabanlı varyant: 592 V100 GPU ile ~12 gün.


## 2. Eğitim Verisi: Web ImageText (WIT)

CLIP, internet üzerinden derlenmiş 400 milyon görüntü-metin (image-caption) çiftinden oluşan WIT veri seti ile eğitilmiştir. Bu veri setinin en kritik özelliği "denetimsiz" (uncurated) olmasıdır; yani modeller ImageNet gibi insan eliyle etiketlenmiş dar setler yerine, internetteki doğal dil açıklamalarından öğrenir. Veri seti halka açık değildir.

## 3. CLIP Eşleştirilmiş Görüntü-Metin Verisinden Nasıl Öğrenir? 

### Contrastive Learning (Karşıtlık Öğrenimi)
CLIP, görüntüleri ve metinleri aynı boyuttaki (vektörel) bir Ortak Gömme Uzayı (Shared Embedding Space) içerisine izdüşürür.Vektör Kodlama: Görüntüler bir Vision Encoder, metinler ise bir Text Encoder (Transformer) aracılığıyla genellikle 512 boyutlu vektörlere dönüştürülür.Symmetric Cross Entropy Loss: Eğitim sırasında $N$ adet görüntü ve metinden oluşan bir mini-batch için $N \times N$ benzerlik matrisi hesaplanır.Optimizasyon: Model, doğru eşleşen çiftlerin (matrisin köşegeni) kosinüs benzerliğini maksimize ederken, yanlış eşleşenlerin ($N^2 - N$ adet hücre) benzerliğini minimize eder.CLIP, "Contrastive Learning" (Karşıtlık Öğrenimi) yöntemini kullanır.


• Vektör Kodlama: Görüntü ve metin, ayrı kodlayıcılar (encoders) tarafından aynı boyutta vektörlere dönüştürülür. Bu vektörler (embedding), verilerin anlamsal içeriğini temsil eder.

• Ortak Uzay: Görüntü ve metin vektörleri ortak bir gömme uzayında (shared embedding space) karşılaştırılır.

• Benzerlik Maksimizasyonu: Eğitim sürecinin amacı, doğru görüntü ve metin çifti arasındaki benzerliği (cosine similarity) maksimize etmek, eşleşmeyen diğer çiftler arasındaki benzerliği ise minimize etmektir.

• Hız: Bu karşıtlık kaybı (contrastive loss) yöntemi, görsel özellikleri öğrenmek için kelime kelime tahmin yapmaya çalışan üretken (generative) yaklaşımlara göre çok daha hızlıdır.



## 4. Mimari Bileşenler

Vision Encoder: ResNet-50 veya Vision Transformer (ViT) mimarisi kullanılır. Görsel özellikleri hiyerarşik veya global olarak çıkarır.

Text Encoder: 12 katmanlı, 512-genişlikli ve 8-dikkat kafalı (attention heads) GPT-2 benzeri bir Transformer yapısıdır.

## 5. Zero-Shot Sınıflandırma ve Prompt Engineering
Modelin en güçlü yanlarından biri, daha önce görmediği sınıfları herhangi bir "fine-tuning" (ince ayar) gerektirmeden tanıyabilmesidir.

Mekanizma: Sınıf etiketleri (örn: "uçak", "araba") "A photo of a {label}" gibi şablonlara yerleştirilerek Text Encoder'a verilir.

Tahmin: Görüntü vektörü ile tüm aday metin vektörleri kıyaslanır. En yüksek benzerlik skorunu veren metin şablonu, modelin tahmini olarak kabul edilir.

## 6. Modern Yapay Zeka Ekosistemindeki Yeri

CLIP, günümüzdeki Generative AI (Üretken YZ) modellerinin temel anlamlandırma motorudur.

Stable Diffusion & DALL-E: Bu modeller, kullanıcının girdiği metnin görsel karşılığını "anlamak" için CLIP'in metin kodlayıcısını veya ortak uzaydaki temsillerini rehber (guidance) olarak kullanır.

Vektör Veritabanları: Görsel arama (image retrieval) sistemlerinde metin-görüntü eşleşmesini sağlamak için standart bir araçtır.

# 7. Teknik Sınırlamalar

Soyut Kavramlar: Nesneleri sayma (counting) veya "hangisi daha yakın" gibi uzamsal ilişkileri anlama konusunda zayıftır.

Spesifiklik: Çok ince detay farkı olan alt türleri (örn: özel bir kuş türü) ayırt etmekte zorlanabilir.

Hassasiyet: Yazılan "prompt" içindeki küçük bir kelime değişikliği, tahmin sonucunu önemli ölçüde değiştirebilir.

Etik ve Yanlılık: İnternet verisindeki toplumsal önyargılar modelin çıktılarına yansıyabilir.






