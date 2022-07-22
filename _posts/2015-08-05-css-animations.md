---
layout: post
title: "CSS <strong>animations</strong>"
subtitle: "A set sequence of CSS rules"
section: css
---

Biz indicə gördük ki, CSS **transitionlar** _başlanğıc_ vəziyyətlə _son_ vəziyyət arasında CSS xassələrini **animasiya etmək üçün bir yoldur.

Beləliklə, CSS transitionlar _xüsusi_ növ animasiyalardır, burada:

* yalnız iki halı var: start və end
* animasiya dönmür
* aralıq vəziyyətlər yalnız timing funksiyası ilə idarə olunur

Yaxşı, əgər istəsən:

* **aralıq** vəziyyətlərə nəzarət etmək?
* animasiya **loop** etmək?
* _eyni_ elementdə müxtəlif animasiyalar?
* spesifik xassəni animasiya etmək yalnız **halfway** animasiya vasitəsilə?
* müxtəlif xassələr üçün **müxtəlif timing funksiyalarını** simulyasiya etmək?

CSS animasiyaları bütün bunlara və daha çoxuna imkan verir.

**CSS animasiyaları rejissor olduğunuz mini filmlərə bənzəyir, burada müxtəlif səhnələr (keyframes) üçün aktyorlarınıza (HTML elementləri) təlimatlar (CSS qaydaları) verir.**

### Animation xassələri

`transition` xassəsi kimi, bəzi başqa xassələr üçün `animation`-da **shorthand** xassədir:

* **name**: animasiyanın adı
* **duration**: transition nə qədər davam edəcək
* **timing-function**: aralıq vəziyyətlər necə hesablanır
* **delay**: müəyyən vaxtdan sonra animasiyaya başlamaq üçün
* **iteration-count**: animasiya neçə dəfə yerinə yetirilməlidir
* **direction**: animasiya tərsinə çevrilməlidir, ya yox
* **fill-mode**: animasiya başlamazdan əvvəl və bitdikdən sonra hansı üslublar tətbiq olunur

### Quick example

Yükləmə düyməsini canlandırmaq üçün siz **bouncing** animasiya yaza bilərsiniz:

{% highlight css %}
@keyframes bouncing{
  0%  { bottom: 0; box-shadow: 0 0 5px rgba(0,0,0,0.5);}
  100%{ bottom: 50px; box-shadow: 0 50px 50px rgba(0,0,0,0.1);}
}

.loading-button{ animation: bouncing 0.5s cubic-bezier(0.1,0.25,0.1,1) 0s infinite alternate both;}
{% endhighlight %}

<div class="result" id="result-1">
  <a>Loading</a>
</div>

Siz əvvəlcə **keyframesdan** istifadə edərək faktiki bouncing animasiyanı yazmalı və onu `bouncing` adlandırmalısınız._Sonra_ siz onu `.loading-button`-a tətbiq etməklə həmin animasiyadan istifadə edə bilərsiniz.

**shorthand** `animation` xassəsindən istifadə etdim, və bütün variantları ehtiva edir:

* **name**: bouncing _(keyframe adı ilə uyğunlaşır)_
* **duration**: 0.5s _(yarım saniyə)_
* **timing-function**: [cubic-bezier(0.1,0.25,0.1,1)](https://cubic-bezier.com/#.1,.25,.1,1)
* **delay**: 0s _(delay yoxdur)_
* **iteration-count**: infinite _(sonduz davam edir)_
* **direction**: alternate _(irəli-geri gedir)_
* **fill-mode**: both

### @keyframes

HTML elementlərinə animasiyalar tətbiq etməzdən əvvəl siz **keyframesdan istifadə edərək animasiyalar yazmalısınız**. Basically, keyframes are each **intermediate step** in an animation. They are defined using **percentages**:

* `0%` animasiyanın birinci addımıdır
* `50%` animasiyanın yarısına qədər olan addımdır
* `100%` son addımdır

müvafiq olaraq `0%` and `100%` yerinə `from` və `to` açar sözlərdən istifadə edə bilərsiniz.
{: .info}

İstədiyiniz qədər keyframes  təyin edə bilərsiniz, `33%`, `4%` həmçinin `29.86%` kimi. Praktikada yalnız bir neçəsini yazacaqsınız.

Hər bir açar kadr **CSS qaydasıdır**, o deməkdir ki, siz həmişəki kimi CSS xassələrini yaza bilərsiniz.

Animasiyanı müəyyən etmək üçün sadəcə olaraq `@keyframes` açar sözünü və onun **adını** yazın.:

{% highlight css %}
@keyframes around {
  0%  { left: 0; top: 0;}
  25% { left: 240px; top: 0;}
  50% { left: 240px; top: 140px;}
  75% { left: 0; top: 140px;}
  100%{ left: 0; top: 0;}
}
p{ animation: around 4s linear infinite;}
{% endhighlight %}

<div class="result" id="result-2">
  <p>Hello</p>
</div>

Başlanğıc `0%` və son `100%` **eyni CSS qaydalarına** malik olmağuna diqqət yetirin. Bu, animasiyanın mükəmməl şəkildə dönməsini təmin edir. Çünki iterasiya sayı “sonsuz” olaraq təyin edilmişdir, animasiya '0%'dən '100%'ə gedəcək, və daha sonraani və qeyri-müəyyən müddətə `0%`-ə qayıdın.

### animation-name

Animasiyanın **name**-i ən azı **iki dəfə** istifadə olunur:

*`@keyframes` istifadə edərək animasiya **yazarkən**
* 'animasiya-adı' xüsusiyyətindən istifadə edərək (və ya 'animasiya' stenoqramı ilə) animasiyadan **istifadə edildikdə**

{% highlight css %}
@keyframes whatever{
  /* ... */
}

.selector{ animation-name: whatever;}
{% endhighlight %}

CSS sinif adları kimi, animasiya adlarıda da yalnız daxil ola bilər:

* hərflər (a-z)
* rəqəmlər (0-9)
* altxətt (_)
* trelər (-)

Bir və ya iki tire ilə başlaya bilməz.

### animation-duration

[transition durations](/css-transitions.html#transition-duration) kimi, animasiya müddətləri **saniyələr** `1s` və ya **millisaniyələr** `200ms` ilə təyin edilə bilər.

{% highlight css %}
.selector{ animation-duration: 0.5s;}
{% endhighlight %}

Defaul dəyərri `0s`-dir, hansı ki, heç bir animasiya yoxdur.

### animation-timing-function

[transition timing functions](/css-transitions.html#transition-timing-function) kimi, animation timing funksiyaları `linear`, `ease-out` kimi **açar sözlərdən** istifadə edə bilər və ya xüsusi **cubic bezier** funksiyalarından istifadə etməklə müəyyən edilə bilər.

{% highlight css %}
.selector{ animation-timing-function: ease-in-out;}
{% endhighlight %}

Default olaraq `ease`-dir.

Çünki CSS animasiyaları keyframelərdən istifadə edir, siz **linear** timing funksiyasını təyin edə və çox _spesifik_ əsas keyframelərin _çoxunu_ müəyyən etməklə xüsusi cubic bezier əyrisini **imitasiya edə bilərsiniz**.Qabaqcıl animasiyalar yaratmaq üçün [Bounce.js](https://bouncejs.com/) saytına baxın.
{: .info}

### animation-delay

Eynilə [transition delays] kimi(/css-transitions.html#transition-delay), animation delay **seconds** `1s` ilə və ya **milliseconds** `200ms ilə təyin edilə bilər`.

Default dəyəri `0s`-dir, bu da heç bir delay-ın olmaması deməkdir.

Çoxlu animasiyaları **ardıcıllıqla** işə saldıqda faydalıdır.

{% highlight css %}
.a,.b,.c{ animation: bouncing 1s;}
.b{ animation-delay: 0.25s;}
.c{ animation-delay: 0.5s;}
{% endhighlight %}

### animation-iteration-count

Default olaraq, animationlar yalnız **bir dəfə** oynayır. 3 növ dəyər təyin edə bilərsiniz:

* **integers** `2` və ya `3` kimi (tam ədədlər)
* **non-integers** `0.5` kimi animasiyanın yalnız yarısını oynayacaq (qeyri-tam ədədlər)
* **keyword** `infinite` animasiyanı sonsuz təkrarlayacaq (açar sözləri)

{% highlight css %}
.selector{ animation-iteration-count: infinite;}
{% endhighlight %}

### animation-direction

Animasiyanın **istiqaməti** əsas keyframelərin oxunmasını _hansı ardıcıllıqla_ müəyyən edir.

* **normal**: `0%`-dan başlayır, `100%`-də bitir, yenidən `0%`-da başlayır
* **reverse**: `100%`-də başlayır, `0%`-də bitir, yenidən `100%`-də bitir
* **alternate**: `0%`-da başlayır, `100%`-ə kimi gedir, `0%`-a gedir
* **alternate-reverse**: `100%`-da başlayır, `0%`-a kimi gedir, `100%`-ə kimi gedir

Animasiyanın iterasiya sayı “infinite” olaraq təyin edilərsə, bunu vizuallaşdırmaq daha asandır.

<div class="result" id="result-3">
  <p><strong>Normal</strong>: 0% --> 100%</p>
  <div class="normal"><div></div></div>
  <p><strong>Reverse</strong>: 100% --> 0%</p>
  <div class="reverse"><div></div></div>
  <p><strong>Alternate</strong>: 0% <--> 100%</p>
  <div class="alternate"><div></div></div>
  <p><strong>Alternate reverse</strong>: 100% <--> 0%</p>
  <div class="alternate-reverse"><div></div></div>
</div>

### animation-fill-mode

Animasiyanın **fill mode**-u animasiya başlamazdan əvvəl və bitdikdən sonra baş verənləri müəyyən edir.

**keyframeləri** təyin edərkən siz animasiyanın müxtəlif mərhələlərində tətbiq olunacaq **CSS qaydaları** müəyyən edirsiniz.. İndi bu CSS qaydaları animasiya edilən elementlərdə artıq tətbiq olunanlarla _toqquşa bilər_.


Gəlin bir ədəd **button** təsəvvür edək:

* default **qırmızı**
* animasiyanın əvvəlində **blue**-ə çevriləcək
* animasiya bitdikdə **green** yaşıl olaraq bitəcək

<div class="table">
  <table>
    <tr>
      <th><code>animation-fill-mode</code></th>
      <th>Before the animation</th>
      <th>Start of the animation</th>
      <th>End of the animation</th>
      <th>After the animation</th>
    </tr>
    <tr>
      <td><code>none</code></td>
      <td><a class="fill-mode fill-mode-red">Default</a></td>
      <td><a class="fill-mode fill-mode-blue">Start</a></td>
      <td><a class="fill-mode fill-mode-green">End</a></td>
      <td><a class="fill-mode fill-mode-red">Default</a></td>
    </tr>
    <tr>
      <td><code>forwards</code></td>
      <td><a class="fill-mode fill-mode-red">Default</a></td>
      <td><a class="fill-mode fill-mode-blue">Start</a></td>
      <td><a class="fill-mode fill-mode-green">End</a></td>
      <td><a class="fill-mode fill-mode-green">End</a></td>
    </tr>
    <tr>
      <td><code>backwards</code></td>
      <td><a class="fill-mode fill-mode-blue">Start</a></td>
      <td><a class="fill-mode fill-mode-blue">Start</a></td>
      <td><a class="fill-mode fill-mode-green">End</a></td>
      <td><a class="fill-mode fill-mode-red">Default</a></td>
    </tr>
    <tr>
      <td><code>both</code></td>
      <td><a class="fill-mode fill-mode-blue">Start</a></td>
      <td><a class="fill-mode fill-mode-blue">Start</a></td>
      <td><a class="fill-mode fill-mode-green">End</a></td>
      <td><a class="fill-mode fill-mode-green">End</a></td>
    </tr>
  </table>
</div>

<div class="result" id="result-4">
  <p>
    <span><strong>1.</strong> Before the animation</span>
    <span><strong>2.</strong> During the animation</span>
    <span><strong>3.</strong> After the animation</span>
  </p>
  <p><strong>None</strong>: the animation styles do not affect the default style</p>
  <p>
    <span>Default red</span>
    <span>From blue to green</span>
    <span>Back to red again</span>
  </p>
  <div class="none"><div></div></div>
  <p><strong>Forwards</strong>: the last styles applied at the end of the animation are retained afterwards</p>
  <p>
    <span>Default red</span>
    <span>From blue to green</span>
    <span>Remains green</span>
  </p>
  <div class="forwards"><div></div></div>
  <p><strong>Backwards</strong>: the animation's styles will already be applied before the animation actually starts</p>
  <p>
    <span>Already blue</span>
    <span>From blue to green</span>
    <span>Back to red again</span>
  </p>
  <div class="backwards"><div></div></div>
  <p><strong>Both</strong>: the styles are applied before and after the animation plays</p>
  <p>
    <span>Already blue</span>
    <span>From blue to green</span>
    <span>Remains green</span>
  </p>
  <div class="both"><div></div></div>
</div>

<style type="text/css">
#result-1{ padding: 1rem;}
#result-1 a{ animation: bouncing 0.5s cubic-bezier(.1,.25,.1,1) 0s infinite alternate both; background: lightslategrey; border-radius: 2px; display: inline-block; color: white; cursor: pointer; font-size: 0.75rem; font-weight: 300; letter-spacing: 0.2em; padding: 1em 2em 1.1em; position: relative; text-decoration: none; text-transform: uppercase; vertical-align: top;}

@keyframes bouncing{
  0%  { bottom: 0; box-shadow: 0 0 5px rgba(0,0,0,0.5);}
  100%{ bottom: 50px; box-shadow: 0 50px 50px rgba(0,0,0,0.1);}
}

#result-2{ height: 300px; padding: 0; width: 300px;}
#result-2 p{ animation: around 4s linear 0s infinite; background: turquoise; color: white; height: 60px; line-height: 60px; margin: 0; position: absolute; text-align: center; width: 60px;}

@keyframes around {
  0%  { left: 0; top: 0;}
  25% { left: 240px; top: 0;}
  50% { left: 240px; top: 240px;}
  75% { left: 0; top: 240px;}
  100%{ left: 0; top: 0;}
}

#result-3{ padding-bottom: 1rem;}
#result-3 p{ color: grey;}
#result-3 p strong{ font-weight: bold;}
#result-3 div{ background: hsl(217,4%,96%); height: 20px; width: 220px;}
#result-3 div div{ animation: swipe 2s linear infinite; background: crimson; height: 20px; left: 0; margin-top: -1rem; position: relative; transition: 1s; width: 20px;}
#result-3 .normal div{ animation-direction: normal;}
#result-3 .reverse div{ animation-direction: reverse;}
#result-3 .alternate div{ animation-direction: alternate;}
#result-3 .alternate-reverse div{ animation-direction: alternate-reverse;}
#result-3 p:nth-child(1) strong{ color: crimson;}
#result-3 div:nth-child(2) div{ background: crimson;}
#result-3 p:nth-child(3) strong{ color: midnightblue;}
#result-3 div:nth-child(4) div{ background: midnightblue;}
#result-3 p:nth-child(5) strong{ color: mediumseagreen;}
#result-3 div:nth-child(6) div{ background: mediumseagreen;}
#result-3 p:nth-child(7) strong{ color: goldenrod;}
#result-3 div:nth-child(8) div{ background: goldenrod;}

@keyframes swipe {
  0%  { left: 0;}
  100%{ left: 200px;}
}

#result-4{ padding: 1rem 1rem 0;}
#result-4 p{ color: grey; margin: 0; position: relative;}
#result-4 p:first-child{ margin-bottom: 1rem;}
#result-4 p span{ animation: toggle 6s infinite both; left: 0; position: absolute;}
#result-4 p:first-child span{ animation-name: tabs; margin-right: 1rem; position: static;}
#result-4 p span:nth-child(1){ animation-delay: 0; position: static;}
#result-4 p span:nth-child(2){ animation-delay: 2s;}
#result-4 p span:nth-child(3){ animation-delay: 4s;}
#result-4 div{ background: hsl(217,4%,96%); height: 20px; margin-bottom: 1rem; width: 220px;}
#result-4 div div{ animation: race-none 6s linear infinite; background: crimson; height: 20px; margin-bottom: 0; position: relative; width: 20px;}
#result-4 div:nth-child(7) div{ animation-name: race-forwards;}
#result-4 div:nth-child(10) div{ animation-name: race-backwards;}
#result-4 div:nth-child(13) div{ animation-name: race-both;}

a.fill-mode,
a.fill-mode:hover{ background: crimson; border-radius: 2px; display: inline-block; color: white !important; cursor: pointer; font-size: 0.75rem; font-weight: 300; letter-spacing: 0.2em; padding: 1em 2em 1.1em; position: relative; text-decoration: none !important; text-transform: uppercase; vertical-align: top;}
a.fill-mode-blue,
a.fill-mode-blue:hover{ background: midnightblue;}
a.fill-mode-green,
a.fill-mode-green:hover{ background: mediumseagreen;}

@keyframes tabs {
  0%  { opacity: 0.2;}
  1%  { opacity: 1;}
  33% { opacity: 1;}
  34% { opacity: 0.2;}
  100%{ opacity: 0.2;}
}

@keyframes toggle {
  0%  { opacity: 0;}
  1%  { opacity: 1;}
  33% { opacity: 1;}
  34% { opacity: 0;}
  100%{ opacity: 0;}
}

@keyframes race-none {
  0%  { background: crimson; left: 0;}
  33%  { background: crimson; left: 0;}
  34%  { background: midnightblue; left: 100px;}
  66%  { background: mediumseagreen; left: 200px}
  67%  { background: crimson; left: 0;}
  100%{ background: crimson; left: 0;}
}

@keyframes race-forwards {
  0%  { background: crimson; left: 0;}
  33%  { background: crimson; left: 0;}
  34%  { background: midnightblue; left: 100px;}
  66%  { background: mediumseagreen; left: 200px}
  67%  { background: mediumseagreen; left: 200px;}
  100%{ background: mediumseagreen; left: 200px;}
}

@keyframes race-backwards {
  0%  { background: midnightblue; left: 100px;}
  33%  { background: midnightblue; left: 100px;}
  34%  { background: midnightblue; left: 100px;}
  66%  { background: mediumseagreen; left: 200px}
  67%  { background: crimson; left: 0;}
  100%{ background: crimson; left: 0;}
}

@keyframes race-both {
  0%  { background: midnightblue; left: 100px;}
  33%  { background: midnightblue; left: 100px;}
  34%  { background: midnightblue; left: 100px;}
  66%  { background: mediumseagreen; left: 200px}
  67%  { background: mediumseagreen; left: 200px;}
  100%{ background: mediumseagreen; left: 200px;}
}
</style>

