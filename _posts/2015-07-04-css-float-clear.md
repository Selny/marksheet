---
layout: post
title: "CSS <strong>float</strong>"
subtitle: "The most unpredictable property"
section: css
---

“Üzmək” sözünün arxasında sonsuz imkanlar dənizi var(və pis davranışlar).

Yəqin ki, `float` CSS-də ən cətin alyaşdır. Onun davranışları maraqlı, gözlənilməz və sehrli ola bilər. Yəqin ki, bütün _positioning_ xassələri içərisində onun **mühitinə** ən çox _təsir edən_ xassədir.

Başqa bir sözdə desək, float tətbiqi təkcə onun tətbiq olunduğu elementi dəyişdirmir, həm də onun  ancestors, siblings, descendants və sonrakı elementlərini də dəyişir**.

`float` aşağıdakı 3 dəyərə sahib ola bilər:

* `left` və `right` elementi **floating** elementə çevirir
* `none` float aspektlərini silir

### When to use float

Elementin **floating** edilməsinin məqsədi **onu bir tərəfə itələmək** **ətrafını** mətn ilə sarımaqdır.

Budavranışı izah etmək məqsədilə, adi bir nümunə göstərək: şəkli mətnin daxilində floating edək.

{% highlight html %}
<p>
  <img src="https://placehold.it/150x150">
  The bells of the neighbouring church made a jangling tumult, a cart carelessly driven smashed, amid shrieks and curses, against the water trough up the street.  Sickly yellow lights went to and fro in the houses, and some of the passing cabs flaunted unextinguished lamps. And overhead the dawn was growing brighter, clear and steady and calm.
</p>
{% endhighlight %}

<div class="result">
  <p style="background: gold; padding: 10px; width: 600px;">
    <img src="https://placehold.it/150x150">
    It was while the curate had sat and talked so wildly to me under the hedge in the flat meadows near Halliford, and while my brother was watching the fugitives stream over Westminster Bridge, that the Martians had resumed the offensive. So far as one can ascertain from the conflicting accounts that have been put forth, the majority of them remained busied with preparations in the Horsell pit until nine that night, hurrying on some operation that disengaged huge volumes of green smoke.
  </p>
</div>

Mətnin içərisinə şəkli daxil edərkən olan problem odur ki, **bir şəkil mətnin bir sətrinə uyğun olmalıdır**, və buna görə də onun üzərində olduğu sətrin hündürlüyünü _artıracaq_. Bu halda bizim şəklimizin 150px hündürlüyü var.

Biz şəklin ətrafını mətn ilə sarımaq istəyirik:

{% highlight css %}
img{ float: left;}
{% endhighlight %}

<div class="result">
  <p style="background: gold; padding: 10px; width: 600px;">
    <img style="float: left;" src="https://placehold.it/150x150">
    It was while the curate had sat and talked so wildly to me under the hedge in the flat meadows near Halliford, and while my brother was watching the fugitives stream over Westminster Bridge, that the Martians had resumed the offensive. So far as one can ascertain from the conflicting accounts that have been put forth, the majority of them remained busied with preparations in the Horsell pit until nine that night, hurrying on some operation that disengaged huge volumes of green smoke.
  </p>
</div>

Gördüyünüz kimi şəkil **sola qoyulmuşdur**, və vətn şəklin ətrafından axır:

* əvvəlcə mətn sağa, _şəklin yanında_ yerləşdirilir
* sonra, şəklin _aşağıdasında_ boş yer olduqda, mətn həmin boşluğu dolduracaq

#### Əgər mətn yetərincə uzun deyildə nə olacaq?

<div class="result">
  <p style="background: gold; padding: 10px; width: 600px;">
    <img style="float: left;" src="https://placehold.it/150x150">
    He heard footsteps running to and fro in the rooms, and up and down stairs behind him
  </p>
</div>

floating olunan şəkil **daşacaq** çünki sarı konteynerdən daha boyükdür. Və _əslində_ gördüyünüz kimi, o, hətta **oxuduğunuz bu paraqrafı** vizual olaraq pozur.

_niyə_ float-ların gözlənilməz olduğunu göstərmək üçün qəsdən bu layout xətasını tərk etdim: hətta parentinin siblinglərini belə poza bilər!

Çünki `float: left` şəkli axından çıxarır, sarı abzasın hündürlüyü yalnız **mətnin hündürlüyünə** bərabərdir. Başqa bir deyişlə, şəklin hündürlüyü nəzərə alınmır.

### Float = block

Floating elementlərində avtomatik olaraq `display: block` təyin edilmiş olacaq, və əsasən blok-level kimi çıxış edəcəklər:

* spesifik height və width təyin edə bilərsiniz
* əgər height təyin edilməyibsə, elementin heighti line-height qədər olacaq
* Əgər `width: 100%` tətbiq edilibsə, blok-level elementə oxşar olacaq

### float-ı təmizləmək

`clear` xassəsi **floatdan _sonraya_ element qoymağa imkan verir**. Bu ancaq **blok** elementlərə tətbiq oluna bilər.

{% highlight html %}
<p>
  <img src="https://placehold.it/150x150">
  <span>He heard footsteps running to and fro in the rooms, and up and down stairs behind him</span>
</p>
{% endhighlight %}

{% highlight css %}
img{ float: left;}
span{ clear: left; display: block;}
{% endhighlight %}

<div class="result">
  <p style="background: gold; padding: 10px; width: 600px;">
    <img style="float: left;" src="https://placehold.it/150x150">
    <span style="clear: left; display: block;">He heard footsteps running to and fro in the rooms, and up and down stairs behind him</span>
  </p>
</div>

Şəkildən _sonraya_ mətn qoymaq yerinə, `clear: left` mətni şəklin **aşağısına** qoyur.

Bu, heç bir float və ya clear olmaması fərqlidir, çünki şəkil öz aıtrindədir və mətnlə eyni sətirdə _deyil.

