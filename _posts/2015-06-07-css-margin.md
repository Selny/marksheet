---
layout: post
title: "CSS <strong>margin</strong>"
subtitle: "To <strong>push away</strong> your neighbours"
section: css
---

Əgər padding elementin _içinə_ boşluq əlavə edirsə (borderi ilə contenti arasına), margin elementin _çöıünə_ yəni element ilə _başqa element_ arasına boşluq əlavə edir.

{% highlight html %}
<p>Hey, you know what sucks?</p>
<p>vaccuums</p>
<p>Hey, you know what sucks in a metaphorical sense?</p>
<p>black holes</p>
<p>Hey, you know what just isn't cool?</p>
<p>lava?</p>
{% endhighlight %}

<div class="result">
  <p>Hey, you know what sucks?</p>
  <p>vaccuums</p>
  <p>Hey, you know what sucks in a metaphorical sense?</p>
  <p>black holes</p>
  <p>Hey, you know what just isn't cool?</p>
  <p>lava?</p>
</div>

{% highlight css %}
p{ margin: 40px;}
{% endhighlight %}

<div class="result">
  <p style="margin: 40px;">Hey, you know what sucks?</p>
  <p style="margin: 40px;">vaccuums</p>
  <p style="margin: 40px;">Hey, you know what sucks in a metaphorical sense?</p>
  <p style="margin: 40px;">black holes</p>
  <p style="margin: 40px;">Hey, you know what just isn't cool?</p>
  <p style="margin: 40px;">lava?</p>
</div>

### Merging vertical margins

Gəlin title və subtitle üzərində izah edək.

{% highlight css %}
.title{ margin-bottom: 30px;}
.subtitle{ margin-top: 15px;}
{% endhighlight %}

{% highlight html %}
<h1 class="title">MarkSheet</h1>
<h2 class="subtitle">A simple HTML/CSS tutorial</h2>
{% endhighlight %}

<div class="result">
  <h1 style="margin: 0 0 30px;">MarkSheet</h1>
  <h2 style="margin: 15px 0 0;">A simple HTML/CSS tutorial</h2>
</div>

Bu bölmənin başlığı cavaba işarə edə bilər, iki element arasındakı sərhəd `45px` deyil `30px` olacaq.Çünki bir-birinə "toxunan" kənarlar bir-biri ilə **birləşəcək**.

#### "That's weird!"

Siz elementin marginini onun digər elementlərdən _uzaqda qalmaq istədiyi **minimum boşluq** kimi də hesab edə bilərsiniz.

Bu biraz elementin: "Ok, mən növbəti elementin məndən _ən azı_ 30px uzaqda olmasını istəyirəm. Əgər daha çoxdursa, niyə də olmasın. Amma ən azı 30px zəhmət olmasa!" deməsinə bənzəyir

### margin və padding arsında seçim

Çətin sual. Bu sual nə border nə də background verilmədikdə ortaya çıxır. Doğrudan da: Əgər ya border yada background verilmiş olsa o zaman vizual render fərqli olacaq. Amma əgər heç biri yoxdursa, və nəzərə alsaq ki, margin və padding transparenrdir(şəffaf) nəticə eyni olcaq.

Əvvəlcə dəqiqləşdirməlisiniz elementləri bir birindən nəyə görə ayırırsınız. Daxili məzmunun daha çox nəfəs almasına icazə verməkdir? Yoxsa bütün elementin daha çox nəfəs almasına icazə verməkdir? Bu, birinci halda padding, ikinci halda margindir.

Həmçinin, kənarların necə **birləşə biləcəyini** nəzərə alaraq.
