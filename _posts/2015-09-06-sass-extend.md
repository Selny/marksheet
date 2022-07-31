---
layout: post
title: "Sass <strong>extend</strong>"
subtitle: "Sharing common properties"
section: sass
---

### Ümumi xassələri

Bəzən fərqli CSS qaydaları üzrə **eyni xassələr coxlugunu** yazırsınız.

  Məsələn, tutaq ki, dizaynınız səhifə boyu **kiçik aralı böyük hərflərdən** istifadə edir: buttons, naviqasiya barı, yan panel başlıqları, tablar...

Buna bənzər:

<div class="result">
  <p style="color: lightslategrey; font-size: 10px; letter-spacing: 0.1em; line-height: 12px; text-transform: uppercase;">Kiçik məzafəli böyük hərflər</p>
</div>

Yazdiğiniz CSS nece görünəcək? You could:

* use a common CSS **class** like `.small-uppercase`
* operatorları**birləşdirin**
* Sass **uzatmasinadan** istifadə edin

#### Ümumi CSS Sinfi

{% highlight css %}
.small-uppercase{
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}
{% endhighlight %}

`.small-uppercase`-in olması CSS qaydalarına görə **semantik olaraq səhvdir** çünki HTML-ni `<p class="small-uppercase">` kimi yazırsınız və bu, əsasən HTML daxilində _yazma_ üslublarına uyğun gəlmir.

#### Seçiciləri Birləşdirin
Çünki CSS qaydaları _seçicilərin_ nömrələrini qəbul edirs, paylaşılan bütün xassələri seçicilərin **siyahısı** altında birləşdirə bilərsiniz:

{% highlight css %}
.button,
.navigation a,
.sidebar h3,
.tabs a{
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}
{% endhighlight %}

Bu yaxınlaşma **semantik olaraq doğrudur** çünki hər bir seçici HTML elementini təsvir edir və bağlıdırlar.

Lakin, iki problem var:

* seçicilərin siyahısı böyüdükcə bu CSS qaydası idarəolunmaz hala gələ bilər
* çünki hər bir seçicinin özünəməxsus qaydaları var, siz xassələr coxlugunu **iki** hisseye ayirirdiniz (`.button` CSS-in daha aşağı hissələrində əlavə qaydalara malik ola bilər)

Sass bu problemləri həll etməyə bizə komək edir.

### Sass @uzanti sintaksis

Sass `@uzantısı` CSS xassələrini _başqa_ **selektor**-dan **miras almağa** imkan verir:

{% highlight scss %}
// scss
.small-uppercase{
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}

.modal-background{
  @extend .small-uppercase;
}

.product-link{
  @extend .small-uppercase;
}

.image-pattern{
  @extend .small-uppercase;
}

// generated css
.small-uppercase,
.modal-background,
.product-link,
.image-pattern{
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}
{% endhighlight %}

`@uzantı`ümumi xassələri **list** seçicisi atinda yenidən quruplaşdıracaq.

Bu siyaı çox asanlıqla **saxlanıla biləndir** çünki seçiciləri sadəcə bir bir əlavə edirsiniz, və birbaşa əlaqəli seçicinin içərisinə.

HTML-niz **semantik** qalır çünki her element özünün təsviri sinif adını saxlayır.

### Qarşılıqlı fərqlər

_"Gözləyin, o zaman miksinlər kimi deyilmi?"_ deyə düşünürsünüz?

Aralarında 2 fərq var:

* `@uzanti` qaydasının parametrləri yoxdur. Miksinlərin isə var.
* `@uzantı` qaydası seçiciləri birləşdirir. Miksinlər isə xeyir.

Gəlin [overlay mixin](/sass-mixins.html#syntax) -zi yenidən istifadə edək, və həmçinin `.small-uppercase` qaydasını yazaq:

{% highlight scss %}
// scss
@mixin small-uppercase() {
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}

.modal-background{
  @include small-uppercase();
}

.product-link{
  @include small-uppercase();
} 

.image-pattern{
  @include small-uppercase();
}

// generated css

.modal-background{
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}

.product-link{
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}

.image-pattern{
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}
{% endhighlight %}

Xassələr siyahısı çağırılan `@include small-uppercase()` kimi sadəcə bir neçə dəfə **təkrarlanır**.

Bu səbəbdən Sass `@uzantısı` cox **səmərəlidir**, 
A Sass `@extend` is more **efficient**, çünki yalnız ümumi xassələri **bir dəfə** yazır.

### Placeholders(Yer Tutucular)

Siz düşünə bilərsiniz ki, _".kiçik-böyük hərf' semantik deyil! Mən onu HTML-də istifadə edə bilərdim!"_?

Bəli haqlısınız, və bu səbəbdən Sass-da **placeholders(Yer Tutucular)** mövcuddur.

Əgər istəmirsinizsə və ya `.small-uppercase` seçicisinə ehtiyacınız varsa, onu **Sass placeholder**-ə **percentage sign** `%`-dən istifadə etmədən çevirə bilərsiniz:

{% highlight scss %}
// scss
%small-uppercase{
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}

.modal-background{
  @extend %small-uppercase;
}

.product-link{
  @extend %small-uppercase;
}

.image-pattern{
  @extend %small-uppercase;
}

// generated css
.modal-background,
.product-link,
.image-pattern{
  color: lightslategrey;
  font-size: 10px;
  letter-spacing: 0.1em;
  line-height: 12px;
  text-transform: uppercase;
}
{% endhighlight %}

Qeyd edək ki, yaradılmış CSS `.small-uppercase` **seçicisini artıq q
bul eləmir**. Çünki `%small-uppercase` qaydası ancaq ümumi xassələrin yerini təmin etmək üçün var.

### Uzatma, yer tutucular və qarışıqlar arasındakı fərq

<div class="table">
  <table>
    <tr>
      <th class="empty"></th>
      <th>Definition</th>
      <th>Referencing</th>
      <th>Combines selectors?</th>
      <th>Allows parameters?</th>
      <th>Can be used on its own?</th>
    </tr>
    <tr>
      <th>Mixins</th>
      <td><code>@mixin name()</code></td>
      <td><code>@include name()</code></td>
      <td class="no">No</td>
      <td class="yes"><span>Yes</span></td>
      <td class="no">No</td>
    </tr>
    <tr>
      <th>Extensions</th>
      <td>Any class</td>
      <td><code>@extend .class</code></td>
      <td class="yes"><span>Yes</span></td>
      <td class="no">No</td>
      <td class="yes"><span>Yes</span></td>
    </tr>
    <tr>
      <th>Placeholders</th>
      <td><code>%placeholder</code></td>
      <td><code>@extend %placeholder</code></td>
      <td class="yes"><span>Yes</span></td>
      <td class="no">No</td>
      <td class="no">No</td>
    </tr>
  </table>
</div>

Şübhə olduqda, **mixins** istifadə edin. Onlar çoxlu CSS sətirlərini yaradır və uzatma/yer tutuculardan daha az zərifdir, lakin onlar düzdür.
