---
layout: post
title:  "ESP-IDF Non-volatile Storage(NVS) Kullanımı"
date:   2020-07-15 21:51:34 +0300
categories: esp-idf esp32
tags: esp idf esp32 nvs non-volatile storage
---

NVS yani Non-volatile storage, çevirisine baktığımızda kalıcı, uçucu olmayan anlamlarına gelen, kısaca anahtar-değer çiftlerini flaşta saklamamıza yarayan bir kütüphanedir. Malum değişkenler her cihaz yeniden başladığında ona atanan değere geri döner. Ekstra elde ettiğin ya da kullanıcıdan aldığın veriyi saklamak istediğinde onu bir yere yazabilmeli ve cihaz her yeniden başladığında onu yazdığın yerde bulabilmelisin. Bu anlattığım senaryo içinde verileri kalıcı olarak tutabileceğimiz hafızalar gerekiyor. Bunlardan bir tanesi de NVS yani Non-volatile storage. Ayrıca bu alan üzerinde şifreleme yapabilir ve verilerimizi güvende tutabiliriz. Tabi her şeyi kendi kaynağından okuyup daha güzel şekilde anlayabilirsiniz ve benim burda bahsetmediklerimi görebilirsiniz.


[Non-volatile Storage Library](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/storage/nvs_flash.html)

**Gelelim bu alanda neler saklayabileceğime, bu alanda saklayabileceğimiz anahtar-değer çiftleri şu şekilde olabilir;**

+Anahtarlar maksimum 15 karekter uzunluğunda ASCII karekter kümesinden karekterler olabilir.
+Değerler ise integer tipler: uint8_t, int8_t, uint16_t, int16_t, 32, 64,
+bloblar,
+sıfır-sonlu dizeler olabilir.

**Peki bu alana yazdığımız verileri nasıl silebiliriz?**

>Flashı tümden silebilmek için idf.py erase_flash demek yeterli olacaktır.

**Kısaca nasıl kullanıldığından bahsetmem gerekirse**

Öncelikle kütüphaneleri include ediyoruz.

`#include "nvs_flash.h"
#include "nvs.h"`

Daha sonra nesnesini oluşturuyoruz.

`nvs_handle_t my_handle;`

NVS i yazma ve okuma yetkisiyle açıyoruz.

`nvs_open("storage", NVS_READWRITE, &my_handle)`

Yazma işlemi için set komutunu kullanıyoruz ve girdiğimiz anahtar kelimeye gönderdiğimiz değeri yazıyoruz. Daha sonra commit ediyoruz.

`nvs_set_str(my_handle, "PASS", pass);
nvs_commit(my_handle);`

Okuma işlemini de tam tersi şeklinde get ile yapıyoruz.

`nvs_get_str(my_handle, "PASS", PASS, &required_size_PASS);`

Daha fazla örnek kod incelemek isterseniz vermiş olduğum kütüphane linkinden örnekleri inceleyebilirsiniz.

Ayrıca geliştirmekte olduğum [ESP-IDF Wifi Manager](https://github.com/AHakan/WifiManager) projemi de inceleyebilirsiniz.
