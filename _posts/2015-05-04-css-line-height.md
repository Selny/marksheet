---
layout: post
title: "CSS <strong>line-height</strong>"
subtitle: "For <strong>readibility</strong> concerns"
section: css
---

`line-height` xassəsi, block-level elementlərə təttbiz olunduqda, adındanda göründüyü kimi, **hər bir sətrin yüksəkliyini** təyin edir. Paraqrafdakı sətirlər arasındakı boşluğun miqdarını təyin edən əksər qrafik proqramlarda (Photoshop kimi) tapılan sətir aralığı ilə qarışdırılmamalıdır. Baxmayaraq ki, onların hər ikisi eyni məqsədi daşıyır (mətn sətirləri arasında məsafəni təyin etmək), bunun müxtəlif yolları var təbii ki.

`line-height` xassəsi aşağıdakı dəyərləri istifadə edir:

* `px`
* `em`
* `%`
* vahidsiz sadəcə ədədlərdə ola bilər, `1.5` kimi

Vahidsiz dəyərlər əsasən faizlər kimi fəaliyyət göstərir. yəni `150%` `1.5`-ə bərabərdir. Sonuincu sadəcə daha yığcam və oxunaqlıdır.

### Why line-height is important

`line-height`-ın məqsədi mətniniz üçün oxunaqlı sətir aralığını təmin etməkdir. Çünki oxunaqlılıq mətnin ölçüsündən asılıdır, **dinamik** dəyərdən istifadə etmək tövsiyə olunur. Buna görə də 'px' istifadə etmək tövsiyə edilmir, çünki o, **statik** dəyəri müəyyən edir.

Bəzi hallarda, 'px' istifadə etmək faydalıdır (mətni şrift ölçüsünə görə deyil, başqa elementə görə şaquli şəkildə hizalamaq istədiyiniz zaman).
{: .info}

Çünki `%` və ya `em` dəyərlərindən istifadə gözlənilməz nəticələrə səbəb ola bilər, tövsiyə olunan metod **unitless numbers**-dir

* bodynin mətni üçün, mətnin ölçüsündən 1,5 dəfə çox olan sətir hündürlüyü tövsiyə olunur.
* headinglər üçün, 1.2 line-height tövsiyyə olunandır

{% highlight css %}
body{ font-size: 16px; line-height: 1.5;}
{% endhighlight %}

Mətnin hündürlüyünü hesablasaq belə ki, 16 * 1.5 = `24px` dir

### Line-height inheritance

Çünki `line-height` xassəsi child element ilə inherited dir sonradan hansı `şrift ölçüsü` tətbiq olunmasından asılı olmayaraq ardıcıl olaraq qalacaq.

{% highlight css %}
body{ font-size: 16px; line-height: 1.5;}
blockquote{ font-size: 18px;}
{% endhighlight %}

`blockquote` elementinin `27px` sətir hündürlüyü olacaq.
