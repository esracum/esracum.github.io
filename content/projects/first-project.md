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
## Proje Konusu :
 Böbrek tümörü ameliyatlarında, ameliyat zorluğunu belirleyen MAP (Mayo Adhesive Probability) skorunu hızlı ve doğru şekilde elde etmek amacıyla böbrek çevresindeki perinefrik yağ dokusunun kalınlığı ve stranding (yapışık yağ dokusu yoğunluğu) parametreleri otomatik olarak hesaplanmıştır.

## Proje Detayları 
Proje kapsamında, BT (Bilgisayarlı Tomografi ) görüntüleri üzerinde derin öğrenme ve görüntü işleme yöntemleri kullanılarak cerrahi planlama süreçlerini iyileştiren bir sistem geliştirilmiştir. Model eğitiminde kullanılan veri seti elle hazırlanmıştır. *Böbrek segmentasyonu* için *U-Net modeli* kullanılmıştır. Stranding (yapışık yağ dokusu yoğunluğu) eşiğinin belirlenmesinde ise görüntü kontrastını artırmak için *CLAHE* yöntemi uygulanmış ve stranding hesabında otomatik eşikleme için *Otsu*, *Yen*, *Triangle* ve *Mean* gibi farklı yöntemler kıyaslanmıştır. Perinefrik yağ uzunluğunun tespitinde Z-skora dayalı fonksiyonlar kullanılarak bölgesel yoğunluk analizleri gerçekleştirilmiştir.

## Elde Edilen Sonuçlar
Yağ kalınlığı ölçümlerinde uzmanların elle yaptığı değerlendirmelerle *%89* oranında uyum sağlanırken stranding skorlamasında *%77* oranında örtüşme elde edilmiştir. 

> ⚠️ Ölçümdeki sapmalar, farklı BT cihazları, tarama protokolleri ve görüntü format dönüşümlerinden kaynaklanmaktadır. Gelecekte, DICOM formatında daha fazla veri kullanılması, görüntülerin JPG yerine DICOM formatında işlenmesi gelişmiş model mimarileri (U-Net++, Attention U-Net gibi) ile segmentasyon doğruluğunun arttırılması planlanmaktadır. Geliştirilen sistem, cerrahi planlama sürecinde hızlı ve doğru karar verilmesini sağlayarak ameliyat başarısını artırmaya önemli katkılar sunmaktadır. 





 Örneğin; *"https://kullanaciadiniz.github.io/"* şeklinde veya *"https://kullaniciadiniz.github.io/depoismi/"* şeklinde bir alan adına sahip olabiliyorsunuz. Aynı zamanda ücretli bir şekilde satın aldığınız domain uzantılarını da GitHub Pages ile kullanarak web sayfalarınızı özel bir alan adıyla yayına alabiliyorsunuz. 

 *Bknz. [HUGO Themes](https://themes.gohugo.io/)*

 [Install HUGO on Windows](https://gohugo.io/installation/windows/) dökümanından faydalanabilirsiniz. 

Öncelikli olarak HUGO'yu özelleştirmek ve Github depomuz ile arasındaki bağlantıyı kurabilmek için **"Git"** kurulumu yapmamız gerekiyor. Bunun için terminale şu komutu yazın;
```properties
sudo dnf install git
```
#### HUGO Tema Seçimi ve Blog Kurulumu
HUGO kurulumuna geçmeden önce, kullanmak istediğiniz temayı belirlemeniz çok daha iyi olacaktır. Temanın kurulum yönergelerine göre alt yapınızı oluşturmanız, temanın düzgün bir şekilde çalışması ve kolay yönetilebilmesi için önemlidir. Biz tema olarak [Papermod](https://github.com/adityatelange/hugo-PaperMod) kullanacağız. Örneğin; PaperMod'un yapımcısı bizlere HUGO kurulumunu "YAML" formatında yapmamızın, dosyaların okunması ve kullanımı hakkında çok daha rahat olacağını belirtiyor. YAML formatında yeni bir HUGO blog kurulumu için terminale şu komutu girmemiz gerekiyor;
```properties
hugo new site BenimBlogum --format yaml
# Burada "BenimBlogum" yazan yeri kendinize göre değiştirmeniz gerekiyor.
```
> ℹ️ Tema yükleme işlemine geçmeden önce terminal üzerinde kendi blog klasörünüzde Git ilişkilendirilmesini ayarlamanız gerekiyor. Bunun için **"git init"** komutunu klasör içerisinde çalıştırmalısınız.

Daha sonrasında PaperMod temasının kurulumuna geçeceğiz. Bunun için geliştiricinin önerdiği şekilde "Git Submodule" ile kurulum gerçekleştireceğiz;
```properties
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive 
```
Ardından HUGO blogunuzun kurulu olduğu dizinde şu komutu çalıştırın; 
```properties
git submodule update --remote --merge
```
Tema dosyaları kendi klasörümüze yüklendiğine göre artık "config" dosyası yapılandırma işlemine geçebiliriz. Klasörünüzde bulunan **"hugo.yaml"** isimli dosyaya şu satırı eklemeniz gerekiyor;

```properties
theme: ["PaperMod"]
```

Bu ayarlamayı yaptıktan sonra, başka hiç bir şey yapmadan HUGO bloğumuzun aktif bir şekilde lokalde çalışıyor olması gerekiyor. Bunu test etmek için terminalde hugo kurulumu yaptığımız klasörde şu komutu yazıyoruz; 
```properties
hugo serve
```

![Lokal Bağlantı Adresi GÖrseli](https://private-user-images.githubusercontent.com/91957149/480462588-c1204dc7-50e1-463b-984d-36df922be288.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTU3NzM3MjMsIm5iZiI6MTc1NTc3MzQyMywicGF0aCI6Ii85MTk1NzE0OS80ODA0NjI1ODgtYzEyMDRkYzctNTBlMS00NjNiLTk4NGQtMzZkZjkyMmJlMjg4LmpwZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MjElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODIxVDEwNTAyM1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWRjNTYyOTgxZDVlNTFjNDhjNGI1NDI5NGZmOTg0YjVjYjY0NzM1N2EzZDJlZTc0ODAxYzUwZmVkNDZjN2YzNzYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.IaCjWfzIldSXlly8U7fMXJsKdNlG8KwhIt3MO6kLaw0)

Her şey yolunda giderse gördüğünüz gibi bir lokal bağlantı adresi elde ediyoruz ve bu bağlantıyı tarayıcımızla açtığımızda HUGO blogumuz bizi karşılıyor. 

>ℹ️ Lokal sitemize baktığımızda boş bir sayfa görebilirsiniz. Bunun için yine config dosyamızı optimize etmemiz gerekiyor. Çok fazla uğraşmadan [PaperMod Örnek config.yaml dosyası](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/#sample-configyml) sayfasındaki örneği kullanabilirsiniz. Elbette burda kullanmayacağınız özellikleri silebilir, kullanacağınız kısımları düzenleyebilirsiniz. Yine **"posts"** klasörü altında *"yaziniz.md"* isimli bir dosya oluşturarak [Örnek Sayfa Dosyası](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/#sample-pagemd) kısmındaki hazır şablonu kullanarak ilk yazınızı hazırlayabilirsiniz. Yazılarınızı "markdown" formatında yazmanız gerektiğini lütfen unutmayın. Bknz. [Markdown Basic Syntax](https://www.markdownguide.org/basic-syntax/)

## Lokal Proje Github Pages Deploy Aşaması 
Lokal üzerinden hazırlamış blogumuzu internete açabilmek için (Github Pages Deploy), öncelikli olarak Github üzerinden bir hesap oluşturmanız gerekiyor. Hemen sonrasındayda bir repository (depo) oluşturmanız gerekli. 

>ℹ️ Depo isminizi belirlerken eğer ana dizinde subdomain kullanmak istiyorsanız depo isminizi *"github-kullanici-adiniz.github.io"* şeklinde belirlemeniz gerekiyor. Aksi halde "Blog" tarzı bir depo ismi belirlemeniz durumunda web siteniz *"kullanici-adiniz.github.io/blog"* gibi bir adreste yayınlanacaktır.

Depoyu oluşturduktan sonra lokal projemizi depoya göndermemiz gerekiyor. Bunun için sırasıyla terminalde blog dizininde şu komutları çalıştırmalısınız;

```properties
git add . 
git commit -m "İlk HUGO Kurulumu"
## Burda tırnak içerisindeki kısma kendinize göre yaptığınız işlemler hakkındaki yorumu girebilirsiniz.
git remote add origin https://github.com/kullanici-adiniz/depo-isminiz.git
## Burada kullanıcı adı ve depo ismini düzenleyiniz!
git branch -M main
git push -u origin main
```
>⚠️ Bu aşamada terminal sizden Github kullanıcı adı ve şifrenizi isteyecektir. Burada şifre olarak kullanmak için bir "Token" oluşturmanız gerekiyor. Bunun için Github Settings>Developer Settings>Personel access tokens>Tokens(classic)>Generete New Token aşamalarını izleyerek **"repo ve workflow"** yetkileri olan bir token oluşturmanız gerekiyor. Bunu terminal üzerinde Github şifremiz olarak kullanacağız!

Bu aşamada dosyalarımız artık Github depomuza gönderilmiş oluyor. Ancak "Deploy" aşamasında sorun yaşamamak için bir ayar yapmamız lazım. 

>ℹ️ Blog klasörümüzde "Gizli Klasörleri Göster" seçeneğini aktif etmeli ve ardından *".github/workflows"* klasörlerini oluşturmalıyız. Bu dizine **"hugo.yaml"** isimli bir dosya oluşuturup bu dosyayı da [Hugo Host on Github Pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/) sayfasında gösterildiği şeklilde yapılandıralım. (Step 6'da belirtilen kodu dosya içerisine kopyala yapıştır yapmanız yeterli olacaktır)

Daha sonrasında lokal üzerinde bazı değişiklikler yaptığımız için bu değişiklikleri tekrardan Github depomuza göndermemiz gerekecek. Bunun için terminalde;

```properties
git add . 
git commit -m "Create a Github Workflow HUGO.YAML"
## Burda tırnak içerisindeki kısma kendinize göre yaptığınız işlemler hakkındaki yorumu girebilirsiniz.
git push -u origin main
```
