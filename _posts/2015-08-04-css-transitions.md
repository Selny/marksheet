---
layout: post
title: "CSS <strong>transitions</strong>"
subtitle: "From one rule to another"
section: css
---

CSS <strong>transitions</strong> bir elementin vəziyyətindən digərinə rahat şəkildə keçməyə imkan verir.Necə işləyir ki, fərdi **xassələr** **ilkin** vəziyyətindən **son** vəziyyətinə qədər canlandırılır.

You can define:

* `transition-property`: hansı **xassə** animasiya ediləcək
* `transition-duration`: animasiya **nə qədər** davam edəcək
* `transition-timing-function`: **aralıq vəziyyətlər** necə hesablanır
* `transition-delay`: müəyyən vaxtdan **sonra** animasiyaya başlaması üçün

Siz hər bir CSS xassəsini ayrıca təyin edə və ya stenoqrafiya versiyasından istifadə edə bilərsiniz: `transition`. Bu halda, yalnız **müddət məcburidir**.

Unutmayın ki, **transition xüsusi bir _animasiya növüdür, burada yalnız başlanğıc və son vəziyyət var**.

### Quick example

Transitionlar **hover hallarında** tez-tez istifadə olunur.

{% highlight css %}
a{ background: lightgrey; color: grey;}
a:hover{ background: yellow; color: red;}
a.with-transition{ transition: 1s;}
{% endhighlight %}

<div class="result" id="result-841">
  <a>Without transition</a>
  <a class="with-transition">With transition</a>
</div>

Hover CSS qaydalarının **ani** olması əvəzinə, həm background, həm də mətn rəngləri yavaş-yavaş canlandırılır.

### transition-duration

Transition's duration keçid yaratmaq üçün lazım olan yeganə CSS xüsusiyyətidir. O, ya **saniyə** `2s` və ya **millisaniyə** `100ms` ilə təyin oluna bilər.

Transition **yarım saniyə** davam etməsini istəyirsinizsə, ya `0,5s` və ya `500ms` yaza bilərsiniz. Transitions nə qədər sürətli olmasını istədiyinizdən asılı olaraq, bir vahidin yazılması daha asan və/yaxud daha sürətli ola bilər.

{% highlight css %}
a{ background: lightgrey; color: grey;}
a:hover{ background: yellow; color: green;}
a.with-fast-transition{ transition-duration: 0.5s;}
a.with-slow-transition{ transition: 3s;}
{% endhighlight %}

<div class="result" id="result-842">
  <a>Without transition</a>
  <a class="with-fast-transition">A 0.5s transition</a>
  <a class="with-slow-transition">A 3s transition</a>
</div>

### transition-property

CSS xassələrinin yalnız **1/3**-i animasiya edilə bilər.Mozilla-da [tam siyahı](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties) var.

Default olaraq, `transition-property` xassəsinin `all` dəyəri vardır, bu o deməkdir ki, o, bütün mümkün xassələri animasiya ediləcək.

Siz yalnız 1 və ya bir neçə xassəni animasiya etmək qərarına gələ bilərsiniz.

{% highlight css %}
a{ background: lightgrey; color: grey;}
a:hover{ background: yellow; border: 5px solid blue; color: green;}
a.with-background-transition{ transition-duration: 2s; transition-property: background;}
a.with-all-transition{ transition-duration: 2s;}
{% endhighlight %}

<div class="result" id="result-843">
  <a>Without transition</a>
  <a class="with-background-transition">With only background transition</a>
  <a class="with-all-transition">With all transitions</a>
</div>

The `border` xassəsi tam olaraq animasiya ediləndir və keçidi asanlıqla yavaş (2 saniyə) görüntüləməyə imkan verir.

### transition-timing-function

Timing funksiyası hər bir xassənin ** dəyərinin ** keçid zamanı** necə hesablandığını müəyyən edir.

Default olaraq, transition **eased**-dir: başlanğıcda sürətlənir və sonunda yavaşlayır.

Siz keçidin **sabit sürətlə** baş verəcəyinə əmin ola bilərsiniz. Zamanlama funksiyaları keçidi **sürətləndirə** və/və ya **yavaşlatdıra bilər**.

Timing funksiyalarını vizuallaşdırmağın ən asan yolu, `left` kimi **position xüsusiyyətlərini** dəyişdirməkdir.

{% highlight css %}
div{ left: 0; position: relative; transition: 1s;}
main:hover div{ left: 200px;}
.ease{ transition-timing-function: ease;} /* Default behavior */
.linear{ transition-timing-function: linear;} /* Constant speed */
.ease-in{ transition-timing-function: ease-in;}
.ease-out{ transition-timing-function: ease-out;}
.ease-in-out{ transition-timing-function: ease-out;}
{% endhighlight %}

{% highlight html %}
<main>
  <p><strong>Ease</strong>: slow start, fast middle, slow end</p>
  <div class="ease"></div>
  <p><strong>Linear</strong>: constant speed</p>
  <div class="linear"></div>
  <p><strong>Ease In</strong>: slow start, fast end</p>
  <div class="ease-in"></div>
  <p><strong>Ease Out</strong>: fast start, slow end</p>
  <div class="ease-out"></div>
  <p><strong>Ease In Out</strong>: like ease, but with more pronounced acceleration/deceleration curves</p>
  <div class="ease-in-out"></div>
</main>
{% endhighlight %}

<div class="result" id="result-844">
  <p><strong>Ease</strong>: slow start, fast middle, slow end</p>
  <div class="ease"></div>
  <p><strong>Linear</strong>: constant speed</p>
  <div class="linear"></div>
  <p><strong>Ease In</strong>: slow start, fast end</p>
  <div class="ease-in"></div>
  <p><strong>Ease Out</strong>: fast start, slow end</p>
  <div class="ease-out"></div>
  <p><strong>Ease In Out</strong>: like ease, but with more pronounced acceleration/deceleration curves</p>
  <div class="ease-in-out"></div>
</div>

Unutmayın ki, bütün keçidlər **eyni vaxt** alır (1 saniyə).

Digər vaxt funksiyalarının necə işlədiyini vizuallaşdırmaq istəyirsinizsə, bunu yoxlayın [Easing Functions Cheat Sheet](https://easings.net/).

#### cubic-bezier

Bütün bu **əvvəlcədən təyin edilmiş** vaxt funksiyaları sizə uyğun gəlmirsə, **cubic bezier** funksiyalarından istifadə edərək özünüz yaza bilərsiniz.

[cubic-bezier.com](https://cubic-bezier.com/) veb saytı öz əyrilərinizi vizual olaraq yazmaq üçün çox rahat tooldur.

### transition-delay

**delay** keçidlərin faktiki olaraq başlamazdan əvvəl **gözləyərək** nə qədər müddətə ehtiyac olduğunu müəyyən edəcək.

`transition-duration` kimi, saniyə `s` və ya millisaniyə `ms` istifadə edə bilərsiniz.

{% highlight css %}
a{ background: blue; color: white; transition: all 1s;}
div:hover a{ background: red;}
a.with-delay{ transition-delay: 1s;}
{% endhighlight %}

{% highlight html %}
<div>
  <p>Hover the grey area</p>
  <a>Without any delay</a>
  <a class="with-delay">With a second delay</a>
</div>
{% endhighlight %}

<div class="result" id="result-845">
  <div>
    <p>Hover the grey area</p>
    <a>Without any delay</a>
    <a class="with-delay">With a second delay</a>
  </div>
</div>

<style type="text/css">
#result-841{ padding: 1rem;}
#result-841 a{ background: lightgrey; color: grey; margin-right: 10px; padding: 5px 10px; transition: none;}
#result-841 a:hover{ background: yellow; color: red;}
#result-841 .with-transition{ transition: 1s}
#result-842{ padding: 1rem;}
#result-842 a{ background: lightgrey; color: grey; margin-right: 10px; padding: 5px 10px; transition: none;}
#result-842 a:hover{ background: yellow; color: green;}
#result-842 .with-fast-transition{ transition: 0.5s;}
#result-842 .with-slow-transition{ transition: 3s;}
#result-843{ padding: 1rem;}
#result-843 a{ background: lightgrey; color: grey; margin-right: 10px; padding: 5px 10px; transition: none;}
#result-843 a:hover{ background: yellow; border: 5px solid blue; color: green;}
#result-843 .with-background-transition{ transition: 2s; transition-property: background;}
#result-843 .with-all-transition{ transition: 2s;}
#result-844{ padding-bottom: 1rem;}
#result-844 div{ background: crimson; height: 20px; left: 0; margin-top: -1rem; position: relative; transition: 1s; width: 20px;}
#result-844:hover div{ left: 200px;}
#result-844 p{ color: grey;}
#result-844 p strong{ font-weight: bold;}
#result-844 .ease{ transition-timing-function: ease;} /* Default behavior */
#result-844 .linear{ transition-timing-function: linear;} /* Constant speed */
#result-844 .ease-in{ transition-timing-function: ease-in;}
#result-844 .ease-out{ transition-timing-function: ease-out;}
#result-844 .ease-in-out{ transition-timing-function: ease-in-out;}
#result-844 p:nth-child(1) strong{ color: crimson;}
#result-844 div:nth-child(2){ background: crimson;}
#result-844 p:nth-child(3) strong{ color: midnightblue;}
#result-844 div:nth-child(4){ background: midnightblue;}
#result-844 p:nth-child(5) strong{ color: mediumseagreen;}
#result-844 div:nth-child(6){ background: mediumseagreen;}
#result-844 p:nth-child(7) strong{ color: orangered;}
#result-844 div:nth-child(8){ background: orangered;}
#result-844 p:nth-child(9) strong{ color: darkviolet;}
#result-844 div:nth-child(10){ background: darkviolet;}
#result-845{ padding: 1rem;}
#result-845 div{ background: lightgrey; padding: 1rem; width: 400px;}
#result-845 div p{ color: grey; margin-top: 0;}
#result-845 a{ background: blue; color: white; padding: 5px 10px; text-decoration: none; transition: all 1s;}
#result-845 div:hover a{ background: red;}
#result-845 a.with-delay{ transition-delay: 1s;}
</style>
