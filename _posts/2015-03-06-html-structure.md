---
layout: post
title: "HTML <strong>Structure</strong>"
subtitle: "To <strong>organize</strong> the <strong>main</strong> parts of your webpage"
section: html
---

Paraqraf kimi hər hansı bir HTML məzmunu yazarkən, listlər və ya linklər, _mətninizə_ **məna** verirsiniz. Ancaq bu elementlərin bəzilərini _birlikdə_ quruplaşdırmaq istəyə bilərsiniz.

Məsələn, bloq veb səhifəsi **4** hissəyə bölünə bilər:

* **header** bu hər bir səhifədəki kimi oxşardır, və vebsaytın naviqası mənasına gəlir
* **main** məzmun, bu hər bir veb səhifəyə görə dəyişir: məqalələrin siyahısı, sadə məqalələr şərhlərlə birgə, haqqıda səhifəsi...
* **sidebar** aylıq arxivlərə və kateqoriyalara keçid verir
* a **footer** az əhəmiyyətli səhifələrə əlavə bağlantılar üçün

Bəzi **struktur HTML elementləri** var ki, digər elementlər üçün **konteyner** kimi istifadə edə bilərsiniz.

### Header/(başlıq)

`header` adətən kodda birinci HTLM elementidir. It acts as an **introduction** to the webpage,loqo ilə, a şüar, və naviqasiya linkləri.

{% highlight html %}
<header>
  <p>
    <a>
      <img src="my-logo.jpg" alt="Tibitaco logo">
    </a>
    <em>A cool website</em>
  </p>
  <ul>
    <li>
      <a href="home.html">Home</a>
      <a href="about.html">About</a>
      <a href="contact.html">Contact</a>
    </li>
  </ul>
</header>
{% endhighlight %}

### Footer/(altbilgi)

`header`-ın əksi kimidə fikirləşilə bilər, `footer` adətən səhifənin **son** elementidir, naviqasiya linkləri təkrar olunduqda və ya ikinci dəfə əlavə olunduqda burdan istifadə olunur.

{% highlight html %}
<footer>
  <p>MarkSheet.io | Copyright 2015</p>
  <ul>
    <li>
      <a href="home.html">Home</a>
    </li>
    <li>
      <a href="about.html">About</a>
    </li>
    <li>
      <a href="contact.html">Contact</a>
    </li>
  </ul>
  <ul>
    <li>
      <a href="privacy-policy.html">Privacy Policy</a>
    </li>
    <li>
      <a href="terms-of-use.html">Terms of use</a>
    </li>
  </ul>
</footer>
{% endhighlight %}

### Main/(əsas)

`main` elementi ehtiva edir, adından göründüyü kimi, **səhifənin çox önəmli məzmunları**, hansı ki, səhifənin məqsədini müəyyən edən.

Vebsaytın bütün səhifələri ümumi elementləri ehtiva edir (header kimi, naviqasiya, altbilgi...), `main` elementi **vahid** bir məzmuna fokuslanır.

məsələn, bu veb səhifənin `main` elementində yerləşən və hal hazırda oxumaqda olduğunuz bu məqalə, çünki onun məzmunu bütün veb səhifə boyu vahiddir.

### Aside

  `aside` elementi əsasən `main` elementi ilə eyni mənanı daşıyır və əsas məzmun ilə bağlı alavə məlumat ehtiva edir.

### Section/(bölmə)

`section` elementi qruplaşmaya imkan verir

Sectionlar özləri heç bir məna daşımır. Bu, ümumi səhifə daxilində öz mənasından daha çox onun uşaq elementləri arasındakı əlaqəyə aiddir.

[MarkSheet ana səhifəsi](https://marksheet.io) 3 section ekrana çıxarır:

* **heading** (logo, title, subtitle)
* **introduction** (_"Short"_, _"Simple"_, _"Free"_)
* **chapters** (_"Web"_, _"HTML"_, _"CSS"_)

onları hər biri ana səhifədə `main` elementinin içərisində yaşayırlar, lakin oxşar məzmunu qruplaşdırmaq və səhifənin strukturuna daha çox məna vermək üçün məntiqi olaraq bölünür.



