---
layout: post
title: "CSS <strong>responsiveness</strong>"
subtitle: "Designing for every screen"
section: css
---

Veb, məlumatın hansı **cihazda** baxılmasından asılı olmayaraq, İnternetdə asanlıqla məlumat mübadiləsi üçün platforma təmin etmək üçün nəzərdə tutulub. İnternetə daxil olan kompüterlər arasındakı yeganə fərqlər əsasən fərqli ekran qətnamələrindən ibarət olsa da, **mobil cihazların** sürətli inkişafı tələbləri dəyişdi: bir veb saytın müvafiq olması üçün mobil cihazlarda əlçatan olmalıdır.

Mobil cihazları idarə etmək üçün hansı seçimlər mövcuddur?

1. **Heç bir şey etməyin** və mobil istifadəçilər saytınızdakı məlumatı oxumaq üçün böyütsün.
1. **ikinci** vebsayt yaradın, [m.facebook.com](https://m.facebook.com/) kimi, və mobil cihazları həmin vebsayta yönləndirin
1. **responsive web design**-dan istifadə edin

### Device, browser, viewport

Daha irəli getməzdən əvvəl bəzi terminləri müəyyənləşdirməliyik:

device
: istifadə olunan aparat: smartphone, tablet, pc or laptop

browser
: istifadə olunan proqram: Firefox, Google Chrome, Safari, Internet Explorer

viewport
: brauzer daxilində veb səhifəni həqiqətən göstərən bölgə

![device, browser, və viewport arasındakı fərq](/images/device-browser-viewport.png)

### Responsive web design

**responsive web design**-ın ideyası veb saytınızı **istənilən cihaza uyğunlaşdırmaqdır**. Bunu CSS-nizlə cihazları **hədəfləmək** və bu cihazlarda _yalnız_ müəyyən üslubları tətbiq etməklə edir.

Responsiveness **cihazın** və ya **görüntü pəncərəsinin** xüsusiyyətlərindən asılıdır. Məsələn:

* viewport nə qədər **enlidir**?
* viewport nə qədər **yüksəkdir**?
* how is the viewport **oriented**?
* what is the device's **resolution**?

Bu sualların cavabından asılı olaraq, cavab verən CSS fərqli və ya əlavə CSS qaydaları tətbiq edəcək.

İndiyə qədər, CSS-nin hər bir hissəsi veb səhifəmizə daxil olan hər bir cihaz tərəfindən istifadə edilmişdir. Cavab verən veb dizayn _müəyyən_ hallarda _müəyyən_ üslubları tətbiq etməyə imkan verir.

### media queries

Biz CSS-də yalnız həmin blokun meyarlarına uyğun gələn cihazlar tərəfindən istifadə olunacaq **bloklar** yazmalıyıq. Bu bloklar **media querielər** adlanır.

Media querylərin sintaksisi [animasiya keyframelərin sintaksisini] xatırladır.(/css-animations.html#keyframes), o, **CSS daxilindəki bloku** müəyyən etdiyinə görə, yazdığınız əlavə CSS qaydaları _yalnız müəyyən hallarda tətbiq olunur_.

{% highlight css %}
/* This part is read by every device/viewport */
body{ font-size: 14px;}

@media (min-width: 1200px) {
  /* This part is only read by viewports wider than 1200 pixels */
  body{ font-size: 16px;}
}
{% endhighlight %}

Burada standart mətn ölçüsü `14px`-dir. Lakin daha böyük görünüş portlarını yerləşdirmək üçün, görünüş pəncərəsi **1200 piksel**-dən _daha genişdirsə, mətn ölçüsü `16px` olaraq təyin edilir.

Unutmayın ki, söhbət cihazın yox, **görüntü portundan** gedir.

Mobil cihazlarda brauzerlərin tam ekran rejimində işlədiyini nəzərə alsaq, iki genişlik bir-birini əvəz edə bilər. Əgər masaüstünüzdəsinizsə, media sorğularının aktivləşdirildiyini/deaktiv edildiyini görmək üçün brauzerinizin pəncərəsinin ölçüsünü dəyişdirin.

#### Several parameters

Media sorğusunun aktivləşdirilməsi üçün **2 şərt** tələb edə bilərsiniz.

{% highlight css %}
body{ font-size: 18px;}

@media (min-width: 1000px) and (orientation: landscape) {
  body{ font-size: 20px;}
}
{% endhighlight %}

Şrift ölçüsü yalnız görünüş pəncərəsi ən azı _1000px enində_ **və** _landşaft_ rejimində olduqda (portret rejimindən fərqli olaraq) '20px' olaraq təyin ediləcək.

Həmçinin `not` və `only` istifadə edə bilərsiniz. Bunlara [məntiqi operatorlar](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Media_queries#Logical_operators) deyilir.
{: .info}

#### Several CSS rules

Media sorğusuna istədiyiniz qədər **CSS qaydaları** daxil edə bilərsiniz. 

{% highlight css %}
body{ font-size: 14px;}
.button{ display: block;}
.title{ text-align: center;}

@media (min-width: 1200px) {
  body{ font-size: 16px;}
  .container{ margin: 0 auto; width: 960px;}
  .button{ display: inline-block;}
  .title{ text-align: left;}
}
{% endhighlight %}

### Parameters

Media sorğuları **conditions** kimi fəaliyyət göstərən **parametrlər** tələb edir ki, onlar media sorğusunun **aktivləşdirilməsi** üçün doldurulmalıdır.

`@media (min-width: 1200px)` yazaraq, biz brauzerə deyirik ki, bu bloku _yalnız baxış pəncərəsi 1200px-dən daha geniş olarsa oxusun.

#### width

**width** parametri responsive veb dizaynda ən çox istifadə edilən parametrdir. Bu, **veb-səhifələrin şaquli oxunmağından irəli gəlir**: gizli məzmunu oxumaq üçün sürüşdürürük. Nəticədə veb-saytın hündürlüyü dəyişkən olsa da, eni sabit və məhduddur.

Çünki biz (adətən) üfüqi olaraq sürüşmürük, dizaynımızı **mövcud baxış pəncərəsi eni** daxilində uyğunlaşdırmalıyıq. Media sorğuları bu genişlikdə **yoxlamalar** həyata keçirməyə imkan verir, və əgər görüntü pəncərəsi müəyyən piksel miqdarından _geniş (`min-en`) və ya _dar_(`maksimum-en`) olarsa, müəyyən üslubları tətbiq edin.

You can use either:

* `min-width(960px)`: üslublar yalnız görünüş pəncərəsi 960px-dən _daha geniş olduqda tətbiq olunacaq
* `max-width(768px)`: üslublar yalnız görünüş pəncərəsi 768px-dən daha dar olduqda tətbiq olunacaq

Bu parametirlər **pixels**, **ems** və **rems** qəbul edirlər.

Baxış pəncərənizin ölçüsünü hər dəfə dəyişdirdiyiniz zaman brauzer CSS-də genişlik parametrlərini ehtiva edən media sorğuları üçün yoxlayır və buna uyğun olaraq üslublarını tətbiq edir.

#### height

**height** parametri width kimi işləyir, o baxış pəncərəsinin hündürlüyündə yoxlama aparacaq.

`min-height` və `max-height` istifadə edə bilərsiniz.

O, nadir hallarda istifadə olunur, çünki veb-saytlar əsasən **şaquli yöndə** sürüşdürülür və nadir hallarda onların dizaynını daha qısa baxış pəncərələri üçün uyğunlaşdırmaq lazımdır.

#### orientation

**orientation** parametri baxış pəncərəsinin aşağıdakı rejimlərdən birində olub-olmadığını aşkar edir:

* **landscape**: baxış pəncərəsi hündürlüyündən **daha genişdir**
* **portrait**: baxış pəncərəsi genişliyindən **daha uzundur**

{% highlight css %}
@media (orientation: portrait) {
  /* For vertical viewports */
}

@media (orientation: landscape) {
  /* For horizontal viewports */
}
{% endhighlight %}

Daha çox planşet və smartfonlar üçün istifadə olunmasına baxmayaraq, Nəzərə alın ki, hətta geniş ekranlı monitorda, eni hündürlüyündən kiçik olarsa, görüntü pəncərəsi portretdə ola bilər.

Mobil telefonda, hətta cihazınızı portret rejimində saxlasanız belə, klaviatura görünsə, hündürlüyünün enindən necə kiçildiyini nəzərə alaraq görüntü pəncərəsi landşaft kimi qəbul edilə bilər.
{: .info}

#### resolution

**resolution** parametri **cihazın piksel sıxlığına** uyğundur, və ya hər düym üçün nöqtə `dpi` və ya hər santimetr üçün nöqtə `dpcm` ilə ifadə oluna bilər.

It depends on:

* **resokution**-iz nədir (məsələn, 1440x900, 1280x800, 1024x768 və s.)
*ekranınızın **diaqonalı** nədir ( 11,6'', 14'', 21'' və s. kimi)

Piksel sıxlığı əsasən ekranınızın necə **kırtıl** olduğunu bildirir (dpi nə qədər yüksəkdirsə, ekran daha kəskin olur).

{% highlight css %}
@media (min-resolution: 300dpi) {
  /* */
}
{% endhighlight %}

İş masası ekranları adətən **100** dpi ətrafında piksel sıxlığına malikdir. Digər tərəfdən smartfonların [inanılmaz dpi diapazonu](https://dpi.lv/) var. Məsələn:

* **Nokia Lumia 640**: 332dpi
* **Apple iPhone 6+**: 401dpi
* **Google Nexus 5**: 445dpi
* **HTC One**: 469dpi
* **Samsung Galaxy S6**: 577dpi

CSS burada hansı rol oynayır? yüksək resolutionlu ekranlar mətni daha aydın render edəcək: individual piksellər çətin nəzərə çarpır və hərflər tamamilə hamar görünür.

Problem, məsələn, Retina displeylərindəki **şəkillərlə**dir.Bu uzun bir mövzudur, buna görə də bunu oxuyun [sitepoint-də "Retina Ekranları üçün CSS Texnikaları" məqaləsi](https://www.sitepoint.com/css-techniques-for-retina-displays/).

<figure markdown="1">
![Image density in CSS](/images/image-density-in-css.png)
<figcaption markdown="1">
Source: [sitepoint.com](https://www.sitepoint.com/css-techniques-for-retina-displays/)
</figcaption>
</figure>

İstifadə nümunəsi hər bir cihaz üçün defolt fon təsviri təqdim etmək və Retina displeylərində **yüksək resolutiona malik fon şəkillərini** tətbiq etmək olar.

{% highlight css %}
/* 40x40 logo */
.logo{ background-image: url(marksheet-logo.png); background-size: 40px 40px;}

@media (min-resolution: 300dpi) {
  /* 80x80 logo resized to 40x40 */
  .logo{ background-image: url(marksheet-logo@2x.png);}
}
{% endhighlight %}

Unutmayın ki, **fon ölçüsü təyin edilməlidir**. Əks halda, `@2x` Retina şəkli iki dəfə yer tutacaq.

`@2x` şəkilçisi yalnız Apple-ın Retina şəkilləri üçün qeydidir və CSS-də _de facto_ default notation kimi qəbul edilmişdir.
{: .info}

### Mobile-first or desktop-first

Adətən, siz əvvəlcə tam eni **desktop** versiyasına diqqət yetirmək istəyirsiniz, çünki o, columns, hover states, absolute positioning, floats və s. daxil olan daha mürəkkəb dizayna malikdir.

Lakin əvvəlcə **mobil** versiyasını tərtib etmək **["HTML qutudan demək olar ki, 100% cavab verir"](https://fluidity.sexy/) nəzərə alınmaqla əslində daha asandır **. Mobil cihazlarda əksər veb dizaynlar yalnız şaquli planlara diqqət yetirir, sütunlar yoxdur və ya çox azdır, çünki sürüşmə mobil cihazlarda **təbii**dir.

[The Flow](/css-the-flow.html) istifadə etmək mobil saytın dizaynını sadələşdirir: sadəcə HTML elementlərinizi onların göstərilməsini istədiyiniz şəkildə sifariş edin. Sadəcə olaraq HTML kodunuzu yazmaqla siz _artıq mobil vebsaytınızı dizayn edirsiniz_. Əvvəlcə başlıq, sonra menyu, sonra məzmununuz və sonunda altbilgi. _Voilà_!

Mobil ilk CSS, daha böyük baxış pəncərələri üçün xüsusi qaydaları tətbiq etmək üçün "min-width" media sorğularından istifadə edərdi:

{% highlight css %}
/* General CSS rules for every viewport, including smartphones */
body{ }
.title{ }
.button{ }

@media (min-width: 768px) {
  /* Rules for tablets and bigger viewports */
}

@media (min-width: 992px) {
  /* Rules for laptops, small desktop screens and bigger viewports */
}

@media (min-width: 1200px) {
  /* Rules for larger desktop screens only */
}
{% endhighlight %}

A desktop-first approach starts with styles for large screens and  `max-width` media queries in order to apply specific rules for smaller viewports:

{% highlight css %}
/* General CSS rules for every viewport, including large desktop screens */
body{ }
.title{ }
.button{ }

@media (max-width: 1199px) {
  /* Rules for laptops, small desktop screens, and smaller viewports */
}

@media (max-width: 991px) {
  /* Rules for tablets and smaller viewports */
}

@media (max-width: 767px) {
  /* Rules for smartphones only */
}
{% endhighlight %}

Notice how the desktop-first `max-width` values are _1 fewer than_ the mobile-first `min-width`. For example:

* `@media (min-width: 768px)` targets tablets
* `@media (max-width: 767px)` doesn't target tablets


