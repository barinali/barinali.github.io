---
author: barinali
comments: true
date: 2014-11-04 22:28:01+00:00
excerpt: 'Mac OS X kullananların sıkca başvurduğu kısayollardan biridir cmd + shift
  + 3 (bütün ekranın ekran görüntüsü kaydetmek) veya cmd + shift + 4 (ekranın bir
  kısmının ekran görüntüsü kaydetmek) kısayolu.

  Sıkca kullandığım bu işlemin masaüstümü kirletmesinden hiçbir şekilde mutlu değildim
  ki kısa bir araştırma sonrası bu kısayollar aracılığıyla alınan ekran görüntülerin
  kaydedildiği varsayılan klasör adresinin nasıl değiştirildiğini öğrendim.'
layout: post
link: http://blog.alibarin.com.tr/mac-os-xte-screenshot-kayit-klasorunu-degistirmek
permalink: /mac-os-xte-screenshot-kayit-klasorunu-degistirmek
title: Mac OS X'te Screenshot Kayıt Klasörünü Değiştirmek
categories:
- Uncategorized
tags:
- change
- macOS
- save location
- screenshots
- terminal
---

Mac OS X kullananların sıkca başvurduğu kısayollardan biridir cmd + shift + 3 (bütün ekranın ekran görüntüsü kaydetmek) veya cmd + shift + 4 (ekranın bir kısmının ekran görüntüsü kaydetmek) kısayolu.

Sıkca kullandığım bu işlemin masaüstümü kirletmesinden hiçbir şekilde mutlu değildim ki kısa bir araştırma sonrası bu kısayollar aracılığıyla alınan ekran görüntülerin kaydedildiği varsayılan klasör adresinin nasıl değiştirildiğini öğrendim.

Bunun için birkaç basit adım izlememiz yeterli. Kayıt klasörünü masaüstündeki "Screenshots" adlı klasör olacak şekilde güncellemek için sırasıyla terminalde uygulamamız gereken komutlar;


    mkdir ~/Desktop/Screenshots/
    defaults write com.apple.screencapture location ~/Desktop/Screenshots/
    killall SystemUIServer


**Dipnot:** Eğer siz dosyaları kaydedeceğiniz klasörü kullanıcı arayüzü (gui) aracılığıyla oluşturduysanız vurgulanmış satırdaki _mkdir_ komutu ile yeni bir klasör oluşturmanıza gerek yok.
