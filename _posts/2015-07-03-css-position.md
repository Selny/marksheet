---
layout: post
title: "CSS <strong>position</strong>"
subtitle: "Going manual"
section: css
---

CSS `position` xassəsi çox yönlü və güclüdür. It allows to _set_ or _alter_ an element's position. It has 4 possible **values**:

* `static` (default qiyməti)
* `relative`
* `absolute`
* `fixed`

4 **kotdinatlı** xassələrlə yanaşı tez-tez istifadə olunur:

* `left`
* `right`
* `top`
* `bottom`

### static

This is the **default** `position` value: static elements just follow the [natural flow](css-the-flow.html). They aren't affected by any `left`, `right`, `top` or `bottom` value.

### relative

`position` **relative** təyin edilən zaman, element  **indiki mövqeyinə** görə hərəkət edə bilər.

{% highlight html %}
<p>Well, Ja should know his own business, I thought, and so I grasped the spear and clambered up toward the red man as rapidly as I could - being so far removed from my simian ancestors as I am</p>
<p>I imagine the slow-witted sithic, as Ja called him, suddenly realized our intentions and that he was quite likely to lose all his meal instead of having it doubled as he had hoped</p>
<p>When he saw me clambering up that spear he let out a hiss that fairly shook the ground, and came charging after me at a terrific rate</p>
{% endhighlight %}

{% highlight css %}
p{ border: 1px solid blue;}
{% endhighlight %}

<div class="result">
  <p style="border: 1px solid blue;">Well, Ja should know his own business, I thought, and so I grasped the spear and clambered up toward the red man as rapidly as I could - being so far removed from my simian ancestors as I am</p>
  <p style="border: 1px solid blue;">I imagine the slow-witted sithic, as Ja called him, suddenly realized our intentions and that he was quite likely to lose all his meal instead of having it doubled as he had hoped</p>
  <p style="border: 1px solid blue;">When he saw me clambering up that spear he let out a hiss that fairly shook the ground, and came charging after me at a terrific rate</p>
</div>

Gəlin indi **ikinci** paraqrafı hərəkət etdirək:

{% highlight html %}
<p>Well, Ja should know his own business, I thought, and so I grasped the spear and clambered up toward the red man as rapidly as I could - being so far removed from my simian ancestors as I am</p>
<p class="second">I imagine the slow-witted sithic, as Ja called him, suddenly realized our intentions and that he was quite likely to lose all his meal instead of having it doubled as he had hoped</p>
<p>When he saw me clambering up that spear he let out a hiss that fairly shook the ground, and came charging after me at a terrific rate</p>
{% endhighlight %}

{% highlight css %}
.second{ position: relative; border-color: red; left: 20px; top: 10px;}
{% endhighlight %}

<div class="result">
  <p style="border: 1px solid blue;">Well, Ja should know his own business, I thought, and so I grasped the spear and clambered up toward the red man as rapidly as I could - being so far removed from my simian ancestors as I am</p>
  <p style="border: 1px solid red; position: relative; left: 20px; top: 10px;">I imagine the slow-witted sithic, as Ja called him, suddenly realized our intentions and that he was quite likely to lose all his meal instead of having it doubled as he had hoped</p>
  <p style="border: 1px solid blue;">When he saw me clambering up that spear he let out a hiss that fairly shook the ground, and came charging after me at a terrific rate</p>
</div>

Qırmızı paraqraf olması lazım olduğu _təbii_ vəziyyətinə nisbətən **soldan** 20px **yuxarıdan** 10px yerini dəyişmişdir.

Mavi paraqrafların ümumiyyətlə necə yerindən tərpənmədiyinə diqqət yetirin. relative positioning-dən istifadə edərək, qırmızı abzas layoutu pozmadan sərbəst hərəkət edə bilər. Yersiz olan tək şey özüdür. Digər bütün elementlər **həmin elementin hərəkət etdiyini bilmirlər**.

### absolute

`position` **absolute** təyin edildikdə, element **ilk yerləşdirilmiş ancestor** elementə uyğun olaraq hərəkət edə bilər.

#### "Positioned?? _positioned_ element nədir?"

**positioned** element `position` qiyməti ya `relative`, `absolute` ya da `fixed` olan elementdir.

_positioned_ elementin xarakteristikası ondan ibarətdir ki, o, **öz child elementləri üçün istinad nöqtəsi** kimi çıxış edə bilər..

Gəlin sadə bir **iyerarxiya** təsəvvür edək:

{% highlight html %}
<section>
  I'm in position relative.
  <p>
    I'm in position absolute!
  </p>
</section>
{% endhighlight %}

{% highlight css %}
section {
  background: gold;
  height: 200px;
  padding: 10px;
  position: relative; /* This turns the <section> into a point of reference for the <p> */
}

p {
  background: limegreen;
  color: white;
  padding: 10px;
  position: absolute; /* This makes the <p> freely movable */
  bottom: 10px; /* 10px from the bottom */
  left: 20px; /* 20px from the left */
}
{% endhighlight %}

<div class="result">
  <section style="background: gold; height: 200px; margin: 1em 0; padding: 10px; position: relative;">
    I'm in position relative.
    <p style="background: limegreen; bottom: 10px; color: white; left: 20px; margin: 0; padding: 10px; position: absolute;">
      I'm in position absolute!
    </p>
  </section>
</div>

Sarı bölmənin `200px` hündürlüyü var və positionı `relative` olaraq təyin edilmisdir, bu onu ** bütün child elementlərim üçün istinad nöqtəsinə** çevirir.

Yaşıl paraqrafın positionu `absolute` təyin edildiyi üçün , sarı hissəyə görə sərbəst hərəkət edə bilir. Həm `alt`, həm də `sol` dəyərləri təyin etməklə, o, aşağı sol küncdən hərəkət edəcək.

#### Əgər biz sol və sağı ikisinidə təyin etsək nə baş verəcək?

Əgər elementə `width` təyin edilməyibsə, `left: 0` və `right: 0` təyin etsək **element bütün en boyunca uzanacaq**. `left: 0` və `width: 100%` təyin etməyə bərabərdir.

Əgər `width` təyin edilibsə, o zaman `right` dəyəri nəzərə alınmır.

### fixed

`position` **fixed** təyin edildikdə, **absolute** kimi çəıxış edir: left/right və top/bottom koordinatlarını təyin edə bilərsiniz.

Yeganə fərq ondadır ki, **istinad nöqtəsi viewport-dir**. Bu o deməkdir ki, fixed element səhifə ilə birlikdə sürüşdürülməyəcək; ekranda _sabitdir_.
