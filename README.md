# Mert Okuyaz — Blog arşivi

Markdown tabanlı, GitHub Pages üzerinde ücretsiz yayımlanan Jekyll blogu.
Bu depo `mertokuyaz.github.io` deposundan bağımsızdır.

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
