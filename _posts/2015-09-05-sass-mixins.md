---
layout: post
title: "Sass <strong>mixins</strong>"
subtitle: "CSS programming"
section: sass
---

Özünüzü təkrar-təkrar eyni kodu yazarkən tapdığınız zaman Sass mixinləri sizə kömək edə bilər.

Sass mixinləri istədiyiniz zaman **daxil edə biləcəyiniz **CSS funksiyalarıdır**.

### Syntax

**[CSS animasiyaları](/css-animations.html)** yaratarkən `@keyframes`-i necə yazdığımızı xatırlayırsınız? Sass mixin sintaksisi olduqca oxşardır:

{% highlight scss %}
@mixin overlay() {
  bottom: 0;
  left: 0;
  position: absolute;
  right: 0;
  top: 0;
}
{% endhighlight %}

Bu miksinin **adı** `overlay`-dir. Siz `@include` istifadə edərək istənilən CSS qaydasında bu mixin istinad edə bilərsiniz:

{% highlight scss %}
.modal-background{
  @include overlay();
  background: black;
  opacity: 0.9;
}
{% endhighlight %}

Həmişə olduğu kimi, bu `.scss` `.css`-də tərtib ediləcək:

{% highlight css %}
.modal-background{
  bottom: 0;
  left: 0;
  position: absolute;
  right: 0;
  top: 0;
  background: black;
  opacity: 0.9;
}
{% endhighlight %}

### Reusability

Miksinlərin əsas məqsədi **xassələr toplusunu təkrar istifadə edilə bilən etməkdir.

Sass dəyişənləri kimi (bir yerdə **dəyərlərinizi** təyin etdiyiniz yerdə), Sass miksinləri sizə bir yerdə **propertylər** müəyyən etməyə imkan verir.

Əvvəlki miksin digər qaydalarda təkrar istifadə edilə bilər:

{% highlight scss %}
.modal-background{
  @include overlay();
}

.product-link{
  @include overlay();
}

.image-pattern{
  @include overlay();
}
{% endhighlight %}

{% highlight css %}
.modal-background{
  bottom: 0;
  left: 0;
  position: absolute;
  right: 0;
  top: 0;
}

.product-link{
  bottom: 0;
  left: 0;
  position: absolute;
  right: 0;
  top: 0;
}

.image-pattern{
  bottom: 0;
  left: 0;
  position: absolute;
  right: 0;
  top: 0;
}
{% endhighlight %}

### Parameters

Miksinlər **funksiyalar** olduğundan və _output_-da **dəyişiklik etmək istəyə biləcəyiniz üçün miksinlər **parametrləri** qəbul edə bilər.

Məsələn, bu [border-radius mixin](https://sass-lang.com/guide#topic-6-SCSS) **satıcı prefikslərinin** yenidən yazılmasının qarşısını alır və faktiki _radius_ dəyərini parametr kimi qəbul edir:

{% highlight scss %}
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box{
  @include border-radius(3px);
}
{% endhighlight %}

{% highlight css %}
.box{
  -webkit-border-radius: 3px;
     -moz-border-radius: 3px;
      -ms-border-radius: 3px;
          border-radius: 3px;
}
{% endhighlight %}

Mixin bütün satıcı prefikslərini yazmaq çətinliyindən yayınır və hər bir satıcı xassəsi üçün eyni radius dəyərini müəyyən etməyə imkan vermək üçün `$radius` istifadə edir.

### Optional parameters

Əgər siz bir parametrin **defolt** dəyərə malik olmasını istəyirsinizsə, hərdən bir parametri təyin etmək imkanı verirsinizsə, siz **istəyə bağlı parametrlər** yarada bilərsiniz:

{% highlight scss %}
@mixin label($text: "Code", $background: $yellow, $color: rgba(black, 0.5)) {
  position: relative;
  &:before{
    background: $background;
    color: $color;
    content: $text;
    display: inline-block;
    font-size: 0.6rem;
    font-weight: 700;
    height: 1rem;
    left: 0;
    letter-spacing: 0.1em;
    line-height: 1rem;
    padding: 0 0.5em;
    position: absolute;
    text-transform: uppercase;
    top: 0;
  }
}
{% endhighlight %}

Bu miksin bu vebsayt tərəfindən kod parçalarının yuxarı sol küncünə **etiketlər** əlavə etmək üçün istifadə edilən mixindir. Onun 3 isteğe bağlı parametri var, onların hər biri iki nöqtə `:` ilə təyin edilmiş öz standart dəyərinə malikdir.

Bu mixin kod boyunca bir neçə dəfə istifadə olunur:

{% highlight scss %}
div.highlighter-rouge{
  @include label();
  &.css{
    @include label("CSS", $blue, white);
  }
  &.scss{
    @include label("SCSS", #c69, white);
  }
}
{% endhighlight %}

`div.highlighter-rouge` miksinin standart dəyərlərindən istifadə edəcək:

* text `"Code"`
* background: `$yellow`
* color: `rgba(black, 0.5)`

`.css` və `.scss` versiyaları, onların parametrləri _set_ olduğundan, müxtəlif etiket və rənglərdən istifadə edəcək.

### Mixin libraries

Öz Sass mixinlərinizi yazmağa vaxt sərf etmək istəmirsinizsə, aşağıdakı **mixin kitabxanalarından** istifadə edə bilərsiniz:

* **Bourbon**: [bourbon.io](https://bourbon.io/)
* **Compass**: [compass-style.org](https://compass-style.org/)
* **Susy**: [susy.oddbird.net](https://susy.oddbird.net/)
