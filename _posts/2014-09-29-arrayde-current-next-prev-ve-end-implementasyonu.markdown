---
author: barinali
comments: true
date: 2014-09-29 20:30:27+00:00
excerpt: 'Merhaba,


  Bu yazıda PHP‘deki Array‘in sahip olduğu bir takım işlevlerin JavaScript’teki Array‘e
  implemente edilişini anlatacağım. Benim yaygın olarak kullandığım bir kaç method
  mevcut. Bunlar sırasıyla; current, next, prev ve end methodları.'
layout: post
link: http://blog.alibarin.com.tr/arrayde-current-next-prev-ve-end-implementasyonu/
slug: arrayde-current-next-prev-ve-end-implementasyonu
title: Array’de Current, Next, Prev ve End İmplementasyonu
wordpress_id: 36
categories:
- Javascript
tags:
- array
- current
- end
- javascript
- method
- next
- php
- prev
---

Merhaba,

Bu yazıda [PHP](http://php.net/)'deki [Array](http://php.net/manual/tr/ref.array.php)'in sahip olduğu bir takım işlevlerin JavaScript'teki [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)'e implemente edilişini anlatacağım.

Benim yaygın olarak kullandığım bir kaç method mevcut. Bunlar sırasıyla; current, next, prev ve end methodları. Methodların işlevleri adlarından da anlaşılacağı üzere sırasıyla o anki elemanı, bir sonraki elemanı, bir önceki elemanı ve sonuncu elemanı döndürür.

Bu tarz işlemler için genelde;

    
    index = 0;
    arr = ["item 1", "item 2", "item 3"];
    
    console.log(arr[index++]);
    
    console.log(arr[index++]);


gibi yöntemler kullanmaktayız. Fakat bu şekilde her Array için dizinin indeksini bulup elle artırıp/azaltıp veyahut dizinin uzunluğunu bulup ona göre son elemanı bulmaktayız. Ama aşağıdaki gibi bir implementasyon yaparsak bu dizi gezme işlemini daha efektif şekilde kullanabiliriz.

    
    Array.prototype.index = 0;
    
    Array.prototype.current = function() {
      return this[this.index];
    }
    
    Array.prototype.prev = function() {
      return this[--this.index];
    }
    
    Array.prototype.next = function() {
      return this[++this.index];
    }
    
    Array.prototype.end = function() {
      return this[this.length-1];
    }


Buraya kadar herşey güzel, tamam. Ama aklınızda burada bir soru oluşması lazım. "Eğer dizide ilk/son elemana gelirsem bir sonraki adımımda boşluğa mı düşeceğim?". Üstteki implementasyon sonucunda dizilerin sonuna gelip aynı yönde bir adım daha atarsanız size undefined dönecektir.

Bu noktada yukarıdaki kod bloğumuzu aşağıdaki şekilde güncellersek herhangi bir sıkıntı kalmayacaktır.

    
    Array.prototype.index = 0;
    
    Array.prototype.current = function() {
      return this[this.index];
    }
    
    Array.prototype.prev = function() {
      return this[--this.index] || this[this.index = this.length-1];
    }
    
    Array.prototype.next = function() {
      return this[++this.index] || this[this.index = 0];
    }
    
    Array.prototype.end = function() {
      return this[this.length-1];
    }


Array'in prototype'ına müdahele edişimiz aklınızı karıştıysa ve bunun sebebi prototype'ı bilmemekten kaynaklanıyorsa [Fatih Kadir Akın](http://blog.fatihak.in/)'ın [Object Oriented Javascript'e Giriş: Prototype](http://blog.fatihak.in/object-oriented-javascript-e-giris-prototype/) adlı yazısını okuyup aydınlanabilirsiniz.
