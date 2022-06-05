---
layout: post
title: "<strong>Why</strong> CSS exists"
subtitle: "<strong>Separating</strong> content and styling"
section: css
---

90-cı illərdə İnternet populyarlıq qazandıqca, vebsayta xüsusi dizayn tətbiq etmək nəqsədləri də artdı.. Veb tərtibatçıları veb-səhifələri təkmilləşdirmək üçün xüsusi HTML etiketlərinə etibar edirdilər:

* `<basefont>` büten HTML sənədinə font təyin edir
* `<font>` daxilindəki mətnlər üçün şrift, rəng, və ölçü ölçü təyin edir
* `<center>` bütün məzmununu üfüqi olaraq mərkəzləşdirir
* `<big>` mətnin ölçünü böyüdür
* `<strike>` mətnin üstündən xət çəkir

Bir neçə HTML atributu istifadə oluna bilər:

* `bgcolor` arxxa fon rəngi təyin edir
* `text` mətn rəngi təyin edir
*  elementin her bir tərəfinə boşluqlar əlavə etmək üçün bir çox `margin` atributu isrifadə oluna bilər

### Nə üçün cədvəllərdən qaçınmalı

Ancaq ən cox, sütunlar yaratmaq üçüb, elementləri vizual olaraq tarazlayın, və əsasən elementlərin mövqeləri bir birinə qohumdur, veq tərtibatçılar veb səhifələrini dizayn etmək üçün `<table>` elementindən istifadə edirlər çünki cədvəl vizual olaraq təbii bir **şəbələ** təmin edir:

{% highlight html %}
<table>
  <thead>
    <tr>
      <th>Logo</th>
      <th colspan="2">Tagline</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <th colspan="3">Copyright 2015</th>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Left menu</td>
      <td>Main content</td>
      <td>Right sidebar</td>
    </tr>
  </tbody>
</table>
{% endhighlight %}

Bu yanaşma bir çox səbəbdən çətin idi:

* HTML cədvəlləri **müxtəlifdir** və onlar çoxlu kod tələb edir
* işarələməsi **semantik olaraq yanlışdır**: cədvəllərdən çoxölçele məlumatlar üçün istifadə edilməlidir
* işarələməni dəyişmək üçün tələb olunan tərtibatın dəyişdirilməsi: əgər biz sol sütunu sağa keçirmək istəyiriksə, biz **HTML quruluşunu dəyişməliyik**
* cədvəllər **sintaksis səhvlərinə** meylli idi: sətirlərin və xanaların etibarlı olması üçün müəyyən bir şəkildə sıralanması və iç-içə olması lazımdır
* işarələnməsi **oxunaqlı deyildi**: cədvəllər sütunların içərisində əlavə sütunlar təmin etmək üçün cədvəllərin içərisinə yerləşdirildi

Məhz buna görə cədvəllərin tərtibat məqsədləri üçün istifadəsi yavaş-yavaş tərk edildi və əvəzinə CSS istifadə edildi.

### CSS nədir

**CSS** --> **C**ascading **S**tyle **S**heets. Onun məqsədi işarələmə dillərini dizay etməkdir (HTML və ya XML kimi). Buna gorə də, CSS özlüyündə dəyərsizdir, hər hansı bir HTML sənədi ilə əlaqəsi olmadıqda

CSS HTML sənədinə **həyat** gətirir, fontları seçnəklə, rənglərə müraciət etməklə, səhifənin kənarlarını tayin etməklə, elementləri mövqeləndirməklə, qarşılıqlı əlaqəni canlandırmaqla, və daha çoxunu etməklə.

### CSS necə işləyir

HTML elementlərini seçməklə CSS necə işləyir (paraqraf kimi), dəyişdirmək üçün **xassələrini** seçir (rəng kimi), və müıyyın **dəyərə** müraciət edir (qırmızı kimi):

{% highlight css %}
p{ color: red;}
{% endhighlight %}

_"Stil"_ sözü aldadıcı ola bilər. Siz CSS-i sadəcə mətnlərin rəngini dəyişmək üçün istifadə olunduğunu düşünə bilərsiniz, ölçüsünü, və şriftini. Ancaq CSS HTML sənədinin görünüşünü dəyişmə qabiliyyətinə malikdir, hündürlüyünü təyin etməklə, enini, daxili və xarici səhifə kənarı boşluqlarını, mövqelərini, sütunlarını...
{: .info}

### CSS harada yazılır?

#### CSS atribut kimi

CSS-i birbaşa HTML elementlərinin içərisinə yaza bilərsiniz, `style` attributunu istifadə etməklə:

{% highlight html %}
<p style="color: red;">This text is important.</p>
{% endhighlight %}

#### CSS <head>-in içərisində

HTML sənədinin içərisində `<head>`teqləri arasında `<style>` teqini yazmaqla:

{% highlight html %}
<html>
  <head>
    <title>Hello World</title>
    <style type="text/css">
      p{ color: red;}
    </style>
  </head>
  <body>
    <p>This paragraph will be red.</p>
  </body>
</html>
{% endhighlight %}

#### CSS ayrı bir faylda

`.css` uzantısından istifadə etməklə siz CSS-i ayrı bir faylda yaza bilərsiniz, və HTML `<link>` teqindən istifadə etməklə HTML sənədinizə link edin.

{% highlight css %}
p{ color: red;}
{% endhighlight %}

{% highlight html %}
<html>
  <head>
    <title>Hello World</title>
    <link rel="stylesheet" type="text/css" href="style.css">
  </head>
  <body>
    <p>This paragraph will be red.</p>
  </body>
</html>
{% endhighlight %}

Bu CSS adlandırılan HTML faylıdır, bu halda fayl `style.css` adlandırılır və HTML ilə eyni folderdə yerləşir.

Bu tövsiyyə olunan **3-cü metoddur** ayrı CSS faylı .

### Niyə birbaşa HTML içərisində dizayn etmirik?

Çünki biz **məzmunu** (HTML) onun **təqdimatından** ayırmaq istəyirik (CSS).

Əgər siz bu fərqin məqsədini vizuallaşdırmaq istəyirsinizsə, möcüzəyə doğru irəliləyin [CSS Zen Garden](https://www.csszengarden.com/): hər dizayn _dəqiq_eyni HTML-dən, lakin hər dəfə _fərqli_CSS-dən istifadə edir.

Bu hər sanam **texniki qulluğu** rahatlaşdırır: eyni CSS faylı bütün veb sayt üçün istifadə oluna bilər. bu **eviklik** təmin edir: bir tərəfdən məzmuna diqqət yetirin, digər tərəfdən üslubu. SEO məqsədləri, müxtəlif narahatlıqlar.
