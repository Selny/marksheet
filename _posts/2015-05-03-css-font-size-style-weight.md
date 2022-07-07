---
layout: post
title: "CSS <strong>font properties</strong>"
subtitle: "For <strong>bold</strong> and <em>italic</em> text"
section: css
---

### font-size

Biz artıq **[CSS size units](/css-size-units.html)**-ı qavradıq, başqa başqa şeylər arasında şrift ölçüsünü təyin etmək üçün istifadə olunur.

{% highlight css %}
p{ font-size: 16px;}
{% endhighlight %}

Nəzərə alın ki, `16px` şrift ölçüsünün təyin edilməsi hər bir hərfi `16px` yüksək etməyəcək. Hər hərfin _faktiki_ ölçüsü istifadə olunan şrift ailəsindən asılıdır.

### font-style

Bu xassə mətninizi _italic_ edə bilər:

{% highlight css %}
h2{ font-style: italic;}
{% endhighlight %}

Default dəyər: `font-style: normal;`.

Başqa mümkün dəyər isə `oblique` ancaq heç vaxt istifadə olunmur.

### font-weight

Bu xassə mətninizi **qalın** edə bilər:

{% highlight css %}
h2{ font-weight: bold;}
{% endhighlight %}

Default dəyər: `font-weight: normal;`.

İstifadə olunan `font-family`-dən asılıdır, bir neşə srift dəyəri mövcuddur,  `100` dən `900`-a qədər:

{% highlight css %}
font-weight: 100; /* Thin */
font-weight: 200; /* Extra Light */
font-weight: 300; /* Light */
font-weight: 400; /* Which is like font-weight: normal; */
font-weight: 500; /* Medium */
font-weight: 600; /* Semi Bold */
font-weight: 700; /* Which is like font-weight: bold; */
font-weight: 800; /* Extra Bold */
font-weight: 900; /* Ultra Bold */
{% endhighlight %}

Çox az srift 9 dəyərin hər birini ehtiva edir. [Exo font](https://www.google.com/fonts/specimen/Exo) bunlardan biridir.

 400 (normal) və 700 (bold) kimidə görə bilərsiniz, və bəzən 300 (light) və 500 (medium).

### font-variant

Bu xassə mətninizi kiçik hərflərə çevirir:

{% highlight css %}
h2{ font-variant: small-caps;}
{% endhighlight %}

Default dəyəri: `font-variant: normal;`.

Geniş istifadə olunan xassə deyil.
