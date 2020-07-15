---
layout: post
title:  "ESP-IDF Non-volatile Storage(NVS) Kullanımı"
date:   2020-07-15 21:51:34 +0300
categories: esp-idf esp32
tags: esp idf esp32 nvs non-volatile storage
---

NVS yani Non-volatile storage, çevirisine baktığımızda kalıcı, uçucu olmayan anlamlarına gelen, kısaca anahtar-değer çiftlerini flaşta saklamamızı sağlayan 
kütüphanedir.

**Anahtar-değer çiftleri nasıl olabilir?**
Anahtarlar maksimum 15 karekter uzunluğunda ASCII karekter kümesinden karekterler olabilir.
Değerler ise integer tipler: uint8_t, int8_t, uint16_t, int16_t, 32, 64,
bloblar,
sıfır-sonlu dizeler olabilir.

devamı geliyor.

>Flashı tümden silebilmek için idf.py erase_flash demek yeterli olacaktır.
