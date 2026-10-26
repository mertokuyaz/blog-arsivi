---
title: "Yazılım Geliştiricilerinin Yan Projeleri için Uygun Bulut Sağlayıcısı Önerileri — Bölüm 1 / 2"
date: 2022-01-24 17:37:18 +0000
category: Bulut
tags: [aws, cloud, lightsail, docker]
description: "Yan projeleri bulutta yayımlarken maliyetleri öngörülebilir tutmak: AWS Lightsail, sanal sunucular ve container hizmetleri."
archive_url: https://web.archive.org/web/20220124174541/https://hashnode.com/post/yazilim-gelistiricilerinin-yan-projeleri-icin-uygun-bulut-saglayicisi-onerileri-bolum-1-2-ckysz2j5w0bwisus13385dsv0
image: /assets/images/bulut-maliyetleri.png
---

> **Arşiv notu:** Bu yazı ilk kez 24 Ocak 2022'de Hashnode'da yayımlandı ve [arşiv kaydından]({{ page.archive_url }}) geri getirildi. Görseller bu siteye yedeklenmiştir. Fiyatlar ve teknik bilgiler yazının yayımlandığı tarihe aittir.

Diyelim ki, aklınıza gelecekte size çok iyi kapılar açacak bir proje fikri geldi ve o proje için bir gece yarısı bilgisayarınızın başına geçtiniz. Bütün gece kod yazdınız ve 24 saatte harikalar yarattınız. Şimdi o projeyi dünyayla paylaşma zamanı.

Muhtemelen aklınıza ilk başta, projeyi üç bulut devinden birini (Amazon Web Services (AWS), Google Cloud Platform, Microsoft Azure) kullanarak paylaşmak gelecektir.

Ancak projenizi bulutta yayınlarken, işaretlediğiniz bir kutucuğun ay sonunda gelmesini beklediğiniz bulut faturasını x100 katına çıkarabileceğini biliyor muydunuz?

![foto 1.png]({{ '/assets/images/bulut-maliyetleri.png' | relative_url }})

AWS’te React ile yaptığı bir statik web uygulamasını paylaşarak; ay sonunda karşılaştığı 60.000 USD tutarında faturayı internette paylaşan bir Reddit kullanıcısı.

Yukarıdaki paylaşımda da görülebileceği üzere, Public Cloud servis fiyatları acemi kullanıcılar için şoke edici olabilir.

İşte bu blog yazısının amacı da, bulut servis sağlayıcıları hakkında ekonomik çözümler arayan kullanıcılara bazı tüyolar vermek.

## İlk ve En Sevdiğim Seçenek: Amazon Web Services Lightsail

Bu seçeneğin gözdem olmasının sebebi Amazon’un EC2 ve ECS (Elastic Container Service) gibi en meşhur servislerini düşük ve öngörülebilir fiyatlar ile kullanıcıya sağlaması.

![foto 2.png]({{ '/assets/images/amazon-lightsail.png' | relative_url }})

Amazon Lightsail’in sayfasına girdiğiniz zaman yukarıdaki landing page açılacaktır.  Amazon Lightsail ile EC2 ile aynı kalitede ve aynı standartlarda sanal sunucunuzu 5’te 1’i fiyatı ile daha uyguna kiralayabiliyorsunuz.

Üstelik fiyatlandırma daha öngörülebilir. EC2’de karmaşık seçenekler ve konfigürasyonlar bulut ile ilgili deneyimi olmayan bir yazılım geliştiricisi için çok zor olabilirken, Lightsail adeta bunların önüne geçmek için tasarlanmış. Yani, Amazon bir nevi burada kendini eleştirmiş.

![foto 3.png]({{ '/assets/images/eser-ozvataf-tweet.png' | relative_url }})

Eser Özvataf’ın yukarıda paylaştığım twitine ek olarak:

T3.Medium kurduğunuz zaman; bedeli Türk Lirasına çevirdiğinizde gelecek fatura güncel döviz kurları ile 580 liraya denk geliyor (1 USD = 13.5 TRY). Üstelik, EC2’nin aksine arayüzün kolaylığı sayesinde kurulum sırasındaki olası yanlış işaretlemeler de faturanızı şahlandırmıyor.

Peki T3 Medium’un muadili, AWS Lightsail’de ne kadar:

![t3 medium.png]({{ '/assets/images/lightsail-fiyatlandirma.png' | relative_url }})

20 USD.  Ayrıca 3.5 , 5 , 10 dolar gibi çok daha uygun seçenekler var!

Burada akıllara şu soru gelecektir: Faturamın, AWS Lightsail’de yazan fiyattan daha fazla gelme olasılığı var mı?

Evet ancak EC2’den farklı olarak, burada tek olasılık sizin belirtilen transfer limitinizi aşmanız.

Frankfurt’ta açtığınız T3.medium muadili sunucu 4000 GB (4 TB) transfer limitini aştığı zaman size her GB için 9 cent ek fatura gelecek (içeri ve dışarı yüklemeler dahil) .

## AWS Lightsail Container’da Uygulamalar Çalıştırma

Container teknolojisi, kullanıcılarına sağladığı avantajlar ile son 5 yılda yazılım geliştirmenin çok büyük bir parçası haline geldiler.

Container’ların hayatımıza kattığı avantajlara ilişkin daha detaylı okuma için Mustafa Alkan tarafından yazılan aşağıdaki blog yazısını okuyabilirsiniz:

https://medium.com/batech/docker-nedir-docker-kavramlar%C4%B1-avantajlar%C4%B1-901b37742ee0

### Docker’ın Avantajları Nelerdir?

1. (Yukarıdaki Mustafa Alkan tarafından yazılan blog yazısından alıntıdır.)

2. “Docker saniyeler içerisinde başlar, çünkü içerisinde barındırdığı her bir container sadece birer processtir. Böylece karşımıza lightweight bir yapı karşımıza çıkar. Bu da bizi sanal makinelerin hantallığından kurtarmış oluyor aslında.

3. Daha hızlı deployment süreci: İşte bence en önemli avantajı diyebilirim docker için. Dockerı kullanmak için yeni bir environment kurmaya gerek yoktur. Farklı sunucularda çalışmak isteyen developerlar sadece docker imageleri indirip o sunucuda imageleri çalıştırmaları yeterlidir. Böylece ‘benim makinemde çalışıyordu, sunucuda neden çalışmıyor!’ gibi sorunlardan da kurtulmuş oluruz.

4. Daha Kolay Yönetim ve Ölçeklendirme: Bir sanal makineye göre docker üzerindeki containerleri çok daha kolay bir şekilde çalıştırabiliriz veya istediğimiz zaman yok edebiliriz. Containerleri manage etmek için farklı toollar mevcut. En çok ta Orchestrator diye nitelendirdiğimiz Kubernetes teknolojisi daha popüler olarak kullanılıyor. Kubernetes, kısaca container kullanan uygulamaların dağıtımını, ölçeklendirmesini ve yönetilmesini otomatik hale getiren açık kaynak kodlu bir sistem. Kubernetes mimarisini ve çalışma sistemini detaylı olarak öğrenmek isterseniz sizin için çok faydalı olacağını düşündüğüm bir linki bırakıyorum.

5. https://www.mshowto.org/kubernetes-nedir.html

6. Daha İyi Kaynak Kullanımı Sanal makinelere göre tek bir sunucu üzerindeki kaynak tüketimi dockerda çok daha verimlidir. Daha az kaynak tüketimi ile daha fazla containeri çalıştırabiliriz.

Deployment Verimliliği:  Dockerın en güzel yanlarından birisi de şu: Siz localinizde test ettiniz, uygulamanızı Test veya Live ortamınıza attınız. (veya daha çeşitli ortamlar (dev, staging, pre-prod vs..) Localde çalıştırdığınız herşey burada da aynı şekilde çalışacak. Container ve Imagelerin tutulduğu dockerfile’ları da Git üzerinde tutmanız işinizi daha da kolaylaştıracağından eminim.

Farklı İşletim Sistemlerine Destek Vermesi Docker Windows, Linux, MacOs gibi farklı işletim sistemlerine destek verir.
Popüler Cloud Servislerle Entegre Edilebilir. Docker , AWS, Microsoft Azure, Ansible, Kubernetes, Istio ve daha fazla tool ve cloud hizmetlerle entegre şekilde çalışabilir.
Burada benim dikkat çekmek istediğim en önemli özellik deployment kolaylığı ve CI/CD süreçlerinde sağladığı avantajlar.

AWS Lightsail’de Containerlar İçin Herhangi Bir Container Depolama
Container registry ve versiyon kontrol araçlarını kullanabilirsiniz. Böylece kodunuzu güncellediğiniz zaman tek tıkla kodunuz AWS Lightsail’e yansır.

### Bazı Container Registry Araçları

Bunların fiyatlandırmaları farklı olabilir.
https://hub.docker.com/ (ücretsiz)

https://docs.gitlab.com/ee/user/packages/container_registry/

AWS Lightsail’de container barındırma ücretleri sanal sunucu ücretleri ile çok benzerlik gösteriyor. Sanal sunucu hizmeti EC2’nin muadili olurken bu servis ise ECS (Elastic Container Service) muadili ama dediğim gibi diğerinden çok daha uygun.
Peki, Amazon durup dururken neden bu servislerin çok daha uygununu çıkardı? REKABET.

Digital Ocean ve Linode gibi piyasaya AWS’den sonra giren uygun fiyatlı bulut sağlayıcıları ile rekabet etmek için.

Digital Ocean’ın sanal sunucu fiyatları ile AWS Lightsail’in fiyatları birbirine benzerlik göstermekte. İkisinin arasında kalmanız halinde AWS Lightsail’i tercih etmenizi öneririm çünkü AWS Lightsail’in yetersiz kaldığı durumlarda diğer AWS servislerine rahatça geçebilirsiniz.

Dipnot: AWS servisleri Türkiye adresli AWS hesabı ve Türk Bankası Kredi Kartı ile kiralanıyorsa, fiyatların üstüne %18 KDV eklenecektir.
Teşekkürler:

- Yukarıda blog yazısında geçen tweeti atan ve bu yazıyı yazmamda ilham kaynağı olan gönlümüzün getirian’ı Eser Özvataf’a  ( https://twitter.com/eserozvataf )
- Docker hakkında çok güzel bir yazı kalem alan Mustafa Alkan’a.
- Siz okuyucuya.
Benimle takipte kalın.
https://twitter.com/mertokuyaz
https://www.linkedin.com/in/mert-okuyaz-6a18b1147/
