---
layout: post
title: "CSS <strong>background</strong>"
subtitle: "How your rectangle is <strong>filled</strong>"
section: css
---

HTML elementinin fonu mətnin arxasında görünən şeydir. CSS in bizə hər bir elementə background tərtib etmək imkanı verməyinə baxmayaraq, bu xassə daha çox blok-level elementlərdə istifadə olunur.

Backgrounds ancaq hədəf elementə tətbiq olunur. Ancaq cox HTML elementinin şəffaf backgrounda malik oldugunu nəzərə alsaq, `body`-ə background versək bütün elementlərə background tətbiq edilmiş kimi görünəcək.

### background-color

Default dəyəri: `transparent`
children elementlərlə Inherited dir: no.

[color in CSS](/css-color-units.html) rəng təyin etməyin müxtəlif yollarını artıq əhatə etdiyimiz kimi, background təyin etməkdə sadədir:

{% highlight css %}
body{ background: #f2eee9;}
{% endhighlight %}

Bütün element **düz** background ilə doldurulmuş olacaq. Məzmununuzu asan oxumaq üçün həmişə uyğun mətn rəngini seçməyi unutmayın.

### background-image

Düz rənglər hər zaman kifayət etmirlər, CSS bizə elementlərin backgrounduna **şəkil** tərtib etməyə imkan yaradır.

Background şəklinin tətbiqi yalnız onun URL-ni göstərməyi tələb edir:

{% highlight css %}
body{ background-image: url(images/diagonal-pattern.png);}
{% endhighlight %}

Şəklin davranışı (öz özünə təkrarlanması, yerləşməsi, ölçüsü) başqa bir CSS xasssəsi ilə təyin edilir. `background-image` xassəsi sadəcə _hansı_ şəkli istifadə edəcəyimizi təyin edir.

Nəzərə alın ki, HTML elementi öz fon şəklinin ölçülərini nəzərə almır. Şəkil tətbiq olunduğu elementdən böyük olsa belə, element **şəkilə uyğunlaşmaq üçün ölçüsünü dəyişməyəcək**, çünki şəkil sırf dekorativdir və elementi dəstəkləmək üçündür.

### HTML images `<img>` və CSS background images xassəsi arasındakı fərqlər

HTML `<img>` element **məzmunun bir hissəsi olan şəkillər üçündür, CSS background images sırf **dekorativdir**. 

Bir şirkətin loqosu, qalereyanın kiçik şəkli, məhsulun şəkli... Bunların hamsı **məzmun** kimi nəzərə alınır və HTML `<img>` elementindən istifadə edir.

Diaqonal naxış, gözəl mənzərə, araba ikonu... Bunlar **decorative** olaraq nəzərə alına bilər, çünki onlar məzmunu _dəstəkləyir, lakin onun bir hissəsi deyil. Əgər onlar yoxa çıxsaydı, buna baxmayaraq veb-səhifə yenə də mənalı olardı.

 Bir çox dual seçimlərə gəldikdə, content və styling arasındakı sərhəd bulanıqdır. Bəzi vizual üsulları CSS background ilə əldə etmək daha asandır. Sadəcə özünüzdən soruşun ki, istifadə etdiyiniz şəkil səhifə üçün vacibdirmi? Əgr elədirsə, o zaman `<img>` elementindən istifadə edin.

#### Gradients

CSS həmçinin **rəng gradientlərini** fon şəkilləri kimi müəyyən etməyə imkan verir, 2 müxtəlif formada:

* `linear-gradient` bir istiqamətdə, düzbucaqlı formada gradientlər üçün
* `radial-gradient` bütün istiqamətlərdə, dairəvi formada gradientlər üçün

Biz bunu 8.3-cü fəsildə əhatə edirik: [CSS gradients](/css-gradients.html). Hələlik bilmək lazım olan yeganə şey background gradientlərinin **background şəkilləri** kimi qəbul edilməsidir.:

{% highlight css %}
body{ background-image: linear-gradient(white, grey);}
{% endhighlight %}

### background-position

Default olaraq, fon şəkli sonsuz təkrarlanacaq. Siz onun **orijinal mövqeyini** təyin edə bilərsiniz, üfüqi `x` və  `y` dəyərini seçməklə.

Hər bir koordinat üçün:

* pixel qiymətini `px`
* percentages, HTML elementinin ölçülərinə nisbətən
* `center`, `left`, `bottom` kimi...

istifadə edirsiniz

{% highlight css %}
body{ background-position: right bottom;}
{% endhighlight %}

Müxtəlif koordinat vahidlərini qarışdıra bilərsiniz:

{% highlight css %}
body{ background-position: center 20px;}
{% endhighlight %}

### background-repeat

Default olaraq, fon şəkli sonsuz təkrarlanacaq. Siz onu yalnız üfüqi, yalnız şaquli və ya hər iki istiqamətdə təkrarlanmasını ləğv edə bilərsiniz.

{% highlight css %}
body{ background-repeat: repeat-x;} /* Only horizontally */
body{ background-repeat: repeat-y;} /* Only vertically */
body{ background-repeat: no-repeat;} /* The background image will only appear once */
{% endhighlight %}
