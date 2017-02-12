---
author: barinali
comments: true
date: 2014-12-17 22:14:44+00:00
excerpt: Bazı durumlarda bilgisayarımızda bulunan web tabanlı geliştirmelerimizi veya
  benzeri durumdaki şeyleri yerel ağımızda bulunmayan birilerine sunmamız gerekebiliyor.
  Bu tarz bir işlem için DNS-O-Matic, no-ip, Dyn, easyDNS gibi ücretli hizmetleri
  kullanabiliriz. Fakat bunun yanı sıra ngrok gibi ücretsiz -isterseniz ücretli *-
  bir hizmeti kullanabilirsiniz. Bilgisayarınız üzerindeki herhangi bir port üzerinden
  kendinize sunduğunuz servisi, ngrok ile size vereceği {customsubdomain}.ngrok.com
  (örn. http://2bf53de0.ngrok.com) adresi üzerinden internete açıp herkese sunabileceksiniz.
layout: post
link: http://blog.alibarin.com.tr/ngrok-ile-internete-acilmak/
permalink: ngrok-ile-internete-acilmak
title: ngrok ile İnternet'e Açılmak
categories:
- Uncategorized
tags:
- expose to internet
- ngrok
---

Bazı durumlarda bilgisayarımızda bulunan web tabanlı geliştirmelerimizi veya benzeri durumdaki şeyleri yerel ağımızda bulunmayan birilerine sunmamız gerekebiliyor. Bu tarz bir işlem için [DNS-O-Matic](http://dnsomatic.com/), [no-ip](http://www.noip.com), [Dyn](http://dyn.com), [easyDNS](https://www.easydns.com/) gibi ücretli hizmetleri kullanabiliriz. Fakat bunun yanı sıra [ngrok](https://ngrok.com/) gibi ücretsiz -isterseniz ücretli- bir hizmeti kullanabilirsiniz. Bilgisayarınız üzerindeki herhangi bir port üzerinden kendinize sunduğunuz servisi, ngrok ile size vereceği subdomain.ngrok.com (örn. http://2bf53de0.ngrok.com) adresi üzerinden internete açıp herkese sunabileceksiniz.

Bunun için öncelikle [ngrok](https://ngrok.com/download)'un sitesi üzerinden kendisini indiriyoruz. Bilgisayarımıza indirdiğimiz ngrok.zip adlı dosyayı terminal üzerinden unzip ngrok.zip  ile içindekileri dışarıya çıkartıyoruz. Ardından en basit şekilde ./ngrok 80  diyerek 80. portumuzu ngrok'un rastgele şekilde oluşturacağı bir subdomain ile internete açıyoruz. 80. port yerine, istediğiniz herhangi bir portu da kullanabilirsiniz.

Bu şekilde istediğimiz portu internete açtıktan sonra http://127.0.0.1:4040 adresinden internete açtığımız port üzerindeki veri alış-verişini izleyip gözetleyebiliyoruz.

Terminal üzerinden ./ngrok 80 dediğimizde karşımıza bu görüntü çıkacak;

[![ngrok on terminal](http://blog.alibarin.com.tr/wp-content/uploads/2014/12/Screen-Shot-2014-12-18-at-12.02.47-AM.png)](http://blog.alibarin.com.tr/wp-content/uploads/2014/12/Screen-Shot-2014-12-18-at-12.02.47-AM.png)

Eğer ngrok'u çalıştırdığınızda rastgele bir subdomain ile değil de, belirttiğiniz subdomain ile çalışmasını istiyorsanız ./ngrok -subdomain ahaha 80  şeklinde çalıştırıp ahaha.ngrok.com adresi ile 80. portunuzu internete açabilirsiniz.

[![ngrok with custom subdomain in terminal](http://blog.alibarin.com.tr/wp-content/uploads/2014/12/Screen-Shot-2014-12-18-at-12.07.35-AM.png)](http://blog.alibarin.com.tr/wp-content/uploads/2014/12/Screen-Shot-2014-12-18-at-12.07.35-AM.png)

Eğer bu subdomain'i bir başkası sizden önce kullandıysa hâliyle ngrok "Server failed to allocate tunnel: The tunnel http://ahaha.ngrok.com is already registered." şeklinde bir uyarı vererek kullanmanıza izin vermeyecektir. ngrok'un ücretli olarak sunduğu sanırım tek bir özelliği mevcut. Bu da reserved subdomain özelliği. Eğer [ngrok'un ödeme sayfası](https://ngrok.com/pay)na bakarsanız $2.08/aylık gibi komik bir rakama bu özelliği sunduklarını göreceksiniz. Yıllığı ise $25/year'a denk gelmekte. Eğer servis ciddi anlamda işinizi görecekse ve istediğiniz subdomain'i kendiniz için rezerve etmek istiyorsanız ödemesi komik olan bir rakam istemekte.

Bunların yanı sıra eğer kendi bilgisayarınızda değil de başka bir adresteki portu internete açmak istiyorsanız yine aynı şekilde ./ngrok 192.168.2.2:80  tarzında bir kullanım ile 192.168.2.2 numaralı IP adresine sahip bilgisayardaki 80. portu internete açabilirsiniz.

ngrok'ı daha da özelleştirilmiş şekilde nasıl kullanabileceğinizi [bu sayfadan](https://ngrok.com/usage) öğrenebilirsiniz.
