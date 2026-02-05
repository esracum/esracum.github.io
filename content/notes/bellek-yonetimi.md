---
title: "Bellek Yönetimi ve Donanım Etkileşimi"
date: 2026-02-03
tags: ["C++", "Embedded", "Memory"]
categories: ["Gömülü Sistemler"]
author: "Esra Cüm"
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Stack, Heap ve Register erişimi ve bellek yönetimi üzerine teknik notlar."
---
# Bellek Yönetimi ve Stratejileri: Stack, Heap ve Fragmantasyon



Bellek yönetimi, bir yazılımın hem performansını hem de kararlılığını belirleyen en temel unsurdur. Bu yazıda, belleğin fiziksel düzeninden başlayarak modern yönetim stratejilerine göz atacağız.



---



## 1. Stack (Yığın) vs. Heap (Öbek)



İşletim sistemi ve derleyici, verileri kullanım amaçlarına göre iki farklı bölgeye ayırır:



| Özellik | **Stack (Yığın)** | **Heap (Öbek)** |



| **Yönetim** | Otomatik (Derleyici/OS) | Manuel (Yazılımcı/GC) |

| **Büyüme Yönü** | Yüksek adresten düşüğe (LIFO) | Düşük adresten yükseğe |

| **Hız** | Çok Hızlı (Pointer kaydırma) | Yavaş (Boş yer arama/Search) |

| **Kullanım Alanı** | Lokal değişkenler, Dönüş adresleri | Dinamik nesneler, Büyük veriler |







---



## 2. Fragmantasyon (Parçalanma) Sorunu



Heap üzerinde sürekli dinamik bellek tahsisi yapıldığında iki tür parçalanma meydana gelir:



1.  **Dış Fragmantasyon (External):** Bellekte toplamda yeterli boş alan olsa da, bu alanın parçalı olması nedeniyle büyük bir bloğun sığamamasıdır.

2.  **İç Fragmantasyon (Internal):** İstenen miktardan daha büyük bir bloğun tahsis edilmesi sonucu, blok içinde kalan kullanılmayan alanın israf edilmesidir.



---



## 3. Yönetim Stratejileri



Dış fragmantasyonu önlemek ve performansı artırmak için şu yöntemler kullanılır:



### A. Memory Pooling (Bellek Havuzu)

Belleğin önceden sabit boyutlu bloklara (chunks) bölünmesidir.

* **Nasıl Çalışır:** Büyük bir alan rezerve edilir ve yumurta kolisi gibi eşit parçalara bölünür.

* **Artısı:** Dış fragmantasyonu sıfıra indirir ve $O(1)$ hızında tahsis sağlar.

* **Zayıf Yanı:** Bloklar veriden çok büyükse iç fragmantasyon artar.







### B. Slab Allocation (Dilim Ayırma)

Memory pooling'in daha esnek bir versiyonudur (Linux Kernel'da yaygındır).

* **Nasıl Çalışır:** Sık kullanılan nesneler (proses kontrol blokları vb.) için farklı boyutlarda havuzlar (slab'ler) oluşturur.

* **Amacı:** Nesne "kalıplarını" hazır tutarak önbellek verimliliğini artırmak.



### C. Buddy Memory Allocation

Belleği sürekli ikiye bölerek ihtiyaca en yakın $2^n$ boyutunu bulur.

* **Nasıl Çalışır:** Eğer 7 KB lazımsa, 8 KB'lık bir blok verilir. Yan yana duran iki boş "arkadaş" blok otomatik olarak birleşip daha büyük bir bloğa dönüşür.







---



## 4. Kısıtlı Sistemlerde Dinamik Bellek Riskleri



Gömülü sistemlerde veya kritik görev yazılımlarında `malloc` veya `new` kullanımı şu riskleri taşır:



* **Determinizm Kaybı:** Boş blok arama süresi belirsizdir (WCET riski).

* **Memory Leaks:** Küçük sızıntılar bile bellek bitti (OOM) hatasıyla sistemi çökertebilir.

* **Overhead:** Her blok için tutulan meta-data (boyut bilgisi vb.), kısıtlı RAM kapasitesinde büyük bir kayıptır.



### Örnek: Bellek Tahsis Süreçleri (Mantıksal Akış)



```bash

# Standart malloc (Riskli/Yavaş):

# [Heap'i tara] -> [Uygun boşluğu bul] -> [Meta-datayı güncelle] -> [Adresi döndür]



# Memory Pool (Güvenli/Hızlı):

# [Sıradaki boş bloğu listeden çek] -> [Adresi döndür]                                                                       # Sonuç

Gömülü sistemlerde veya yüksek performanslı oyun motorlarında hız hayati olduğu için Memory Pooling tercih edilirken; işletim sistemi gibi genel ve karmaşık yapılarda Slab veya Buddy sistemleri tercih edilerek bellek verimliliği optimize edilir.                                                                              

