---
layout: post
title: "A <strong>valid</strong> HTML document"
subtitle: "Some boilerplate"
section: html
---

İndiyə qədər, _təcrid olunmuş_ HTML kod fraqmetlərinə baxdıq. Ancaq HTML sənədi (vəya web səhifə, eyni mənaya gəlirlər) **etibarlı** olmaq üçün xüsusi quruluş tələb edir.

HTML sənədini **təsdiqə** nə üçün ehtiyacımız var?

* **düzgün**: etivarlı sənə brauzer tərəfindən _dügün ekrana çıxarılır_
* **sazlama**: etibarsız HTML kodları hədəflənməsi çətin səhvlərə yol aça bilər
* **texniki qulluq**:etibarlı sənədi daha sonra _yeniləmək_ rahat olur, həmçinin başqaları tərəfindən

### Sənəd növü

İlk təmin olunacaq məlumat HTML sənədini növünü yazırıq: **Sənəd növü**.

Doctipi illərdir gələn avtomobil versiyası kimi düşünə bilərsiniz: 1984-da alınan Ford Fiesta Fiesta 2 idi. bu gün bir eded alsanız, bu Fiesta 7 olacaq.

Əvvəllər HTML-nin bir neçə versiyası var idi (XHTML və HTML 4.01 standartlarla rəqabət aparırdılar). Bu günlərdə, **HTML 5** normadır.

Brauzerə HTML sənədinin HTML 5 olduğunu demək üçün, sadəcə sənədinizi göstərildiyi şəkildə yazmağa başlayın:

{% highlight html %}
<!DOCTYPE html>
{% endhighlight %}

Budur. Sadəcə yazın və artıq unudun.

Bu HTML 5 sənədinin niyə 5 reqemi ile ni qey olunamamğı sizi narahat edə bilər. W3C əvvəlki doktip təriflərinin çox qarışıq olduğunu düşündü və HTML versiyası haqqında hər hansı qeydi silməklə onu sadələşdirmək fürsətindən istifadə etdi.
{: .info}

### <html> elementi

doctype sətrində ayrı olaraq, **bütün** HTML sənədləri `<html>` elementi ilə əhatə olunmalıdır

{% highlight html %}
<!DOCTYPE html>
<html>
  <!-- The rest of your HTML code is here -->
</html>
{% endhighlight %}

`<html>` elementi texniki olaraq bütün HTML elementlərini əcdadıdır..

### <head>

Eyni şəkildə atributlar HTML elementi üçün əlavə məlumat daşıyır, `<head>` elementi bütöv veb səhifə üçün əlavə məlumatlar daşıyır.

Məsələn, veb səhifənin **başlığı** (tabda görünür) `<head>` elementini içərisində yerləşir:

{% highlight html %}
<head>
  <title>MƏnim möhtəşəm bloqum</title>
</head>
{% endhighlight %}

Başqa HTML elementləridə `<head>` elementinin içərisində görünə bilər, və _ancaq_ `<head>`-də:

* `<link>`
* `<meta>`
* `<style>`

### <body>

`<head>` elementi sadəcə içərisində metadata saxlayırsa və heç bir yerdə çap olunmayacaqsa (`<title>` elementindən başqa), `<body>` elementi bizim içərisini bütün məzmunu yazacağımız elementdir. `<body>`-in _içərisindəki_ hər şey brauzerdə görünəcəkdir

### Tamamilə etibarlı HTML sənədi

Bu tələblərin hər birini özündə birləşdiri, biz sadə və etibarlı bir HTML sənədi yaza bilərik:

{% highlight html %}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>MarkSheet</title>
    <meta name="description" content="A simple HTML and CSS tutorial">
  </head>
  <body>
    <p>Hello World!</p>
  </body>
</html>
{% endhighlight %}

Əgər bu nümunəni brauzerinizdə görürsünüzsə, ki, görəcəksiniz:

* _"MarkSheet"_ brauzerdə tabda görünəcək
* _"Hello World!"_ pəncərədə görünəcək tək mətn olacaq, `<body>`-in _içərisindəki_ yeganə məzmundur

<p>The <abbr title="World Wide Web Consortium">W3C</abbr> provides a <a href="https://validator.w3.org/#validate_by_input">Markup Validation Service</a> to check any HTML document for errors and warnings.</p>
