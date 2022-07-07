---
layout: post
title: "CSS <strong>Size</strong> units"
subtitle: "Sizing for <strong>content</strong> and <strong>space</strong>"
section: css
---

**Ölçü vahidi** tələb edən bir çox css xassələri var:

* `font-size` mətnin ölçüsünü təyin edir
* `border-width` elementin borderlərinin ölçülərini təyin edir
* `margin` elementlər arasındakı məsafəni təyin edir
* `left/right/top/bottom` elementləri yerləşdirməyə imkan verir

Ən çox istifadə olunanlar:

* piksel vahidi üçün `px`
* faiz vahidi üçün `%`
* `font-size` dəyərinin parent-lərin nisbi ölçüləri üçün `em`.

### Pixels/Piksellər

Çünki komputer ekranları məzmunu çap etmək üçün piksellərdən istifadə edir, bu **CSS də ən çox istifadə olunan ölçü vahididir**.

Bu elementlərin enini düzəltmək üçün istifadə oluna bilər:

{% highlight css %}
body{ width: 400px;}
{% endhighlight %}

Və ya **nətnin ölçüsünü** verə bilərsiniz:

{% highlight css %}
body{ font-size: 20px;}
{% endhighlight %}

Piksellər CSS də çox sadədir, çünki onlar **mütləq dəyərləri** müəyyən edirlər: onlar digər inherited CSS xassələrinə təsir etmirlər.

Onlar həmçinin **positioning/(yerləşdirmə)** və **boşluqları** təyin etmə .

### Percentages

Percentages **nisbi vahidlərdir**: onlar elementin parentlərinə və/yaxud ancestorlarına etibar edirlər.

Məsələn, block-level elementlər paraqraflar kimi təbii olaraq **əlçatan bütün genişliyi** götürür. Aşağıdakı CSS qaydası mövcud olan genişliyi **yarıya** endirir.

{% highlight css %}
p{ width: 50%;}
{% endhighlight %}

Percentages başqa CSS xassələri ilədə istifadə oluna bilər, text size kimi:

{% highlight css %}
strong{ font-size: 150%;}
{% endhighlight %}

{% highlight html %}
<p>There are <strong>important</strong> challenges ahead of us.</p>
{% endhighlight %}

<div class="result">
  <p>There are <strong style="font-size: 150%;">important</strong> challenges ahead of us.</p>
</div>

### Em

`em`  **relative** dəyərdir: `font-size` elementinin dəyərindən asılıdır.

Məsələn, əgər parent elementin `20px` font-size-ı varsa və child elementə `font-size: 0.8em` versək, bu chil element font-size `16px` dəyərində ekrana cıxaracaq.

CSS olçü vahidi olan `em`-i qarışdırmayın və `em` CSS selektorlarını, hansı ki, `<em>` HTML elementini hədəf alır
{: .info}

HTML elementlərinin şrift ölçülərini bir-birinə _nisbi olaraq təyin etdiyiniz üçün `em` vahidi maraqlıdır. Dizayn üçün cəlbedici və veb səhifələri oxumaq üçün rahatdır, sadəcə ardıcıl vizual dərinliyə ehtiyac var. Məsələn, `<h1>` elementinizi body elementinin mətnindən iki dəfə böyül eləmək istəsəniz, `<h2>` teqiniz sadəcə 1.5 dəfə böyük olacaq, və sidebariniz biraz daha kiçik. Buna CSS-də asanlıqla nail olmaq olar:

{% highlight css %}
body{ font-size: 16px;}
h1{ font-size: 2em;}        /* = 32px */
h2{ font-size: 1.5em;}      /* = 24px */
aside{ font-size: 0.75em;}  /* = 12px */
{% endhighlight %}

Əgər body elementinin mətninn olçüsünü dəyişmək qərarına gəlsəniz, headinglərinizin və sidebarinizin nisbi ölçüləri **müvafiq olaraq** dəyişəcək, və veb səhifəniz **vizual olaraq balanslı** qalacaq

Sadəcə bir dəyəri dəyişməklə, bütün qalan dəyərlər dəyişmiş olur:

{% highlight css %}
body{ font-size: 20px;}
h1{ font-size: 2em;}        /* = 40px */
h2{ font-size: 1.5em;}      /* = 30px */
aside{ font-size: 0.75em;}  /* = 16px */
{% endhighlight %}

### Rem

`rem` olçü vahidi `em`-ə oxşardır, ancaq _paren_ elementin dəyərinə görə deyil, **root elementin** dəyərinə görə dəyər alır, which is the `<html>` element.

{% highlight css %}
html{ font-size: 18px;}
body{ font-size: 1rem;}     /* = 18px */
h1{ font-size: 2rem;}       /* = 36px */
h2{ font-size: 1.5rem;}     /* = 27px */
{% endhighlight %}

`rem` və `em` arasındakı fərq is that `rem`-in dəyərləri **sabitdir** halbuki `em`-in dəyəri isə bir birleri arasında çoxala bilər.

Əgər `html{ font-size: 18px;}` təyin etmisinizsə:

* `2rem` hər zaman `36px`-a bərabər olacaq, CSS-də harada istifadə etdiyinizdən asılı olmayaraq
* `2em` hər zaman parentinin  `font-size`-ın **iki qatı** qədər dəyərə sahib olacaq, yeni `36px` olması mütləq deyil

`2em` ilə  `2rem` arasındakı fərqə dair nümunə:

{% highlight css %}
html{ font-size: 20px;}
p{ font-size: 0.8rem;}        /* = 16px */
p span{ font-size: 2em;}      /* = 16px * 2 = 32px */
p strong{ font-size: 2rem;}   /* = 20px * 2 = 40px */
{% endhighlight %}

`span` `p` şrift ölçüsü dəyərinə, `strong` isə `html` şrift ölçüsü dəyərinə əsaslanır.

### Which unit to use?/(Hansı vahiddən istifadə edilməli)

Başlanğıc üçün **piksel** tövsiyə edərdim: çünki onlar mütləq dəyərlərdir, onlar elementlərin məzmununa təsir etmirlər. Onlar sadədir, text ölçüsünü, image ölçülərini, border enini, position koordinatlarını təyin etməyə imkan verir...

**Percentage** və **em** dəyərləri piksellərlə birlikdə istifadə oluna biler, xüsusəndə nisbi text size üçün.
