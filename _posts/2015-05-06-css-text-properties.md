---
layout: post
title: "CSS <strong>text</strong> properties"
subtitle: "Other <strong>text</strong> alterations"
section: css
---

Bir neçə `font-*` xassələri ilə yanaşı, CSS bir çox `text-*` xassəsi də təqdim edir.

### text-align

`text-align` xassəsi block-leve elementlərə tətbiq edilməlidir və textinin və ya inline child elementlərinin necə düzüləcəyini təyin edir.

{% highlight css %}
body{ text-align: left;}
{% endhighlight %}

Ən çox istifadə olunan dəyərlər:

* **left**
* **right**
* **center**
* **justify**

Microsoft Word və ya Photoshopda görmüş ola biləcətiniz alignment düymələri ilə eynidir:

<i class="fa fa-align-left"></i> <i class="fa fa-align-right"></i> <i class="fa fa-align-center"></i> <i class="fa fa-align-justify"></i>

`justify` dəyəri **tövsiyə olunan deyil**. Baxmayaraq ki, visual olaraq cəzbedici görünür, mətndən ibarət düzbucaqlı əmələ gətirir. Ancaq heç oxunaqlı deyil
{: .info}

`text-align` xassəsinin default dəyəri `start`-dır. Əsasən, `start` ya `left` ya da `right` ola bilər, HTML sənədində təyin edilmiş **istiqamətdən** asılıdır.

`direction` CSS xassəsidir ki, ya `ltr` (left to right) ya da `rtl` (right to left) ola bilər:

* Əgər `ltr` secilidirsə, `start` `left`-ə bərabərdir
* Əgər `rtl` seçilidirsə, `start` `right`-a bərabərdir

### text-decoration

`text-decoration` xassəsi textə xətt  əlavə etmək üçün istifadə olunur.

Default Qiyməti: `none`

{% highlight css %}
.deleted{ text-decoration: line-through;}
{% endhighlight %}

<div class="result">
  <p style="text-decoration: line-through;">Deleted</p>
</div>

Mümkün dəyərləri:

* `overline`
* `underline`
* `line-through`

Default olaraq, HTML linklərinin (`<a>`) tətbiq edilmis `text-decoration: underline;` defaul dəyəri var. Coderlərin ilk olaraq gördüyü işlərdən bir bu default dəyəri silməkdir:

{% highlight css %}
a{ text-decoration: none;}
{% endhighlight %}

### text-indent

`text-indent` xassəsi blok-level elementlərin birinci sətrinin birinci hərfindən əvvələ boşluq əlavə etməyə imkan verir.

Default qiyməri: `0` (zero)

{% highlight css %}
blockquote{ text-indent: 30px;}
{% endhighlight %}

<div class="result" style="max-width: 400px;">
  <blockquote style="text-indent: 30px;">People always make the mistake of thinking art is created for them. But really, art is a private language for sophisticates to congratulate themselves on their superiority to the rest of the world. As my artist’s statement explains, my work is utterly incomprehensible and is therefore full of deep significance.</blockquote>
</div>

Diqqət necə yalnız **birinci sətir** indented dir. Bütün mətn blokunu ofset etmək istəyirsinizsə, [paddings](/css-padding.html) dən istifadə edə bilərsiniz.

`font-size` xassəsinə gəldikdə,`px`, `em`, hətta `%` dəyərlərindən istifadə edə bilərsiniz.
{: .info}


### text-shadow

Əgər bir dəfə belə olsa Photoshop istifadə etmisinizsə, ehtimal ki drop shadow tool-dan istifadə etmisinizdir. CSS-də, text-ə kölgə əlavə edə bilərsiniz, ya daha həvəskar, ya da daha oxunaqlı etmək üçün.

Aşağıdakı kimi təyin edə bilərsiniz:

* `x` üfüqi ofset
* `y` şaquli offset
* `blur`
* `color`

{% highlight css %}
h1{ text-shadow: 0 2px 5px rgba(0,0,0,0.5);}
{% endhighlight %}

<div class="result">
  <h1 style="text-shadow: 0 2px 5px rgba(0,0,0,0.5);">Hello World</h1>
</div>

Ancaq `x` və `y` dəyərləri tələb olunur. `blur` default olaraq `0` (zero)-dır, `rəng` isə mətnin default rənginə uyğundur.

Bu xassə mürəkkəbdir, ona görə də onu daha ehtiyatla istifadə edin!
{: .info}
