---
layout: post
title: "CSS <strong>font-family</strong>"
subtitle: "Choosing a <strong>font</strong>"
section: css
---

CSS bir çox **şrift** xüsusiyyətlərini təmin edir, bu birbaşa mətnin ekrana çıxarılmasına təsir edir. `font-family` xassəsi  _hansı_ şriftin istifadə olunacağını müəyyən edir.

### Generic font families

Fontları 5 **ümumi** ailəsi var:

* `serif` fontlarda hər simvolun sonuna kiçik xətlər əlavə olunur
* `sans-serif`
* `monospace`
* `cursive`
* `fantasy`

`cursive` və `fantasy` heç vaxt istifadə olunlmur.
{: .info}

Çünki `font-family` xassəsi bütün HTML children elementləri tərəfindən inheriteddir, bütün HTML elementlərinin ancestor elementinə tətbiq etməklə bütün HTML sənədi üçün şrift təyin edə bilərsiniz: `<body>` elementi.

{% highlight css %}
body{ font-family: sans-serif;}
{% endhighlight %}

Bu CSS qaydası ilə, web səhifə istifadəçi tərəfindən təyin edilmiş **sans-serif** şriftindən istifadə edəcək.

### Web-safe fonts

Ümumi şrift adlarından istifadə ilə bağlı problem ondan ibarətdir ki, veb-səhifənizin dizaynı istifadəçinin öz parametrlərində təyin etdiyi şriftdən asılıdır.

Yəqin ki, veb səhifənizin hər kəsin kompüterində eyni görünməsini istədiyiniz kimi, **spesifik** font istifadə etmək istəyəcəksiniz. Belə etmək üçün, sadəcə şrift **adını** istifadə edin.

{% highlight css %}
body{ font-family: Arial;}
{% endhighlight %}

Veb səhifəniz Arial-dan istifadə edəcək **istifadəçinin kompüterində quraşdırılmış olması şərtilə**. Əgər Arial istifadəçinin komputerində mövcud deyilsə, o zama brauzerin default sans-serif şriftindən istifadə edəcək (Çox zaman).

Arial təhlükəsiz seçim kimi düşünülmüşdür, çünki bütün Windows və Mac komputerlərdə quraşdırılmışdır, və bir çox Linux sistemlərində. Buna gorə də Arial **web-safe** şrift kimi hesab olunur: qısaca desək CSS-də onu təhlükəsiz şəkildə istifadə edə bilərsiniz və istifadəçinin komputerində quraşdırıldığından demək olar ki, əmin ola bilərsiniz.

**9** web-safe fonts var:

* Arial
* Arial Black
* Comic Sans MS
* Courier New
* Georgia
* Impact
* Times New Roman
* Trebuchet MS
* Verdana

### Şriftlər siyahısının tətbiqi

Baxmayaraq ki, bu şriftlərin _hər hansının_ istifadəsi `font-family` xassəsi üçüb təhlükəsizdir, **list of font families** yazmaqla **fallback** dəyər təyin edə bilərsiniz:

{% highlight css %}
body{ font-family: Arial, Verdana, sans-serif;}
{% endhighlight %}

`font-family` üçün **multiple values** təyin etməklə, brauzer birinci dəyərin `Arial` olduğunu görəcək onu istifadə edəcək. Əgər bu mövcud deyilsə, o zaman növbətini istifadə edəcək `Verdana`. Son olaraq, əgər buda mövcud deyilsə, o zaman brauzerin default sans-seriv dəyərindən istifadə edəcək.

**generic family**-dən istifadə etmək üçün yaxşı təcrübədir. Əgər istifadə etmək üçün spesifik font təyin edə bilmirsinizsə, heç olmasa istədiyiniz şriftin _tipini_ təyin edə bilərsiniz.

Çünki dizaynerlər daha orijinal şriftlərdən istifadə etmək istəyirlər, lakin yenə də veb səhifələrinin hər kəsin kompüterində eyni görünməsini istəyirlər, veb səhifəyə **şrift daxil etmək** mümkündür. Bu yolla, onlar istifadəçinin kompüterində olmasa belə şriftin mövcud oldu]una əmin olurlar, sadəcə olaraq veb sayt şrifti təmin etdiyi üçün.

Biz `@font-face` adlı bu metodu nəzərdən keçirəcəyik, və Google Fonts və ya Typekit kimi xidmətlərin sizə necə kömək edə biləcəyinə görəcəyik.
