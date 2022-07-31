---
layout: post
title: "<strong>Sass</strong> vs <strong>SCSS</strong> vs <strong>Less</strong>"
subtitle: "The Sass way"
section: sass
---

Seçmək üçün 2 CSS preprosessoru var:

* **Less** [https://lesscss.org/](https://lesscss.org)
* **Sass** [https://sass-lang.com/](https://sass-lang.com)

Onların hər ikisi bir neçə ildir ki, ortalıqdadır. Bix **Sass** istifadə edəcəyik.

### Sass vs SCSS

Sass-da 2 **sintaksis** mövcuddur:

* **Sass** özü (Sintaktik Awesome StyleSheets) `.sass` fayllarında
* **SCSS** (Sassy CSS) `.scss` fayllarında, bu adi CSS və Sass arasında bir şeydir

Sass və SCSS arasındakı fərq [olduqca incədir](https://sass-lang.com/documentation/file.SASS_REFERENCE.html#syntax).

Remember that:

* Sass preprosessorun adıdır
* SCSS öyrənməyə daha asandır
* internetdəki bütün resurslarda ([The Sass Way](https://github.com/thesassway/thesassway.com) kimi) SCSS deyil, Sass qeyd olunur
* bütün xüsusiyyətlər hər iki sintaksis üçün mövcuddur
* SCSS-dəki hər şey Sass-da mövcuddur

Biz əslində **SCSS** yazacağıq, lakin buna **Sass** deyirik.

### Niyə ilk SCSS

Biz bir neçə səbəbə görə **SCSS** istifadə edəcəyik:

* **readibility**: sintaksis CSS ilə çox oxşardır
* **learning curve**: CSS-in üstünə yalnız bir neçə əlavə xüsusiyyət əlavə edir
* **compatibility**; CSS faylı etibarlı SCSS faylıdır
* **resources**: oxumaq üçün çoxlu onlayn məqalələr və istifadə etmək üçün açıq mənbə kitabxanaları
* **expandibility**: SCSS-dən Sass-a getmək asandır

### Features

Sass-ın təmin etdiyi[^1] budur:

* **variables**: CSS faylınız boyunca `#fce473` təkrarlamaq əvəzinə, sadəcə olaraq bir dəfə `$yellow: #fce473` təyin edin
* **nesting**: CSS qaydaları bir-birinə daxil edilə bilər
* **mixins**: parametrləri qəbul edə bilən və faydasız təkrarların qarşısını alacaq xüsusi funksiyalar
* **extensions**: başqa bir selektorun eyni xassələrini miras almağın asan yolu
* **operators**: `960px / 4` və ya `$space * 2` kimi dəyərləri əlavə etmək/çıxmaq/çoxalmaq/bölmək

### DRY code

Sass haqqında hər şey kodunuzda **özünüzü təkrar etməyin** qarşısını almaq üçün alətlər təmin etməkdir: it's the [DRY principle](https://en.wikipedia.org/wiki/Don't_repeat_yourself), _Özünüzü təkrarlama_ deməkdir.

* **variables** _dəyərlərin_ təkrarlanmasının qarşısını alır
* **nesting** _selektorların_ təkrarlanmasının qarşısını alır
* **mixins** and **extensions** xassələrin təkrarlanmasının qarşısını alır

### Installing Sass

Sass-ı kompüterinizdə quraşdırmaq üçün [https://sass-lang.com/install](https://sass-lang.com/install) linkinə keçid edin.



