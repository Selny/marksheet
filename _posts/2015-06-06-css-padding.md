---
layout: post
title: "CSS <strong>padding</strong>"
subtitle: "To give <strong>space</strong> to your inner content"
section: css
---

**padding** elementin _sərhədləri_ və _məzmunu_ arasındakı boşluqlardır.

Boşluqların miqdarı istənilən [size units](css-size-units.html)-dən istifadə etməklə müəyyən edilə bilər.

{% highlight css %}
blockquote{ padding: 20px;}
{% endhighlight %}

Borderlərdə olduğu kimi, paddin də istənilən 4 tərəfdən fərdiləşdirilə bilər

{% highlight css %}
blockquote{ padding-bottom: 20px;}
{% endhighlight %}

Doldurma _sərhəd_ və _məzmun_ arasında ** olduğundan, tətbiq olunan inner spacei border ilə vizuallaşdırmaq daha asandır:

{% highlight css %}
blockquote{ background: yellow; border: 1px solid blue;}
{% endhighlight %}

<div class="result">
  <blockquote style="background: yellow; border: 1px solid blue;">
    Good night, good night! Parting is such sweet sorrow, that I shall say good night till it be morrow.
  </blockquote>
</div>

Padding əlavə etmək textual content ilə border arasını boşluq ilə təmin edəcək:

{% highlight css %}
blockquote{ background: yellow; border: 1px solid blue; padding: 20px;}
{% endhighlight %}

<div class="result">
  <blockquote style="background: yellow; border: 1px solid blue; padding: 20px;">
    Good night, good night! Parting is such sweet sorrow, that I shall say good night till it be morrow.
  </blockquote>
</div>

Elementin backgroundunun borderlərinə qədər necə uzandığına diqqət yetirin. Paddingin tətbiqi bu backgroundu genişləndirməyə imkan verir
