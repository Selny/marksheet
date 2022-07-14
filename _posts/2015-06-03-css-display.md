---
layout: post
title: "CSS <strong>display</strong>"
subtitle: "Changing the <strong>type</strong> of an HTML element"
section: css
---

Əsasən [2 növ HTML elementinin](/html-block-inline.html) necə olduğunu gördük.: **block-level** elementlər və **inline** olanlar. **list-item** və ya **table-cell** kimi bir neçə alternativi vutğuladıq.

`Display` xassəsi HTML elementinin _tipini_ dəyişməyə imkan verir. Default olaraq, paragraphın `<p>` (**block-level** elementdir) default `display` dəyəri `block` olavaq, anvaq **inline** olaraq render oluna bilər:

{% highlight css %}
p{ display: inline;}
{% endhighlight %}

### Niyə inline HTML elementindən istifadə etmirik, `<span>` kimi?

Çünki HTML elementini onun mənasına görə secirik, render olunmasına görə deyil. Əgər məzmunumuza ən uyğun olanın paragrapg olduğuna qərar vermişiksə, etiketi _yalnız styling məqsədləri üçün_ dəyişməməliyik. Styling üçün CSS var.

Qısacası, `display` bizə elementin **mənasını** dəyişmədən onun **tipini** dəyişməyə imkan verir.

Hər bir `display` seçməsinin spesifik rendering davranışı var:

* `block` mövcud bütün genişliyi alacaq
* `inline` düz mətn kimi çıxış edəcək
* `inline-block`, adından da göründüyü kimi, blok və inlline davranışın birləşməsidir, _"hər iki xassənin ən yaxşısını"_ seçir
* `list-item` `block` ilə oxşardır mövcud bütün genişliyi alır, lakin əlavə bir işarə nöqtəsi göstərir
* `table`, `table-row` və `table-cell` gözlənilməsədə, daha maraqlı tərtibatlara imkan verən çox spesifik davranışlara malikdir.

### display: block

Bu hər hansı elementi **block** elementə çevirir.

bu texnika tez-tez **links**-də onların kliklənən zonasını artırmaq üçün istifadə olunur, background color təyin etməklə asanlıqla qiymətləndirilə bilər.

{% highlight css %}
.menu a{ background: red; color: white;}
{% endhighlight %}

{% highlight html %}
<ul class="menu">
  <li>
    <a>Home</a>
  </li>
  <li>
    <a>Features</a>
  </li>
  <li>
    <a>Pricing</a>
  </li>
  <li>
    <a>About</a>
  </li>
</ul>
{% endhighlight %}

<div class="result">
  <ul>
    <li>
      <a style="background: red; color: white;">Home</a>
    </li>
    <li>
      <a style="background: red; color: white;">Features</a>
    </li>
    <li>
      <a style="background: red; color: white;">Pricing</a>
    </li>
    <li>
      <a style="background: red; color: white;">About</a>
    </li>
  </ul>
</div>

Əgər biz bu linkləri **block**lara çevirsək, onların kliklənmə ərazisini artirmiş oluruq:

{% highlight css %}
.menu a{ background: red; color: white; display: block;}
{% endhighlight %}

<div class="result">
  <ul>
    <li>
      <a style="background: red; color: white; display: block;">Home</a>
    </li>
    <li>
      <a style="background: red; color: white; display: block;">Features</a>
    </li>
    <li>
      <a style="background: red; color: white; display: block;">Pricing</a>
    </li>
    <li>
      <a style="background: red; color: white; display: block;">About</a>
    </li>
  </ul>
</div>


### display: inline

Bu hər hansı elementi **inline** elementə çevirir, sanki sadə **mətn** kimi.

Üfüqi naviqasiya panelləri düzəltmək üçün tez-tez istifadə olunur, burada **list items** semantikdir, lakin vizual olaraq faydalı deyil.

{% highlight html %}
<ul class="menu">
  <li>
    <a>Home</a>
  </li>
  <li>
    <a>Features</a>
  </li>
  <li>
    <a>Pricing</a>
  </li>
  <li>
    <a>About</a>
  </li>
</ul>
{% endhighlight %}

<div class="result">
  <ul>
    <li>
      <a>Home</a>
    </li>
    <li>
      <a>Features</a>
    </li>
    <li>
      <a>Pricing</a>
    </li>
    <li>
      <a>About</a>
    </li>
  </ul>
</div>

{% highlight css %}
.menu li{ display: inline;}
{% endhighlight %}

<div class="result">
  <ul>
    <li style="display: inline;">
      <a>Home</a>
    </li>
    <li style="display: inline;">
      <a>Features</a>
    </li>
    <li style="display: inline;">
      <a>Pricing</a>
    </li>
    <li style="display: inline;">
      <a>About</a>
    </li>
  </ul>
</div>

### display: list-item

`list items` kimi göstərilən yeganə HTML elementləri (təəccüblü deyil) **list items**dır `<li>` həmçinin **definition descriptions** `<dd>`.

list item işarə nöqtəsi ilə göstərilir (əgər unordered list `<ul>` dirsə) və ya artan sıra ilə (əgər ordered list `<ol>` dirsə).

Çünki bu işarə nöqtələrinin və nömrələrin göstərilməsi brauzerə görə dəyişir, və həmçinin CSS də style etmək çəytindir, `display: list-item` qaydası heç vaxt istifadə olunmur. Əslində, `<li>`lərin `display: blok` və ya `display: inline` kimi göstərilməsi adi haldır, çünki onlar style etməyə daha çevikdirlər.

### display: none

HTML elementinə `display: none;` versəniz onu səhifədən silmiş olacaqsınız, kodunuzda heç vaxt olmamış kimi olacaq.

{% highlight css %}
.gone-baby-gone{ display: none;}
{% endhighlight %}

{% highlight html %}
<p>Did I hear someone speaking??</p>
<p class="gone-baby-gone">Hahahahahah</p>
<p>I must be dreaming...</p>
{% endhighlight %}

<div class="result">
  <p>Did I hear someone speaking??</p>
  <p style="display: none;">Hahahahahah</p>
  <p>I must be dreaming...</p>
</div>

Gördüyünüz kimi kodda üç ədəd paraqraf var, ancaq ikisi görünür, ikincisi heç zaman var olmayıbmış kimi.

### visibility: hidden

`visibility` CSS xassəsi  `display` xassəsinə azca oxşardır. Elementə `visibility: hidden;` tətbiq etdikdə elementi səhifədə _gizlədir_ , ancaq sadəcə **invisible**a çevrilir: lazım olan yeri yenədə tutur.

{% highlight css %}
.hollow-man{ visibility: hidden;}
{% endhighlight %}

{% highlight html %}
<p>So far away from me </p>
<p class="hollow-man">So far i just can't see</p>
<p class="hollow-man">So far away from me</p>
<p class="hollow-man">You're so far away from me</p>
<p>You're so far away...</p>
{% endhighlight %}

<div class="result">
  <p>So far away from me </p>
  <p style="visibility: hidden;">So far i just can't see</p>
  <p style="visibility: hidden;">So far away from me</p>
  <p style="visibility: hidden;">You're so far away from me</p>
  <p>You're so far away...</p>
</div>

Gördüyünüz kimi kodda beş ədəd paraqraf var, ancaq ikisi görünür, lakin gizli paraqrafların tutmalı olduğu yer hələ də qalır, ancaq onları görə bilmirsiniz
