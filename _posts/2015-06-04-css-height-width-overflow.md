---
layout: post
title: "CSS <strong>height</strong> and <strong>width</strong>"
subtitle: "Setting <strong>fixed</strong> dimensions to your rectangles"
section: css
---

Elementin ölçüləri (hündürlüyü və eni) **dinamikdir**, çünki onlar məzmuna uyğunlaşmaq üçün dəyişir. **Xüsusi** ölçüləri təyin etmək bir növ mümkündür.

{% highlight css %}
blockquote{ width: 600px;}
{% endhighlight %}

Blockquote bütün mövcud genişliyi tutmayacaq, lakin **istənilən vəziyyətdə** 600px enində qalacaq::

* brauzer pəncərəsinin eni 600px-dən azdırsa, o, üfüqi sürüşmə çubuğunu göstərəcək
* brauzer pəncərəsi 600px-dən daha genişdirsə, Blockquote 600px enində qalacaq və bütün yeri tutmayacaq

Yalnız eni təyin etdiyimiz üçün Blockquote **hündürlükdə** axıcı olaraq qalır: hündürlükblockquote-nin məzmununa uyğun dəyişən ölçüyə çevrilir.

### Hündürlüyü və eni təyin etmək

Elementin ölçülərini təyin etməklə, məzmununun uzunluğundan asılı olmayaraq sabit qalacaq.

Məzmun elementin ehtiva edə biləcəyindən uzun olarsa nə baş verəcək?
{: .question}

Çünki biz elementin ölçülərini dinamik şəkildə dəyişməsinin qarşısını alırıq, məzmunun elementin ölçülərindən daha uzun olma və sonradan **daşma** ehtimalı var.

Standart davranış təəccüblü ola bilər: məzmun hər halda göstəriləcək!

{% highlight css %}
blockquote{ background: yellow; height: 50px; width: 100px;}
{% endhighlight %}

{% highlight html %}
<blockquote>The content er... finds a way</blockquote>
{% endhighlight %}

<div class="result">
  <blockquote style="background: yellow; height: 50px; width: 100px;">The content er... finds a way</blockquote>
</div>

### CSS overflow

`overflow` CSS xassəsi məzmunun containerdən daha böyük olduğu halları idarə etməyə imkan verir.

default qiyməri `visible`dır: məzmun hər bir halda göstəriləcək, çünki _"Kodda olan məzmunun istifadəçi tərəfindən oxunmamasını niyə istiyə bilərsiniz ki?"_ Siz düşünə bilərsiniz **HTML CSS-dən üstündür**

`overflow: hidden;` tətbiq etməklə, siz sadəcə olaraq hər hansı containerdən daşan məzmunun görünməsini qadağan edirsiniz.

<div class="result">
  <blockquote style="background: yellow; height: 50px; overflow: hidden; width: 100px;">The content er... finds a way</blockquote>
</div>

Məzmununuzun çoxalmasını istəyirsinizsə, lakin yenə də onu əlçatan etmək istəyirsinizsə, `overflow: scroll` verərək scrolbar əlavə etmək qərarına gələ bilərsiniz.

<div class="result">
  <blockquote style="background: yellow; height: 50px; overflow: scroll; width: 100px;">The content er... finds a way</blockquote>
</div>

Ən yaxşı seçim `overflow: auto` istifadə etməkdir, çünki sürüşdürmə çubuqları yalnız məzmun daşsa _görünəcək_, lakin o vaxta qədər gizli qalacaq.

<div class="result">
  <blockquote style="background: yellow; height: 50px; overflow: auto; width: 100px;">The content er... finds a way</blockquote>
</div>

### Sabit ölçülərə diqqət yetirin

Vizual olaraq çəlbedici görünüş əldə etmək üçün spesifik ölçülər təyin etməyə tez tez ehtiyac duyulur lakin gözlənilməz nəticələrə səbəb ola bilər. Bu baxımdan:

* contentinizin daşmadığına əmin olun
* yox əgər daşırsa, dizaynınızın pozulmasının qarşısını almaq üçün `overflow: hidden` və ya `overflow: auto` istifadə edin
