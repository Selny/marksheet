---
layout: post
title: "CSS <strong>Priority</strong>"
subtitle: "When several rules <strong>collide</strong>"
section: css
---

HTML elementi **coxlu CSS qaydaları** ilə hədəf alına bilər. Gəlin nümunə üçün kiçik bir paraqraf hazırlayaq:

{% highlight html %}
<p class="message" id="introduction">
  MarkSheet is a free HTML and CSS tutorial.
</p>
{% endhighlight %}

Bu paraqrafı sadəcə onan **teq adından** istifadə etməklə dəyişdirə bilərik:

{% highlight css %}
p{ color: blue;}
{% endhighlight %}

Və ya onun sinif adından istidadə edə bilərik:

{% highlight css %}
.message{ color: green;}
{% endhighlight %}

Və ya onun ID-ni istifadə edə bilərik

{% highlight css %}
#introduction{ color: red;}
{% endhighlight %}

BÇünki brauzer bu paraqrafa tətbiq etmək üçün yalnız **bir rəng** seçə bilər, hansı CSS qaydasının digərlərinə görə **prioritet** tutacağına qərar verməli olacaq. CSS prioriteti budur (və ya CSS _specificity_ haqqındadır).

Nümunəmizdə, paraqraf **qırmızı** olacaq çünki `#id` selektoru digər seçicilərə nisbətən daha _xüsusidir_ və bu səbəbdəndə də daha **əhəmiyyətlidir**.

### CSS qaydalarının sırası

CSS-də oxşar seçicilər varsa, sonuncu müəyyən edilənə üstünlük veriləcək.

{% highlight css %}
p{ color: green;}
p{ color: red;}
/* Paragraphs will be red */
{% endhighlight %}

### 100 əncam

CSS qaydasının nə qədər "güclü" olduğunu anlamaq üçün sürətli bir yol, **selektorların** spesifikliyini ölçməklə olur:

* `#id` selektorları 100 dəyərindədir
* `.class` selektorları 10 dəyərindədir
* `tag` selectorı 1 dəyərindədir

Ən yüksək "bal" toplayan selektor qalib gələcək, _CSS qaydalarının hansı ardıcıllıqla görünməsindən asılı olmayaraq_.

{% highlight css %}
#introduction{ color: red;}
.message{ color: green;}
p{ color: blue;}
{% endhighlight %}

{% highlight html %}
<p class="message" id="introduction">
  MarkSheet is a free HTML and CSS tutorial.
</p>
{% endhighlight %}

<div class="result">
  <p style="color: red;">
    MarkSheet is a free HTML and CSS tutorial.
  </p>
</div>

`#introduction{ color: red;}` qaydası digərlərindən daha çox _spesifikdir_ çünki ID-lər **vahid** olmalıdır, və beləliklə yalnız **bir** elementi hədəfləyə bilər.

`.message{ color: green;}` selektoru`class="message"` attributu ilə hər hansı HTML elementini hədəf ala bilər, və buna görə də daha az spesifikdir. Eyni şey "p{ color: blue;}" üçün də gedir, hansı ki, _istənilən_ HTML paraqrafını hədəfləyə bilər.

### Münaqişələrdən necə qaçmaq olar

CSS yazarkən, **ziddiyyətli qaydalar** yazmaq asandır, burada eyni _xassə_ bir neçə dəfə tətbiq olunur.

Bunun qarşısını almaq üçün:

* ancaq **siniflərdən** istifadə edin: `#introduction` əvəzinə `.introduction` istifadə edin, hətta bu element səhifənizdə yalnız bir dəfə görünsə belə
* sadə HTML elementinizə **çoxlu siniflər* əlavə etməklə qarşısını alın: `<p class="big red important">` kimi yazmayın əksinə `<p class="title">` semanti olaraq hansı daha açıqlayıcıdır
* **daxili stayllardan** istifadə etməyin `<div style="background: blue;">` kimi
