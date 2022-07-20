---
layout: post
title: "CSS <strong>pseudo-classes</strong>"
subtitle: "Enhancing the CSS <strong>selectors</strong>"
section: css
---

Əsasən [3 növ CSS selektorunun](/css-selectors.html) necə olduğunu gördük:

* **generic** burada CSS-dəki `p` selektoru `<p>` HTML elementlərini hədəfləyir
* **classes** burada CSS-də `.intro` selektoru `class="intro"` atributlu HTML elementlərini hədəfləyir
* **ids** burada CSS-də `#loqo` selektoru `id="logo"` atributlu HTML elementlərini hədəfləyir

Bu selectorlarına hamısına **pseudo-classes** əlavə oluna bilər. pseudo-classlar:

* elementin xüsusi **vəziyyətini** müəyyən edir
* **colon** `:` ilə başlayan açar sözdür

### Syntax

pseudo-class **özlüyündə mövcud ola bilməz**. **selektora əlavə edilməlidir**. pseudo-class yalnız həmin selektorun xüsusi _statusunu_ təyin edəcək.

Sintaksisi aşağıdakına bənzəyir:

{% highlight css %}
.selector:pseudo-class{ }
{% endhighlight %}

Onların **bir-birinə bağlı olduğunu göstərmək üçün**, selektor və pseudo-class arasında **boşluq** olmur.

### :hover

Məsələn, ümumi istifadə olunan pseudo-classlardan biri `:hover`-dir, hədəf elementə **hovered** CSS style-i əlavə etməyə imkan verir. Gəlin bunu **linklər**-də sınayaq.

{% highlight css %}
a{ color: blue;}
a:hover{ color: red;}
{% endhighlight %}

<div class="result" id="result-821">
  <p>Hover <a>this link</a> and see how it turns red.</p>
</div>

Birinci sətir bütün `<a>` HTML elementlərinin necə görünəcəyini müəyyən edir (mavi).
İkinci sətir `<a>`-nin **hover edildikdə** necə görünəcəyini müəyyən edir (qırmızı).

İkinci sətir **eyni HTML elementlərini** hədəfləyir, lakin _yalnız_ konkret bir şey baş verdikdə (bu halda, hover edilir).

### :visited

Bu pseudo-class **ziyarət edilmiş linkləri** hədəfləyir. Defolt olaraq, linklər **mavi** olur və onlara baş çəkdiyiniz zaman **bənövşəyi** olur. Google nəticələri belə işləyir.

{% highlight css %}
a{ color: dodgerblue;}
a:visited{ color: rebeccapurple;}
{% endhighlight %}

{% highlight html %}
<a href="https://www.google.com">Google</a>
<a href="https://twitter.com">Twitter</a>
<a href="https://www.facebook.com">Facebook</a>
<a href="https://www.mozilla.org">Mozilla</a>
<a href="https://marksheet.io/visited.html">MarkSheet</a>
{% endhighlight %}

<div class="result" id="result-8211">
  <a href="https://www.google.com">Google</a>
  <a href="https://twitter.com">Twitter</a>
  <a href="https://www.facebook.com">Facebook</a>
  <a href="https://www.mozilla.org">Mozilla</a>
  <a href="/html/visited.html">MarkSheet</a>
</div>

Ziyarət edilən bağlantılar üçün fərqli dizayn tətbiq etmək çox vaxt diqqətdən kənarda qalır, lakin nəticələrin siyahısına baxan istifadəçilər üçün faydalı olur. Bu, onlara artıq olduqları yeri asanlıqla təsəvvür etməyə kömək edir.

### :focus

Bu pseudo-class HTML elementi **fokusda** olduqda baş verir. Bu xüsusilə HTML **inputlar** üçün faydalıdır.

{% highlight css %}
.form-input{ border: 2px solid grey; padding: 5px;}
.form-input:focus{ background: lightyellow; border-color: blue; outline: none;}
{% endhighlight %}

<div class="result" id="result-822">
  <input class="form-input" placeholder="First name">
</div>

`outline: none;` qaydası inputdan parıltını aradan qaldırır.
{: .info}

### :first-child və :last-child

Bu pseudo-classlar **[HTML iyerarxiyası](/html-hierarchy.html) ilə bağlıdır.** Onlar kodda göründükləri **sifarişdən** asılı olaraq HTML elementlərini hədəfləyirlər.

{% highlight html %}
<ul>
  <li>One</li>
  <li>Two</li>
  <li>Three</li>
  <li>Four</li>
</ul>
{% endhighlight %}

{% highlight css %}
li:first-child{ background: greenyellow;}
li:last-child{ background: lightsalmon;}
{% endhighlight %}

<div class="result" id="result-823">
  <ul>
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
    <li>Four</li>
  </ul>
</div>

Gördüyünüz kimi, birinci və sonuncu `<li>`-ə **heç bir CSS classı** tətbiq edilmir. Onların **iyeraxiyadakı mövqeyi** CSS qaydasının tətbiq edilib-edilmədiyini müəyyən edir.

Əgər biz 5-ci siyahı elementini əlavə etsəydik və eyni CSS-dən istifadə etsəydik, styl avtomatik olaraq dəyişəcəkdi:

<div class="result" id="result-824">
  <ul>
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
    <li>Four</li>
    <li>Five</li>
  </ul>
</div>

### :nth-child

Bu pseudo-class `:first-child` və `:son-child`-in daha **qlobal** versiyasıdır. `:nth-child` ilə siz hansı child elementi hədəfləmək istədiyinizi **təyin edə bilərsiniz**.

Məsələn, **ikinci** childı hədəfləmək istəyirsinizsə, `:nth-child(2)` istifadə edirsiniz:

{% highlight css %}
li:nth-child(2){ background: violet;}
{% endhighlight %}

<div class="result" id="result-825">
  <ul>
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
    <li>Four</li>
  </ul>
</div>

#### odd and even

Rəqəmdən istifadə sadə olsa da, `:nth-child` 2 açar sözlə gəlir:

* `:nth-child(odd)` tək elementləri hədəfləyir
* `:nth-child(even)` cüt elementləri hədəfləyir

{% highlight css %}
li:nth-child(odd){ background: gold;}
{% endhighlight %}

<div class="result" id="result-826">
  <ul>
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
    <li>Four</li>
  </ul>
</div>

#### The n iterator/(n iteratoru)

`:nth-child`-in ən güclü cəhəti `n` açar sözündən istifadə edərək **hesablamalara** əsaslanan elementləri hədəfə ala bilməsidir.

'n' dəyəri **sıfır** '0'dan mövcud child elementlərin **sayına** qədər artır.

Hər **üçüncü** elementi hədəfləmək istəsəniz nə olacaq?

{% highlight css %}
li:nth-child(3n){ background: hotpink;}
{% endhighlight %}

<div class="result" id="result-827">
  <ul>
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
    <li>Four</li>
    <li>Five</li>
    <li>Six</li>
    <li>Seven</li>
  </ul>
</div>

Bu vəziyyətdə `n` **sıfır**-dan başlayır və **altı**-da bitir.

Kompüterlər saymağa **sıfır**dan başlayır. Siyahımızda yeddi element olduğu üçün biz altıya qədər yüksələcəyik, çünki 0-1-2-3-4-5-6 **yeddi** elementi təmsil edir.
{: .info}

Siz `:nth-child(3n)` _"Mövqeyi 3-ə bölünən hər bir elementi hədəf almaq"_ kimi nəzərə ala bilərsiniz. Bu vəziyyətdə, o, həm 3-cü, həm də 6-cı list itemları hədəf alır:

* `3 x 0` sıfır
* `3 x 1` üçüncü elementdir
* `3 x 2` altıncı elementdir

#### n + 1

1-ci elementi və ondan sonra hər üç elementdən bir hədəfləmək istəsəniz nə olacaq?

{% highlight css %}
li:nth-child(3n+1){ background: limegreen;}
{% endhighlight %}

<div class="result" id="result-828">
  <ul>
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
    <li>Four</li>
    <li>Five</li>
    <li>Six</li>
    <li>Seven</li>
  </ul>
</div>

`3n+1`-in üç hissəsi var:

* `3n` hər **3-cü** elementi seçir
* `+1` ** başlanğıcı 1 ilə əvəz edir**

Hesablamalar belə aparılır:

* `3 x 0 + 1` **1**
* `3 x 1 + 1` **4**
* `3 x 2 + 1` **7**

`n` iteratoru çox yönlüdür. Düzgün hesablama tapmaq çətindir, ona görə də düzgün seçimi tapmaq üçün sadəcə onu sınaqdan keçirin.

### Başqa pseudo-classlar

[onlarla pseudo-classes mövcuddur]https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes), bəziləri çox konkret hallar üçündür. Ən çox istifadə olunanları əhatə etdik.

<style type="text/css">
#result-821 a{ color: blue;}
#result-821 a:hover{ color: red;}
#result-8211 a{ color: dodgerblue;}
#result-8211 a:visited{ color: rebeccapurple;}
#result-822{ padding: 1rem;}
#result-822 input{ border: 2px solid lightgrey; padding: 5px;}
#result-822 input:focus{ background: lightyellow; border-color: blue; outline: none;}
#result-823 li:first-child{ background: greenyellow;}
#result-823 li:last-child{ background: lightsalmon;}
#result-824 li:first-child{ background: greenyellow;}
#result-824 li:last-child{ background: lightsalmon;}
#result-825 li:nth-child(2){ background: violet;}
#result-826 li:nth-child(odd){ background: gold;}
#result-827 li:nth-child(3n){ background: hotpink;}
#result-828 li:nth-child(3n+1){ background: limegreen;}
</style>

