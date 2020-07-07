---
layout: post
title:  "ESP-IDF Linux kurulumu"
date:   2020-07-04 18:51:34 +0300
categories: esp-idf esp32
tags: esp idf esp32 linux kurulum
---

ESP-IDF, ESP ürünleri için FreeRTOS kullanarak programlama yapmamızı sağlayan Espressif firmasının bize sunduğu geliştirme ortamı. Birçok önemli özelliğinin yanında en önemli özelliklerinden birisi de yazdığımız kodu şifreleyebilmemizi sağlaması. Geliştirme yaparken firmanın yayınladığı dokümanları okumak ve sürekli açıp bakmak çok faydalı olacaktır.

[API Reference](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/index.html)

[API Guides](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-guides/index.html)


Kuruluma geçecek olursak öncelikle ESP-IDF için gereken paketleri kurmamız gerekiyor. Bu paketler olmadan kurulumun bir anlamı olmayacaktır.

**Kullandığımız dağıtıma göre şu paketleri kurmak yeterli olacaktır:**

_Ubuntu ve debian tabanlı linuxler için_

{% highlight bash %}
sudo apt-get install git wget flex bison gperf python python-pip python-setuptools cmake ninja-build ccache libffi-dev libssl-dev dfu-util
{% endhighlight %}

_Arch tabanlı linuxler için_

{% highlight bash %}
sudo pacman -S --needed gcc git make flex bison gperf python-pip cmake ninja ccache dfu-util
{% endhighlight %}

**Serial port izinleri için şu kodu yazmak yeterli olacaktır:**

_Ubuntu ve debian tabanlı linuxler için_

{% highlight bash %}
sudo usermod -a -G dialout $USER
{% endhighlight %}

_Arch tabanlı linuxler için_

{% highlight bash %}
sudo usermod -a -G uucp $USER
{% endhighlight %}

**Kurumları gerçekleştirdikten ve izinleri verdikten sonra esp adında bir dosya oluşturup ESP-IDF yi klonlamaya geldi sıra.**


{% highlight bash %}
cd ~/esp
git clone --recursive https://github.com/espressif/esp-idf.git
{% endhighlight %}

**Klonlama işlemi bittikten sonra esp-idf dizini içine girip install.sh dosyasını çalıştırıyoruz.**
{% highlight bash %}
cd ~/esp/esp-idf
./install.sh
{% endhighlight %}

**Kurulum işlemi bittikten sonra alias ile export.sh dosyasını `.bash_profile` ya da `.profile` tanımlamak yeterli olacaktır.**
{% highlight bash %}
alias get_idf='. $HOME/esp/esp-idf/export.sh'
{% endhighlight %}

Diğer yazıda da ESP-IDF'in nasıl VSCode üzerinden kullanılabileceğini ve işlerimizi kolaylaştırabileceğimizi anlatıyor olacağım.

