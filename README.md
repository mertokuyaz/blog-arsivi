# Mert Okuyaz — Blog arşivi

Markdown tabanlı, GitHub Pages üzerinde ücretsiz yayımlanan Jekyll blogu.
Bu depo `mertokuyaz.github.io` deposundan bağımsızdır.

## Tema

[geohot'un blogundaki](https://geohot.github.io/blog/) klasik **Minima** teması kullanılır.
Tema GitHub Pages tarafından sağlanır; özel layout geçersiz kılmaları yoktur.
Yazı listesi, açık arka plan ve mavi bağlantılar Minima'nın varsayılan görünümüdür.
Yazı sayfalarındaki metinler `assets/main.scss` üzerinden 2,5 kat büyütülmüştür (gövde: 16 → 40 px); ana sayfa değişmez.
Başlık, açıklama ve sosyal bağlantılar `_config.yml` dosyasından düzenlenebilir.

## Adresler

- Blog: https://mertokuyaz.github.io/blog-arsivi/
- RSS: https://mertokuyaz.github.io/blog-arsivi/feed.xml

## Yeni yazı ekleme

`_posts/YYYY-AA-GG-yazi-basligi.md` adında bir dosya oluşturun:

```markdown
---
title: "Yazının başlığı"
date: 2026-10-26 12:00:00 +0300
category: Yazılım
description: "Yazının kısa özeti."
---

Yazının Markdown içeriği burada.
```

`main` dalına yapılan değişiklikler GitHub Pages tarafından otomatik yayımlanır.
Görselleri `assets/images/` altında saklayın ve Markdown içinde şu şekilde kullanın:

```liquid
![Görsel açıklaması]({{ '/assets/images/ornek.png' | relative_url }})
```

## Kendi domainini bağlama

1. Bu deponun **Settings → Pages → Custom domain** alanına örneğin `blog.alanadin.com` girin.
2. Domainin DNS panelinde `blog` adına, `mertokuyaz.github.io` hedefine bir **CNAME** kaydı ekleyin. Hedefe `/blog-arsivi` eklemeyin.
3. `_config.yml` içindeki `url` değerini `https://blog.alanadin.com`, `baseurl` değerini `""` yapın.
4. Sertifika hazır olunca **Enforce HTTPS** seçeneğini açın.
5. Domaini GitHub hesap ayarlarında doğrulamanız önerilir. Mevcut DNS kayıtlarını değiştirmeden önce hangi hizmete ait olduklarını kontrol edin.

Bu ayarlar yalnızca bu depo içindir; `mertokuyaz.github.io` deposunu değiştirmek gerekmez.
Domainin satın alma/yenileme bedeli hariç barındırma ücretsizdir.

## Yerelde çalıştırma (isteğe bağlı)

Ruby ve Bundler kuruluysa:

```sh
bundle install
bundle exec jekyll serve
```

Önizleme: http://127.0.0.1:4000/blog-arsivi/

## Kurtarılan yazı

24 Ocak 2022 tarihli Hashnode yazısı Internet Archive kaydından geri getirilmiştir.
Yazının metni korunmuş; dört görsel bu depoya yedeklenmiştir.
Özgün bağımsız `.md` dosyası masaüstündeki `HER ŞEY` klasöründe bırakılmıştır.
