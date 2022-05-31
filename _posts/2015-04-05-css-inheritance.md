---
layout: post
title: "CSS <strong>Inheritance</strong>"
subtitle: "Using the HTML <strong>hierarchy</strong>"
section: css
---

Tutaq ki, biz veb-səhifənin **mətn rəngini** dəyişmək istəyirik. Hər HTML elementi üçün rəng təyin etmək yorucu olardı:

ul,
ol,
li,
h1,
h2,
h3,
h4,
h5,
h6{ color: grey;}

### Value propagation(Dəyər artımı,yayılması)

body{ color: grey;}

Body daxilində olan butun yazıların rəngi **grey** olacaqdır.


Biz `html` teqindən də istifadə edə bilərik.{: .info}

### Inherited properties(İrsi xüsusiyyətlər)

Yalnız bir neçə CSS xassələri miras ala bilər. Onlar əsasən **mətn** xassələridir:

* text color
* font (family, size, style, weight)
* line-height

Bəzi HTML elementləri miral almır. Məsələn, keçidlər `color` xassəsini miras qoymur.
