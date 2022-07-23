---
layout: post
title: "CSS <strong>transform</strong>"
subtitle: "Fashioning unique shapes"
section: css
---

Biz indiyə qədər CSS-in bizə rəng tətbiq etməyə necə imkanlar verdiyini görmüşük, şriftləri təyin edin, mətn parametrlərini düzəldin, elementləri yerləşdirin, boşluq qoyun, bəzəyin, hərəkət etdirin.

CSS **transformlar** xüsusi üsullarla elementləri **formalaşdırmağa** imkan verən _funksiyalar_ toplusudur:

* **translate**: elementi 3 ox üzrə hərəkət etdirir (x,y və z)
* **rotate**: elementi mərkəzi nöqtə ətrafında hərəkət etdirir
* **scale**: elementin ölçüsünü dəyişir
* **skew**: elementi təhrif edir

### transform xassələri

3 ədəd transform xassəsi mövcuddur:

* `transform` _funksiyanın hansı transformasiyasından istifadə ediləcəyini müəyyən edir (translate, rotate, scale...)
* `transform-origin` transformasiyanın başlanğıc nöqtəsini dəyişdirməyə imkan verir ([background positions](/css-background.html#background-position) kimi işləyir)
* `transform-style` 3D parametrləri üçündür

Qeyd edək ki, `background` və `border`-dən fərqli olaraq, `transform` **shorthand property** deyil.

Transformdan yalnız burada istifadə edəcəyik.

#### Axını pozmur

Gözlənilməz davranışın qarşısını almaq üçün, transformed elementlər **axına təsir etmirlər**. Rotated, scaled və ya translated olsun, onlar digər elementlərə təsir etməyəcək.

### translate

`translate()` funksiyası elementi **müstəvi boyunca** köçürməyə imkan verir. (x və y oxunda).

* **1 parametr**: elementi `x` oxu boyunca hərəkət etdirir
* **2 parametr**: birinci dəyər `x` oxu üçündür, ikinci `y` oxu üçün

Bu, [relative positioning](/css-position.html#relative) funksiyasını `left` və `top` dəyərləri ilə istifadə etmək kimidir.

Sol/yuxarı positioning əvəzinə translation istifadə edərək [circuit animation](/css-animations.html#result-2)-ı yenidən edək:

{% highlight css %}
@keyframes translating {
  0%  { transform: translate(0, 0);}
  25% { transform: translate(240px, 0);}
  50% { transform: translate(240px, 140px);}
  75% { transform: translate(0, 140px);}
  100%{ transform: translate(0, 0);}
}
p{ animation: translating 4s linear infinite;}
{% endhighlight %}

<div class="result" id="translate-animation">
  <p>Hello</p>
</div>

<style type="text/css">
#translate-animation{ height: 200px; padding: 0; width: 300px;}
#translate-animation p{ animation: translating 4s linear 0s infinite; background: turquoise; color: white; height: 60px; line-height: 60px; margin: 0; position: absolute; text-align: center; width: 60px;}

@keyframes translating {
  0%  { transform: translate(0, 0);}
  25% { transform: translate(240px, 0);}
  50% { transform: translate(240px, 140px);}
  75% { transform: translate(0, 140px);}
  100%{ transform: translate(0, 0);}
}
</style>

Unutmayın `transform` CSS xassəsidir `translate()` CSS **dəyəridir** həmin xassəyə bağlıdır (həm də funksiya olur).
{: .focus}

Müvafiq olaraq yalnız `x` və `y` oxu üzrə hərəkət etdirmək üçün `translateX()` və `translateY()` istifadə edə bilərsiniz.

### rotate

`rotate()` funksiyası elementi **sabit nöqtə ətrafında fırlamağa imkan verir**. Default olaraq, elementin mərkəzi ətradında fırlanır. Bunu dönər masada oynanan vinil kimi düşünün.

`rotate()` yalnız **1** parametr alır, `deg` dərəcə ilə müəyyən edilmiş **bucaq** dəyəridir, gradian `grad`, radian `rad` və ya turn `turn` (1 dönüş tam dairəyə bərabərdir).

{% highlight css %}
@keyframes rotating {
  0%  { transform: rotate(0deg);}
  100%{ transform: rotate(360deg);}
}
p{ animation: rotating 4s linear infinite;}
{% endhighlight %}

<div class="result" id="rotate-animation">
  <p>Vinyl</p>
</div>

<style type="text/css">
#rotate-animation{ padding: 2rem;}
#rotate-animation p{ animation: rotating 4s linear 0s infinite; background: slateblue; border-radius: 60px; color: white; height: 120px; line-height: 120px; margin: 0; text-align: center; width: 120px;}

@keyframes rotating {
  0%  { transform: rotate(0deg);}
  100%{ transform: rotate(360deg);}
}
</style>

### scale

`scale()` funksiyası **elementin ölçüsünü dəyişməyə** imkan verir. Onu genişləndirə və ya daralda bilər. The function accepts either:

* **1 parametr**: element hündürlüyü və eni ilə bərabər ölçüsünü dəyişdirir
* **2 parametr**: birinci dəyər elementin ölçüsünü _üfüqi, ikincisi isə _şaquli olaraq dəyişir

Mümkün dəyərin **aralığı**-dır:

* `1`: element orijinal ölçüsünü saxlayır
* `2`: elementin ölçüsü ikiqat artır
* `0.5`: element ölçüsünün yarısıdır
* `0`: element əsasən yox olur (çünki onun hündürlüyü və eni sıfıra bərabərdir)
* `-1`: element əks olunur

{% highlight css %}
@keyframes scaling {
  0%  { transform: scale(1);}
  20%{ transform: scale(2);}
  40%{ transform: scale(0.5);}
  60%{ transform: scale(0);}
  80%{ transform: scale(-1);}
  100%{ transform: scale(1);}
}
p{ animation: scaling 10s steps(1) 0s infinite;}
{% endhighlight %}

<div class="result" id="scale-animation">
  <p><strong>scale(1)</strong>: normal size</p>
  <p><strong>scale(2)</strong>: double size</p>
  <p><strong>scale(0.5)</strong>: half size</p>
  <p><strong>scale(0)</strong>: zero size (invisible)</p>
  <p><strong>scale(-1)</strong>: mirrored</p>
  <div>Scaling</div>
</div>

<style type="text/css">
#scale-animation{ padding: 2rem;}
#scale-animation p{ animation: scaling-toggle 10s steps(1) 0s infinite forwards; background: white; color: grey; left: 2rem; margin: 0; opacity: 0; padding: 0 0.5em; position: absolute; top: 2rem; z-index: 1;}
#scale-animation p:first-child{ left: 0; position: relative; top: 0;}
#scale-animation p:nth-child(2){ animation-delay: 2s;}
#scale-animation p:nth-child(3){ animation-delay: 4s;}
#scale-animation p:nth-child(4){ animation-delay: 6s;}
#scale-animation p:nth-child(5){ animation-delay: 8s;}
#scale-animation p strong{ content: ""; display: inline-block;}
#scale-animation div{ animation: scaling 10s linear 0s infinite; background: goldenrod; border-radius: 60px; color: white; height: 120px; line-height: 120px; margin-top: 2rem;; text-align: center; transition: all 100ms linear; width: 120px;}

@keyframes scaling {
  0%  { transform: scale(1);}
  19% { transform: scale(1);}
  20% { transform: scale(2);}
  39% { transform: scale(2);}
  40% { transform: scale(0.5);}
  59% { transform: scale(0.5);}
  60% { transform: scale(0);}
  79% { transform: scale(0);}
  80% { transform: scale(-1);}
  99% { transform: scale(-1);}
  100%{ transform: scale(1);}
}

@keyframes scaling-toggle {
  0%  { opacity: 1;}
  20% { opacity: 0;}
  100%{ opacity: 0;}
}
</style>

`translate()` kimi, `scale()` funksiyasinin x və y versiyaları var: `scaleX()` və `scaleY()` müvafiq olaraq şaquli və üfüqi ölçülərinin dəyişir.

### skew

`skew()` funksiyası **elementi təhrif etməyə** imkan verir, tərəflərini əsasən bir xətt boyunca sürükləməklə.

Bu transform funksiyası nadir hallarda istifadə olunur, çünki onun olduqca gözlənilməz təsirləri var, və onun nəticələri cəlbedici deyil. Buna baxmayaraq, bunun necə işlədiyini görək.

`scale()` kimi, `skew()` funksiyasıda dəstəkləyir:

* **1 parameter**: element üfüqi şəkildə təhrif olunur
* **2 parameters**: birinci dəyər elementi _üfüqi_, ikincisi isə _şaquli_ olaraq təhrif edir

Və `rotate()` kimi, `skew()` yalnız dərəcə `deg` kimi **bucaq** dəyərlərini qəbul edir.

{% highlight css %}
@keyframes skewing {
  0%  { transform: skew(0deg);}
  20% { transform: skew(10deg);}
  40% { transform: skew(45deg);}
  60% { transform: skew(90deg);}
  80% { transform: skew(120deg);}
  100%{ transform: skew(0deg);}
}
p{ animation: skewing 10s steps(1) 0s infinite;}
{% endhighlight %}

<div class="result" id="skew-animation">
  <p><strong>skew(0deg)</strong>: no distortion</p>
  <p><strong>skew(10deg)</strong>: subtle horizontal distortion</p>
  <p><strong>skew(45deg)</strong>: quarter distortion</p>
  <p><strong>skew(90deg)</strong>: half distortion (invisible)</p>
  <p><strong>skew(120deg)</strong>: same as -60deg</p>
  <div>Skewing</div>
</div>

<style type="text/css">
#skew-animation{ padding: 2rem;}
#skew-animation p{ animation: scaling-toggle 10s steps(1) 0s infinite forwards; background: white; color: grey; left: 2rem; margin: 0; opacity: 0; padding: 0 0.5em; position: absolute; top: 2rem; z-index: 1;}
#skew-animation p:first-child{ left: 0; position: relative; top: 0;}
#skew-animation p:nth-child(2){ animation-delay: 2s;}
#skew-animation p:nth-child(3){ animation-delay: 4s;}
#skew-animation p:nth-child(4){ animation-delay: 6s;}
#skew-animation p:nth-child(5){ animation-delay: 8s;}
#skew-animation div{ animation: skewing 10s linear infinite; background: tomato; color: white; height: 60px; line-height: 60px; margin-top: 2rem;; text-align: center; transition: all 100ms linear; width: 120px;}

@keyframes skewing {
  0%  { transform: skew(0deg);}
  19% { transform: skew(0deg);}
  20% { transform: skew(10deg);}
  39% { transform: skew(10deg);}
  40% { transform: skew(45deg);}
  59% { transform: skew(45deg);}
  60% { transform: skew(90deg);}
  79% { transform: skew(90deg);}
  80% { transform: skew(120deg);}
  99% { transform: skew(120deg);}
  100%{ transform: skew(180deg);}
}

@keyframes skewing-toggle {
  0%  { opacity: 1;}
  20% { opacity: 0;}
  100%{ opacity: 0;}
}
</style>

### 3d functions

Transformasiya funksiyalarının x və y oxu boyunca **müstəvidə** necə işlədiyini gördük.

Nümunə:

* `translate()` with up to 2 parameters:
  * `translate(x)`
  * `translate(x,y)`
* `translateX()` as x only
* `translateY()` as y only

Lakin bütün bu funksiyaların **3D versiyası** da var.

Məsələn, `translate()` **3 ölçü** boyunca transformasiyanı həyata keçirən `translate3d()` versiyasına malikdir, bu o deməkdir ki, o, həmçinin **z oxunu** ehtiva edir (və beləliklə, müstəqil `translateZ()` funksiyası da mövcuddur).

**z** parametri əsasən elementi daha da yaxınlaşdırır, onun dəyərini artırsaq da, azaltsaq da. Bu, böyütmək və kiçiltmək kimidir.

{% highlight css %}
@keyframes zooming {
  0%  { transform: translate3d(0, 0, 0);}
  100%{ transform: translate3d(0, 0, 200px);}
}
p{ animation: zooming 5s alternate;}
{% endhighlight %}

<div class="result" id="zoom-animation">
  <div>Original</div>
  <p>Transformed</p>
</div>

<style type="text/css">
#zoom-animation{ padding: 2rem; perspective: 500;}
#zoom-animation div,
#zoom-animation p{ background: midnightblue; color: white; height: 200px; line-height: 200px; margin: 0; position: relative; text-align: center; width: 200px;}
#zoom-animation p{ animation: zooming 5s alternate infinite both; background: limegreen; left: 2rem; opacity: 0.7; position: absolute; top: 2rem;}

@keyframes zooming {
  0%  { transform: translate3d(0, 0, 0);}
  100%{ transform: translate3d(0, 0, 200px);}
}
</style>

Yaşıl blok z oxu boyunca `200px` _"yuxarıya"_ yüksəlir, sanki bizə yaxınlaşır.

`perspective: 500;` 3D məkanının aktiv olması üçün ana elementə tətbiq edilməlidir. Alternativ olaraq, `transform: perspective(500px);` də istifadə etmək olar.
{: .info}
