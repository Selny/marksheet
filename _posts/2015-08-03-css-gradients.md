---
layout: post
title: "CSS <strong>gradients</strong>"
subtitle: "From one color to another"
section: css
---

CSS gradientlər haqda danışarkən, **rənglərin gradientlərindən** bəhs edirik.

CSS-də iki növ gradient var:

* **linear**: rənglər düz xətt üzrə bir nöqtədən başqa nöqtəyə gedir
* **radials**: rənglər dairənin mərkəzindən onun kənarlarına, bütün istiqamətlərdə gedir

Qradient **background image** hesab olunur və müvafiq xüsusiyyətlə istifadə edilməlidir.

### linear-gradient

Xətti gradientlər üçün sintaksis [olduqca mürəkkəbdir](https://developer.mozilla.org/en-US/docs/Web/CSS/linear-gradient), lakin əsas ideya müəyyən etməkdir:

* hansı **rəngləri** istəyirsiniz
* bu rənglərin **ox boyunca** harada görünəcəyini (başda, ortada, sonda, və s.)
* və **gradientin** hansı istiqamətdə gedəcəyi

Gəlin indi sadə iki rəngli gradient ilə başlayaq:

{% highlight css %}
div{ background-image: linear-gradient(red, blue);}
{% endhighlight %}

{% highlight html %}
<div>A simple vertical background gradient</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(red, blue);">A simple vertical background gradient</div>
</div>

Default olaraq:

* **şaquli** **istiqamətdə**, _yuxarıdan_ _aşağıya_
* **birinci** rəng **başlanğıcda** (yuxarıda)
* **ikinci** rəng **sonda** (aşağıda)

#### Istiqamətin dəyişdirilməsi

Əgər yuxarıdan aşağıya doğru olan istiqamət sizə uyğun gəlmədisə, dəyişdirə bilərsiniz:

* **qradientin təyinatının** müəyyən edilməsi `to left top` açar sözü ilə olur
* `45 deg` kimi dərəcələrdə xüsusi **bucağı** müəyyən etmək

İtiqamət rəngdən əvvəl təyin edilməlidir:

{% highlight css %}
div{ background-image: linear-gradient(to bottom right, yellow, purple); width: 200px;}
{% endhighlight %}

{% highlight html %}
<div>A diagonal gradient from the top left corner to the bottom right one</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(to bottom right, yellow, purple); width: 200px;">A diagonal gradient from the top left corner to the bottom left one</div>
</div>

Daha çox **xüsusi bucaq** vermək istəsəniz, **dərəcə** dəyərindən istifadə edə bilərsiniz:

* `0deg` yuxarıdan aşağı default dəyərdir
* `20deg` bir az diaqonaldır, və **saat əqrəbi istiqamətində** gedir
* `90deg` saat 3 kimi, sağdan sola
* `180deg` aşağıdan yuxarıya doğrudur

{% highlight css %}
div{ background-image: linear-gradient(20deg, green, blue); width: 150px;}
{% endhighlight %}

{% highlight html %}
<div>A diagonal gradient with an angle of 20 degrees</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(20deg, green, blue); width: 150px;">A diagonal gradient with an angle of 20 degrees</div>
</div>

#### Daha çox rəng əlavə etmək

İstədiyiniz qədər rəng əlavə edə bilərsiniz. Onlar ox boyunca **bərabər paylanacaq**:

* **2 rəng**: 0% və 100%
* **3 rəng**: 0%, 50% və 100%
* **4 rəng**: 0%, 33%, 67% və 100%

{% highlight css %}
div{ background-image: linear-gradient(orange, grey, yellow); width: 150px;}
{% endhighlight %}

{% highlight html %}
<div>A rather ugly gradient, but you get the idea</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(orange, grey, yellow); width: 150px;">A rather ugly gradient, but you get the idea</div>
</div>

#### Xüsusi rəngin təyin edilməsinin dayandırılması

Rənglərin bərabər paylanmasını istəmirsinizsə, faizlərdən `%` və ya piksel `px` istifadə edərək xüsusi **rəng dayandırma mövqelərini** təyin edə bilərsiniz:

{% highlight css %}
div{ background-image: linear-gradient(orange, grey 10%, yellow 50%); width: 150px;}
{% endhighlight %}

{% highlight html %}
<div>An even uglier gradient, but you get the idea</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: linear-gradient(orange, grey 10%, yellow 50%); width: 150px;">An even uglier gradient, but you get the idea</div>
</div>

Bu quraşdırmada:

* `orange`-ın dayanma mövqeyi yoxdur, ona görə defolt olaraq **sıfır** `0%`-dir
* `grey` yuxarıya daha yaxındır, `50%` yerinə `10%`-dir
* `yellow` `50%`-dən `100%`-ə kimi gradientin yarısını alır

### radial-gradient

Xətti qradiyentlər bir xətti izləyərkən, **radial qradientlər** bütün istiqamətlərə yayılır. Onların sintaksisi xətti olanlara kifayət qədər bənzəyir, çünki hər ikisində **rəng dayanacaqları** var. Ancaq bir _istiqaməti_ təyin etmək əvəzinə, müəyyən etməlisiniz:

* **forma**: ya dairə yada ellips
* **başlanğıc nöqtəsi**: dairənin/ellipsin mərkəzi olacaq
* **bitmə nöqtəsi**: dairənin/ellipsin kənarının olacağı yer

{% highlight css %}
div{ background-image: radial-gradient(red, yellow); padding: 1rem; width: 300px;}
{% endhighlight %}

{% highlight html %}
<div>This looks like the sun, doesn't it?</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: radial-gradient(red, yellow); padding: 1rem; width: 300px;">This looks like the sun, doesn't it?</div>
</div>

Default olaraq:

* qradient **ellipse** formasındadır
* birinci rəng **mərkəzdən** başlayır
* sonuncu rəng **ən uzaq künc**-də bitir

#### Start position/(Başlanğıc vəziyyəti)

**start position** **[background positions](/css-background.html#background-position)** kimi işləyir. `at` açar sözü ilə təyin edilir.

{% highlight css %}
div{ background-image: radial-gradient(at top right, black, lightgrey); padding: 1rem; width: 300px;}
{% endhighlight %}

{% highlight html %}
<div>A gloomy day.</div>
{% endhighlight %}

<div class="result" style="padding: 1rem;">
  <div style="background-image: radial-gradient(at top right, black, lightgrey); padding: 1rem; width: 300px;">A gloomy day.</div>
</div>

#### end position/(bitiş vəziyyəti)

Default olaraq, forma **ən uzaq küncdə** bitəcək. Siz seçə bilərsiniz:

* `closest-side`
* `closest-corner`
* `farthest-side`
* `farthest-corner`

Fərqi həm başa düşmək, həm də vizuallaşdırmaq çətindir, ona görə də təfərrüatlara girməyəcəyik. Mozilla [müxtəlif dəyərlərin yaxşı təsvirinə malikdir](https://developer.mozilla.org/en-US/docs/Web/CSS/radial-gradient#Values).

{% highlight css %}
div{ background-image: radial-gradient(closest-corner at 20px 20px, green, blue); padding: 1rem; width: 300px;}
div:hover{ background-image: radial-gradient(farthest-side at 20px 20px, green, blue)}
{% endhighlight %}

{% highlight html %}
<div>Hover this green star in the sky to see it expand.</div>
{% endhighlight %}

<div class="result" id="result-831">
  <div>Hover this green star in the sky to see it expand.</div>
</div>

#### fixed size

start _və_ end positionlarını təyin etmək yerinə, sadəcə **xüsusi ölçüləri** təyin edə bilərsiniz:

{% highlight css %}
div{ background-image: radial-gradient(20px 10px at 75% 50%, darkviolet, pink); padding: 1rem; width: 300px;}
{% endhighlight %}

{% highlight html %}
<div>A small violet disc in a sea of pink.</div>
{% endhighlight %}

<div class="result">
  <div style="background-image: radial-gradient(20px 10px at 75% 50%, darkviolet, pink); padding: 1rem; width: 300px;">A small violet disc in a sea of pink.</div>
</div>

Seçimlərin nə qədər sonsuz olduğunu nəzərə alsaq, CSS gradientləri çox güclüdür.

Lakin xüsusilə düymələr üçün daha çox **incə** gradient yazmaq olduqca asandır:

{% highlight css %}
.button-grey  { background-image: linear-gradient(#f2f2f2, #f2f2f2);}
.button-yellow{ background-image: linear-gradient(#fce374, #fcdf5b);}
.button-orange{ background-image: linear-gradient(#f58a38, #f57c20);}
.button-red   { background-image: linear-gradient(#ed6d64, #ed574c);}
.button-purple{ background-image: linear-gradient(#847bba, #7568ba);}
.button-blue  { background-image: linear-gradient(#42b0e3, #2ba9e3);}
.button-green { background-image: linear-gradient(#97cc76, #8bcc62);}
{% endhighlight %}

<div class="result" id="result-832">
  <a class="button-grey">Button</a>
  <a class="button-yellow">Button</a>
  <a class="button-orange">Button</a>
  <a class="button-red">Button</a>
  <a class="button-purple">Button</a>
  <a class="button-blue">Button</a>
  <a class="button-green">Button</a>
</div>

<style type="text/css">
#result-831{ padding: 1rem;}
#result-831 div{ background-image: radial-gradient(closest-corner at 20px 20px, green, blue); padding: 1rem; width: 300px;}
#result-831 div:hover{ background-image: radial-gradient(farthest-side at 20px 20px, green, blue)}
#result-832{ padding: 1rem;}
#result-832 a{ background-image: linear-gradient(lightblue, skyblue); border: 1px solid #eee; border-radius: 3px; color: grey; display: inline-block; line-height: 32px; padding: 0 15px; text-decoration: none; transition: none; vertical-align: top;}
#result-832 .button-grey {
  background-color: #f2f2f2;
  background-image: linear-gradient(to bottom, #f2f2f2, #f2f2f2);
  border: 1px solid #bfbfbf;
  box-shadow: inset 0 1px 0 white, inset 0 -1px 0 #d9d9d9, inset 0 0 0 1px #f2f2f2, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: #8c8c8c;
  text-shadow: 0 1px 0 rgba(255, 255, 255, 0.5);
}
#result-832 .button-grey:hover, #result-832 .button-grey:focus {
  background: #f2f2f2;
  border-color: #8c8c8c;
  box-shadow: inset 0 1px 0 white, inset 0 -1px 0 #d9d9d9, inset 0 0 0 1px #f2f2f2;
}
#result-832 .button-grey:active {
  background: #f2f2f2;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-blue {
  background-color: #42b0e3;
  background-image: linear-gradient(to bottom, #42b0e3, #2ba9e3);
  border: 1px solid #107db0;
  box-shadow: inset 0 1px 0 #7cd4fc, inset 0 -1px 0 #2696c9, inset 0 0 0 1px #59b7e3, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-blue:hover, #result-832 .button-blue:focus {
  background: #2ba9e3;
  border-color: #004c6f;
  box-shadow: inset 0 1px 0 #7cd4fc, inset 0 -1px 0 #2696c9, inset 0 0 0 1px #59b7e3;
}
#result-832 .button-blue:active {
  background: #2ba9e3;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-green {
  background-color: #97cc76;
  background-image: linear-gradient(to bottom, #97cc76, #8bcc62);
  border: 1px solid #5f993a;
  box-shadow: inset 0 1px 0 #c6e5b3, inset 0 -1px 0 #79b356, inset 0 0 0 1px #a4cc8b, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-green:hover, #result-832 .button-green:focus {
  background: #8bcc62;
  border-color: #326612;
  box-shadow: inset 0 1px 0 #c6e5b3, inset 0 -1px 0 #79b356, inset 0 0 0 1px #a4cc8b;
}
#result-832 .button-green:active {
  background: #8bcc62;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-purple {
  background-color: #847bba;
  background-image: linear-gradient(to bottom, #847bba, #7568ba);
  border: 1px solid #493e87;
  box-shadow: inset 0 1px 0 #bab6d4, inset 0 -1px 0 #655aa1, inset 0 0 0 1px #948dba, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-purple:hover, #result-832 .button-purple:focus {
  background: #7568ba;
  border-color: #1f1654;
  box-shadow: inset 0 1px 0 #bab6d4, inset 0 -1px 0 #655aa1, inset 0 0 0 1px #948dba;
}
#result-832 .button-purple:active {
  background: #7568ba;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-orange {
  background-color: #f58a38;
  background-image: linear-gradient(to bottom, #f58a38, #f57c20);
  border: 1px solid #c25706;
  box-shadow: inset 0 1px 0 #ffb984, inset 0 -1px 0 #db6f1d, inset 0 0 0 1px #f59851, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-orange:hover, #result-832 .button-orange:focus {
  background: #f57c20;
  border-color: #773300;
  box-shadow: inset 0 1px 0 #ffb984, inset 0 -1px 0 #db6f1d, inset 0 0 0 1px #f59851;
}
#result-832 .button-orange:active {
  background: #f57c20;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-red {
  background-color: #ed6d64;
  background-image: linear-gradient(to bottom, #ed6d64, #ed574c);
  border: 1px solid #ba3329;
  box-shadow: inset 0 1px 0 #ffb0aa, inset 0 -1px 0 #d44d44, inset 0 0 0 1px #ed837b, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: white;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}
#result-832 .button-red:hover, #result-832 .button-red:focus {
  background: #ed574c;
  border-color: #870c03;
  box-shadow: inset 0 1px 0 #ffb0aa, inset 0 -1px 0 #d44d44, inset 0 0 0 1px #ed837b;
}
#result-832 .button-red:active {
  background: #ed574c;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}

#result-832 .button-yellow {
  background-color: #fce374;
  background-image: linear-gradient(to bottom, #fce374, #fcdf5b);
  border: 1px solid #c9ae34;
  box-shadow: inset 0 1px 0 #fff6ce, inset 0 -1px 0 #e3c852, inset 0 0 0 1px #fce88d, 0 2px 4px rgba(0, 0, 0, 0.2);
  color: #967d09;
  text-shadow: 0 1px 0 rgba(255, 255, 255, 0.5);
}
#result-832 .button-yellow:hover, #result-832 .button-yellow:focus {
  background: #fcdf5b;
  border-color: #967d09;
  box-shadow: inset 0 1px 0 #fff6ce, inset 0 -1px 0 #e3c852, inset 0 0 0 1px #fce88d;
}
#result-832 .button-yellow:active {
  background: #fcdf5b;
  box-shadow: inset 0 2px 3px rgba(0, 0, 0, 0.2);
}
</style>
