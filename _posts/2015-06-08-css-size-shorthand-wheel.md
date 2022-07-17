---
layout: post
title: "CSS <strong>size</strong> shorthand <strong>wheel</strong>"
subtitle: "A <strong>circle</strong> shorthand method"
section: css
---

### Setting 4 values

Bütün tərəfləri (yuxarı, aşağı, sol və sağ) CSs propertyə daxil olduqda həmin CSS property **shorthand** property kimi çıxış edir.

Məsələn, `padding`xassəsindən 4 tərəfin hamsına _eyni_ dəyəri vermək üçün istifadə oluna bilər, həm də müəyyən bir tərəfi  (`padding-top`, `padding-bottom`, `padding-left` and `padding-right`) hədəfləmək üçün 4 varyasyondan istifadə edilir.

{% highlight css %}
blockquote{ padding: 20px;}
/* Is equivalent to */
blockquote{ padding-top: 20px; padding-bottom: 20px; padding-left: 20px; padding-right: 20px;}
{% endhighlight %}

Ancaq 'padding' xüsusiyyətinin maraqlı olduğu yer, odur ki, o **4** dəyəri ala bilir. Beləliklə siz 4 fərqli dəyəri bir dəfəyə təyin edə  bilərsiniz:

{% highlight css %}
blockquote{ padding: 20px 0 10px 50px;}
{% endhighlight %}

The order is `top`, `right`, `bottom` and `left`.

### 2 və ya 3 dəyər təyin etmək

2 dəyər verdikdə, birincisi `top` və `bottom` üçün tətbiq olunacaq, ikincisi isə `right` və `left`:

{% highlight css %}
blockquote{ padding: 20px 0;}
/*
       top
       20px
left         right
 0             0
      bottom
       20px
*/
{% endhighlight %}

### Stenoqrafiya qaydasını necə yadda saxlamaq olar

Hansı dəyərin tətbiq edildiyini yadda saxlamağın asan bir yolu var.

Daxil etdiyiniz dəyərlərə fokuslanmaq yerinə, **olmayan** dəyərlər barəsində düşünün.

* Əgər iki dəyər daxil etmisinizsə (top/right), `bottom` və `left` dəyərlərini ötürmüsünüz. Çünki `bottom` `top`un şaquli qarşılığıdır,  `top`nın dəyəriniz istifadə edəcək. VƏ `left` isə `right`ın üfüqi qarşılığıdır `right`ın dəyərini istifadə edəcək.
* Əgər 3 dəyər daxil etmizinizsə (top/right/bottom),  `left`i daxil etməmisiniz. `right`ın qarşılığında olduğu kimi, onun dəyərindən istifadə edəcək.

### "Çarx" stenoqrafiyası kimi çıxış edə bilən digər xüsusiyyətlər

4 tərəfə aid olan hər hansı bir xassələr:

* `margin`
* `padding`
* `border-width`

#### "Beləliklə, `border` stenoqrafiya xassəsidir `border-width` stenoqrafiya xassəsini ehtiva edən?"

Doğurdan da. `border` stenoqrafiyadır:

* `border-width`
* `border-style`
* `border-color`

Bununla belə, ikisini qarışdıra bilməzsiniz:

{% highlight css %}
blockquote{ border: 1px 0 solid green;}
/* Won't work */
{% endhighlight %}

Lakin siz `border`də eni pas keçib ayrıca təyin edə bilərsiniz:

{% highlight css %}
blockquote{ border: solid yellow; border-width: 1px 0;}
{% endhighlight %}
