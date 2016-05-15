---
author: barinali
comments: true
date: 2014-10-02 17:25:08+00:00
excerpt: 'Merhaba,

  Bu yazımda geçen gün karşılaştığım ve ekip arkadaşım sayesinde çözümünü öğrendiğim
  bir sorunu sizinle paylaşacağım.

  Atlassian firmasının yapmış olduğu HipChat adında bir anlık konuşma uygulaması var.
  Ve bu uygulama üzerinde birden fazla e-mail adresleriyle farklı farklı ekiplere
  dahilseniz hepsine aynı anda girememektesiniz. Bunun için HipChat''in önermiş olduğu
  bir çözüm mevcut. Bu çözümde bize birden fazla client''ı kurup farklı farklı client''lardan
  giriş yapıp birden fazla hesabımıza erişebileceğimizi söylemekte. Fakat bu benim
  için çözüm denilemeyecek gibi bir öneri.'
layout: post
link: http://blog.alibarin.com.tr/coklu-hipchat-oturumu/
permalink: /coklu-hipchat-oturumu
title: Çoklu HipChat Oturumu
categories:
- Uncategorised
tags:
- Atlassian
- Çoklu Oturum
- HipChat
- multiple sign-in
---

Merhaba,

Bu yazımda geçen gün karşılaştığım ve ekip arkadaşım sayesinde çözümünü öğrendiğim bir sorunu sizinle paylaşacağım.

[Atlassian](https://www.atlassian.com) firmasının yapmış olduğu [HipChat](https://hipchat.com) adında bir anlık konuşma uygulaması var. Ve bu uygulama üzerinde birden fazla e-mail adresleriyle farklı farklı ekiplere dahilseniz hepsine aynı anda girememektesiniz. Bunun için HipChat'in önermiş olduğu [bir çözüm](http://help.hipchat.com/knowledgebase/articles/64418-how-do-i-sign-in-to-multiple-accounts) mevcut. Bu çözümde bize birden fazla HipChat client'ı kurup farklı farklı client'lardan giriş yapıp birden fazla hesabımıza erişebileceğimizi söylemekte. Fakat bu benim için çözüm denilemeyecek gibi bir öneri.

Benim önerimse HipChat uygulamasını terminal yardımıyla birden fazla kez açmak;


    $ cd /Applications/HipChat/Contents/MacOS/
    $ ./HipChat --detach


Bu şekilde yeni bir HipChat uygulaması başlattıktan sonra terminaldeki işlemi sonlandırırsanız terminal sayesinde açtığınız HipChat'ler kapanacaktır.


    $ cd /Applications/HipChat/Contents/MacOS/
    $ nohup ./HipChat --detach & nohup


Fakat bu şekilde yeni bir HipChat açıp terminalden bağımsız şekilde çalıştırabilirsiniz. Bu güncelleme için [Umur Gedik](https://github.com/umurgdk)'e teşekkürler. :)
