---
layout: post
title: "HTML <strong>Formatting</strong>"
subtitle: "When <strong>whitespace</strong> doesn't matter"
section: html
---

HTML-də **yazılmış** kodlar, və ekrana çıxan nəticələr arasıda fərqlər var.

Gördüyümüz kimi, HTML **teqləri** `<p>` kimi məsələn sadəcə brauzer tətəfindən _oxunur_ (hansı _növ_ məzmunun yazıldığını bilmək üçün), ancaq brauzer tərəfindən**ekrana çıxarılmır**.

Həmçinin biz HTML də **komment sərilərinin** necə yazıdığınıda görmüşük, insanların kodu oxumasına kömək etmək məqsədilə, Bu lommentlər olmadan da brauzer kodları ekrna çıxardır.

Brauzer tərəfindən **nəzərə alınmayan** basqa növ kodlarda bosluqlardır, hansı ki, bunlara daxildir:

* sətir-qırılmaları
* boş sətirlər
  * cədvəllər (və ya abzaslar)

### Sətir qırılmaları

Sətir qırılmalar və boş sətirlə (hansı ki, sətir-qırılmalarının ardıcıllığıdı) HTML-də brauzer tərəfindən nəzərə alınmır. Onlar **sadəcə**  bosluqlar kimi hesab olunur.

{% highlight html %}
<blockquote>
The original idea of the web was that it should be a collaborative


space


where you can communicate through sharing information.
</blockquote>
{% endhighlight %}

<div class="result">
  <blockquote>
  The original idea of the web was that it should be a collaborative space where you can communicate through sharing information.
  </blockquote>
</div>

Sətri qırılmağa məcbur etmlək üçün, `<br>` HTML elementindən istifadə eməyə ehtiyaciniz var:

{% highlight html %}
<p>At its best, life is completely<br>unpredictable.</p>
{% endhighlight %}

<div class="result">
  <p>At its best, life is completely<br>unpredictable.</p>
</div>

### Tabulations

**Tabulation** _Tab_ düyməsini basmaqla əldə edilmiş xüsusi xarakterdir. Adətən kursoru növbəti taba hərəkət etdirir, ancaq bəzən iki bosluğa çevirilir.

Hər halda, Adi bosluq kimi, Cədvəlləşdirmə **Görünməzdir**. Həmçinin brauzer tərəfindən nəzərə alınmır:

{% highlight html %}
<p>
  Let's push      this text
  with tabulations.
</p>
{% endhighlight %}

<div class="result">
  <p>
    Let's push      this text
    with tabulations.
  </p>
</div>

Sözlərdən əvvəl **boşluq** əlavə etmək istəsəniz bunun üçün CSS istifadə etməlisiniz, bu barədə növbəti fəsildə bu barədə bəhs edəcəyik.

HTML elementlərini  **bağlama istəsəniz**, ilk öncə onun alt lement lərini bir bir bağlamalısınız.
{: .info}

### Ağac formatı

HTML elementləri bir birinin içərisinə yerləşdirilə bilər, onların açıldığı **sifarişi** izləməlisiniz, çünki onların bağlanma sırasına təsir edəcək.

{% highlight html %}
<article><p>Bu kod <strong>sadə/bir</strong> sətirdə yazılmışdır.</p></article>
{% endhighlight %}

<div class="result">
  <article><p>Bu kod <strong>sadə/bir</strong> sətirdə yazılmışdır.</p></article>
</div>

HTML elementkərini açılma ardıcıllığını izləmək çətin görünə bilər, bu səbəbdən HTML kodlarını **ağac formatında** yazmaq məsləhətlidir:

{% highlight html %}
<article>
  <p>
    Bu HTML kodu
    <strong>çoxlu</strong>
    sətirdə yazılmışdır ancaq buna baxmayaraq
    <em>tək</em>
    tək sətirdə ekrana çıxacaqdır
  </p>
</article>
{% endhighlight %}

<div class="result">
  <article>
    <p>
      Bu HTML kodu
      <strong>çoxlu</strong>
      sətirdə yazılmışdır ancaq buna baxmayaraq
      <em>tək</em>
      tək sətirdə ekrana çıxacaqdır
    </p>
  </article>
</div>

Ağac formatı HTML kodunuzun **yuva səviyyələrini** _vizual_ olaraq təkrarlamağa imkan verir. Beləliklə kodu görmək rahratlaşır:

* `<article>` **əcdaddır**
* `<p>` elementi `<strong>` və `<em>` elementlərinin **valideyinidir**
* `<strong>` və `<em>` elementləri **qardaşlardır**

### Özünüz oxumaq ücün HTML kodu yazın

Cədvəlləşdirmə, boş sətirlər, ardıcıl boşluqlar, və sətir-qırılmaları, komputer tərəfindən rədd edilir ixtisar olunur, və hamsı **tək** halına çevrilir.

HTML sənədi insan tərəfindən həm oxunur həmdə yazılır, ancaq lomputer sadəcə _oxuyur_. Cədvəlləşdirməni nəzərə alaq, boşluq və sətir-qırılmaları komputerinizin oxumasına və sonra sizin web səhifənizi ekrana çıxarmasına mane olmur, öz sənədini sizin üçün daha oxunaqlı şəkildə format edə bilərsiniz.

HTML formatlama ilə bağlı xüsusi bir qayda yoxdur lakin gizli **konvensiyalar** var, xüsusən:

* **Cədvəlləşdirmə** istifadə etmək sizə **iç-içə** necə yerləsdiyini görməyə kömək edəcək.
* Blok elementlərini açılış və qapanış teqlərini onların **öz sətirlərində** yerləşdirin.
* İnline elementlərini bir sətirdə yazın (açılış və qapanış teqləri daxil olmaqla)
