---
layout: post
title:  "ESP-IDF Linux kurulumu"
date:   2020-07-04 18:51:34 +0300
categories: esp-idf esp32
tags: esp idf esp32 kurulum linux
---
Öncelikle ESP-IDF için gereken paketleri kurmamız gerekiyor. Bu paketler olmadan kurulumun bir anlamı olmayacaktır.

Kullandığımız dağıtıma göre şu paketleri kurmak yeterli olacaktır:

`Ubuntu ve debian tabanlı linuxler için`

{% highlight %}
sudo apt-get install git wget flex bison gperf python python-pip python-setuptools cmake ninja-build ccache libffi-dev libssl-dev dfu-util
{% endhighlight %}

`Arch tabanlı linuxler için`

{% highlight %}
sudo apt-get install git wget flex bison gperf python python-pip python-setuptools cmake ninja-build ccache libffi-dev libssl-dev dfu-util
{% endhighlight %}

Serial port izinleri için şu kodu yazmak yeterli olacaktır:

`Ubuntu ve debian tabanlı linuxler için`

{% highlight %}
sudo usermod -a -G dialout $USER
{% endhighlight %}

`Arch tabanlı linuxler için`

{% highlight %}
sudo usermod -a -G uucp $USER
{% endhighlight %}

Kurumları gerçekleştirdikten ve izinleri verdikten sonra esp adında bir dosya oluşturup ESP-IDF yi klonlamaya geldi sıra. 

{% highlight %}
cd ~/esp
git clone --recursive https://github.com/espressif/esp-idf.git
{% endhighlight %}

Klonlama işlemi bittikten sonra /esp-idf dosyasının içine giriyoruz ve install.sh dosyasını çalıştırıyoruz.

{% highlight %}
cd ~/esp/esp-idf
./install.sh
{% endhighlight %}


