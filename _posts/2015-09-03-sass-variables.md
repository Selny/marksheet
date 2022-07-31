---
layout: post
title: "Sass <strong>variables</strong>"
subtitle: "Change once, update everywhere"
section: sass
---

İnsanların Sass-a müraciət etmələrinin ilk səbəblərindən biri **CSS dəyişənlərinin** olmasıdır.

Heç eyni CSS _value_-un bir çox hadisəsini axtarıb əvəz etməli olmusunuzmu? Əgər belədirsə, dəyişənlər sizə kömək edəcək.

### Syntax

Siz `$` dollar işarəsini dəyişənin əvvəlinə yazmalısınız:

{% highlight scss %}
$yellow: #fce473;
{% endhighlight %}

Bu xətt dəyişəni **müəyyən etməkdən** başqa heç nə etmir, bizim vəziyyətimizdə sarı rəng:

<div style="background: #fce473; display: inline-block; padding: 10px; vertical-align: top;">#fce473</div>

Bundan sonra [rəng vahidi](/css-color-units.html) tələb olunduqda: biz onu CSS-də istifadə edə bilərik:

{% highlight scss %}
.quote{ border-left: 5px solid $yellow;}
{% endhighlight %}

Bu `.scss` faylı `.css` faylına **tərtib ediləcək**, burada bütün dəyişənlər öz həqiqi _dəyəri ilə _əvəz ediləcək:

{% highlight css %}
.quote{ border-left: 5px solid #fce473;}
{% endhighlight %}

_Why is it called a variable?_{:.question}
Burada **dəyər** `#fce473` dəyişəndir. `$yellow` adının mənası _sabit_ qalır, lakin dəyər _dəyişə bilər.
{: .answer}

### Dəyişəninizi yalnız bir dəfə təyin edin

Dəyişənlərin istifadə məqsədini göstərmək üçün siz onu bir dəfədən çox istifadə etməlisiniz, məsələn, bu **çəhrayı** kölgə:

<div style="background: #ff1493; color: white; display: inline-block; padding: 10px; vertical-align: top;">#ff1493</div>

{% highlight scss %}
$pink: #ff1493;
.quote{ border-left: 5px solid $pink;}
.button{ background: $pink;}
.sidebar a:hover{ border-bottom-color: $pink;}
.footer a{ color: $pink;}
{% endhighlight %}

Bu tərtib ediləcək:

{% highlight css %}
.quote{ border-left: 5px solid #ff1493;}
.button{ background: #ff1493;}
.sidebar a:hover{ border-bottom-color: #ff1493;}
.footer a{ color: #ff1493;}
{% endhighlight %}

Fərqli çəhrayı çalarları seçməyə qərar verdinizsə:

<div style="background: #ff1493; color: white; display: inline-block; padding: 10px; vertical-align: top;">Old pink</div>
<div style="background: #c71585; color: white; display: inline-block; padding: 10px; vertical-align: top;">New pink</div>

Rəng dəyərini **bir dəfə** dəyişməli olacaqsınız:

{% highlight scss %}
$pink: #c71585;
{% endhighlight %}

Və nəticədə CSS **avtomatik** yenilənəcək:

{% highlight css %}
.quote{ border-left: 5px solid #c71585;}
.button{ background: #c71585;}
.sidebar a:hover{ border-bottom-color: #c71585;}
.footer a{ color: #c71585;}
{% endhighlight %}


İndi deyək ki, siz əslində **əsas** rənginiz kimi çəhrayıdan istifadə etmək istəmirsiniz, amma **yaşıl**!

<div style="background: #32cd32; color: white; display: inline-block; padding: 10px; vertical-align: top;">#32cd32</div>

Siz `$green: #32cd32;` dəyişənini təyin etməli **və** SCSS-də `$pink`-in bütün nümunələrini `$green` ilə əvəz etməli olacaqsınız.

Daha yaxşı bir yol var:

{% highlight scss %}
// Defining color values
$yellow: #fce473;
$pink: #c71585;
$green: #32cd32;
$blue: #1d90ff;

// Defining color types
$primary-color: $green;

.quote{ border-left: 5px solid $primary-color;}
.button{ background: $primary-color;}
.sidebar a:hover{ border-bottom-color: $primary-color;}
.footer a{ color: $primary-color;}
{% endhighlight %}

'$yaşıl' dəyişəninə _birbaşa_ istinad etmək əvəzinə, siz '$yaşıl' olaraq təyin edilmiş **əsas rəng** dəyişənini təyin edirsiniz.

Bu barədə düşünəndə, CSS-də `$yaşıl` istifadə etmək istəmirsiniz. _Əslində_ istədiyiniz yaşıl rəngə çevrilən **əsas rənginizdən** istifadə etməkdir.

Əsas rəng kimi `$mavi` istifadə etmək qərarına gəlsəniz, yalnız **tək sətri** dəyişməli olacaqsınız.

### İstənilən növ dəyər üçün

Rəngləri müəyyən etmək üçün dəyişənlərdən istifadə etdik, lakin siz **istənilən məzmun növü** təyin edə bilərsiniz:

{% highlight scss %}
// Colors
$yellow:              #fce473;
$pink:                #c71585;
$green:               #32cd32;
$blue:                #1d90ff;

$primary-color:       $blue;
$secondary-color:     $yellow;

// Fonts
$serif:               "Lora", "Playfair Display", Georgia, serif;
$sans-serif:          "Roboto", "Source Sans Pro", "Open Sans", Arial, sans-serif;
$monospace:           "Inconsolata", monospace;

$primary-font:        $sans-serif;
$secondary-font:      $serif;

// Spacing
$mobile-space:        10px;
$desktop-space:       35px;
{% endhighlight %}
