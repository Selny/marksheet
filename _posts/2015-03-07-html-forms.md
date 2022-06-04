---
layout: post
title: "HTML <strong>Forms</strong>"
subtitle: "To make a page <strong>interactive</strong>"
section: html
---

Səhifə naviqasiya edilərkən, istifadəcilərin qarşılıqlı əlaqəsi sadəcə **linklərin** üzərinə tıklamaqdan ibarət olmalıdır.

Ancaq internet başa düşür ki, bəzən istifadıçilərdən onların girişinin təmin etmək tələb olunur. Bu tip qarşılıqlı əlaqələrə daxildir:

* qeydiyyatdan keçmək və vebsayta daxil olmaq
* şəxsi məlumatlarını daxil etmək (ad, adres, kredit kartı məlumatları...)
* məzmunun filtirlənməsi (dropdownlar istifadə etməklə, checkboxelar...)
* axtarış həyata keçirməklə
* fayllar yükləmək

Bu tələbləri yerləşdirmək üçün, HTML interaktiv **form controls** təmin edir:

* mətn daxiletmələri (bir və ya bir neçə sətir üçün)
* radio düymələr
* checkboxlar
* dropdownlar
* widgetlər yükləmək
* təsdiq buttonləri

Bu kontrollar **fərqli** HTML teqləri istifadə edir, ancaq əksəriyyəti `<input>` teqindən istifadə edirlər. Çünki bu öz-özünə bağlanan teqdir, inputların _tipi_ onların `input` atributu ilə təyin olunur: 

{% highlight html %}
<!-- A text input -->
<input type="text">
<!-- A checkbox -->
<input type="checkbox">
<!-- A radio button -->
<input type="radio">
{% endhighlight %}

<div class="result">
  <input type="text">
  <br>
  <input type="checkbox">
  <br>
  <input type="radio">
</div>

### Form elementi

<form>` elementi blok elementdir vebsəhifənin **interaktiv** hissəsi kimi təyin olunur. Nəticə etibarilə, bütün form kontrollar ( `<input>`, `<textarea>` və ya `<button>` kimi) `<form>` elementinin içərisində yerləşməlidir.

İki HTML atributu tələb olunur:

* `action` form məlumatlarının hansı adresə gondəriləcəyini özündə saxlayır
* `method` GET və ya POST metodlarından biri ola bilər, və məlumatların necə gondəriləcəyini təyin edir

Adətən, form məlumatları **serverə** göndərilir. Bu məlumatların _necə_ işlənəcəyi bu təlimatın əhatəsindən çıxır.

Sadə əməliyyatları həyata keçirilməsi üçün nəzərdə tutulmuş birlikdə işləyən giriş kontrollarının yığımı kimidə fikirləşə bilərsiniz. Əgər siz giriş formu yazmısınızsa, **3** kontroleriniz ola bilər:

* email girişi `<input type="email">`
* şifrə girişi `<input type="password">`
* təsdiq ddüyməsi `<input type="submit">`

Bu 3 HTML teqi `<form action="/login" method="POST">`elementinin içərisində bağlıdır.

Qeydiyyat səhifəsinidə siz həmin HTML səhifəsinin içərisində yaza bilərsiniz, aprı `<form>` elementinin içərisində.

### Mıtn inputları

Demək olar ki, bütün `inputlar` istifadəçidən mətn daxil edilməsini tələb edir, adlarını daxil etmələri üçün, email, şifrə, adres... Mətn form kontrollerlər müxtəlif versiyalarda olur:

<div class="table">
  <table>
    <tr>
      <th>Text</th>
      <td><code>&lt;input type="text"&gt;</code></td>
      <td><input type="text"></td>
      <td>Allows any type of character</td>
    </tr>
    <tr>
      <th>Email</th>
      <td><code>&lt;input type="email"&gt;</code></td>
      <td><input type="email"></td>
      <td>Might display a warning if an invalid email is entered</td>
    </tr>
    <tr>
      <th>Password</th>
      <td><code>&lt;input type="password"&gt;</code></td>
      <td><input type="password"></td>
      <td>Shows dots as characters</td>
    </tr>
    <tr>
      <th>Number</th>
      <td><code>&lt;input type="number"&gt;</code></td>
      <td><input type="number"></td>
      <td>Up/Down keyboard keys can be used</td>
    </tr>
    <tr>
      <th>Telephone</th>
      <td><code>&lt;input type="tel"&gt;</code></td>
      <td><input type="text"></td>
      <td>Can trigger an autofill</td>
    </tr>
    <tr>
      <th>Multiple line text</th>
      <td><code>&lt;textarea&gt;&lt;/textarea&gt;</code></td>
      <td><textarea></textarea></td>
      <td>Can be resized</td>
    </tr>
  </table>
</div>

Baxmayaraq ki, bu `inputlar` çox oxşar görünür və istifadəçilərin _istənilən_ mətni daxil etmələrinə icazə verir (hətta yanlış `input`), onların tipləri inpurlara xüsusi **semantka** təmin edir, hansı məlumatın **ehtimal olunduğunu** müəyyən etməklə.

Brauzerlər sonradan onun interaktivliyini artırmaq və ya hansı məzmunun gözlənildiyinə işarə etmək üçün idarəetmə interfeysini bir qədər dəyişə bilər.

Məsələn, şifrə inputu xarakterlərin yerinə nöqtələr göstərir.

<div class="result">
  <input type="password" value="hunter2">
</div>

Və nömrə daxiletmələri yuxarı və aşağı düymələri ilə onların dəyərini artırmağa/azaltmağa imkan verir.

<div class="result">
  <input type="number" value="12">
</div>

### Placeholders.(Yer tutucular)

Mətn `inputları` **placeholder** mətnləri göstərə bilər, hər hansı bir mətn daxil edilən kimi yox olacaq.

{% highlight html %}
<input type="text" placeholder="Enter your name">
{% endhighlight %}

<div class="result">
  <input type="text" placeholder="Enter your name">
</div>

nə isə yazmağa başlamısınızsa əgər, _"Adınızı daxil edin"_ mətni yox olacaq.

### Labels.(Etiketlər)

Çünki form elementləri özləri çox təsvir edici deyil, onlardan əvvəl adətən mətn **etiket** gəlir.

{% highlight html %}
<label>Email</label>
<input type="email">
{% endhighlight %}

<div class="result">
  <label>Email</label>
  <input type="email">
</div>

Baxmayaraq ki, `placeholders` hansı məzmunun gözlənilməsi barədə ipucu verir, `labelin` olmasının hər zaman üstünlüyü vardır, və digər form kontrollerlərlə istifadə oluna bilər, checkboxes və ya radio buttonlar ilə.

Həmçinin elementi təsvir etmək üçün qısa paraqraf istifadə edə bilərsiniz, `<label>` istifadə etmək semantik olaraq çox etibarlidir çünki onlar sadəcə formlarda mövcuddur, və xüsusi form kontrollerlə qoşalana bilər `for` attributundan istifadə etməklə və inputun `id`-i ilə uygulaşdırmaqla.

{% highlight html %}
<label for="first_name">First name</label>
<input id="first_name" type="text">
{% endhighlight %}

<div class="result">
  <label for="first_name">First name</label>
  <input id="first_name" type="text">
</div>

Etiketə klikləməklə, mətn daxiletmə diqqət mərkəzində olacaq və mətn kursoru içəriyə yerləşdiriləcək. bu cütluk mənasız və istifadəsiz görünə bilər, chechboxlar və radio düymələri ilə lazımlı olacaq.

### Checkboxes/(onay düymələri)

**Checkboxes** ancaq 2 halı olan form kontrollerləridir: checked və ya unchecked. Əsasən istifadəçilərə `hə` ya da `yox` cavabı verməyə imkan yaradır.

{% highlight html %}
<input type="checkbox"> Remember me
{% endhighlight %}

<div class="result">
  <input type="checkbox"> Remember me
</div>

xırda checkboxlara tıklamaq çətin ola bilər, checkboxları ətrafını `<label>` ilə əhatə etmək tövsiyyə olunandır **və** onların açıqlamalarını.

{% highlight html %}
<label>
  <input type="checkbox"> I agree to the terms
</label>
{% endhighlight %}

<div class="result">
  <label>
    <input type="checkbox"> I agree to the terms
  </label>
</div>

Checkbox-un üzərinə basmaq yerinə _"Şərtlə razıyam"_ mətninin üzərinə basmağınız kifayət edir.

default olaraq, checkbox inputları unchecked olur. `checked` attributu əlavə etməklə checked olaraq təyin edə bilərsiniz.

{% highlight html %}
<label>
  <input type="checkbox" checked> Use as my billing address
</label>
{% endhighlight %}

<div class="result">
  <label>
    <input type="checkbox" checked> Use as my billing address
  </label>
</div>

### Radio buttons/(radio düymələr)

Siz radio button-lardan istifadə etməklə istifadəçiyə seçim etmək üçün **seçimlərin siyahısını** təqdim edə bilərsiniz.

bu form kontrolleri işlək etmək üçün, sizin HTML kodlarınızın radio buttonların siyahısını gruplaşdırılması lazımdır. bu `name` atributu ilə eyni dəyəei istifadə etməklə mümkündür:

{% highlight html %}
<label>Marital status</label>
<label>
  <input type="radio" name="status">
  Single
</label>
<label>
  <input type="radio" name="status">
  Married
</label>
<label>
  <input type="radio" name="status">
  Divorced
</label>
<label>
  <input type="radio" name="status">
  Widowed
</label>
{% endhighlight %}

<div class="result">
  <label>Marital status</label>
  <br>
  <label>
    <input type="radio" name="status">
    Single
  </label>
  <br>
  <label>
    <input type="radio" name="status">
    Married
  </label>
  <br>
  <label>
    <input type="radio" name="status">
    Divorced
  </label>
  <br>
  <label>
    <input type="radio" name="status">
    Widowed
  </label>
</div>

Çünki bütün radiobuttonlar onların `name` atributu üçün eyni _dəyəri_ istifadə edirlər (bu halda dəyər `"statusdur"`), bir variantın seçilməsi bütün digərlərinin seçimini ləğv edəcək. radiobuttonlara **bir-birlərini istinad** edənlər demək olar.

#### buttons və checkboxes arasındakı fərqlər

nə zaman ki, checkbox özlüyündə mövcud olsa belə, radio buttonlar sadəcə siyahı kimi görünə bilər (bu da ən azı _2_ variantın olması deməkdir).

Həmçinin, checkbox-a klikləmək **istəyə bağlıdır**radio düymələrindən birini secmək **məcburidir**. Buna görə radio buttonun digərinin seçimini seçməyincə radio düyməsinin işarəsini silmək mümkün deyil. Ancaq sonda, rado buttonlardan birini secmək zəruridir.

### Dropdown menus/(Açılan menyular)

Seçmək üçün seçimlərin sayı çox yer tutursa, `<select>` dropdown menusundan istifadə edə bilərsiniz.

Onlarda radio buttonlar kimi istifadə olunur. Yalnız onların sxemi fərqlidir.

{% highlight html %}
<select>
  <option>January</option>
  <option>February</option>
  <option>March</option>
  <option>April</option>
  <option>May</option>
  <option>June</option>
  <option>July</option>
  <option>August</option>
  <option>September</option>
  <option>October</option>
  <option>November</option>
  <option>December</option>
</select>
{% endhighlight %}

<div class="result">
  <select>
    <option>January</option>
    <option>February</option>
    <option>March</option>
    <option>April</option>
    <option>May</option>
    <option>June</option>
    <option>July</option>
    <option>August</option>
    <option>September</option>
    <option>October</option>
    <option>November</option>
    <option>December</option>
  </select>
</div>

#### Çoxlu seçim dropdown menusu

Əgər `çoxlu` attributlar əlavə etmisinizsə, birdən çox seçim seçmək imkanı verə bilərsiniz.

{% highlight html %}
<label>Which browsers do you have?</label>
<select multiple>
  <option>Google Chrome</option>
  <option>Internet Explorer</option>
  <option>Mozilla Firefox</option>
  <option>Opera</option>
  <option>Safari</option>
</select>
{% endhighlight %}

<div class="result">
  <label>Which browsers do you have?</label>
  <br>
  <select multiple>
    <option>Google Chrome</option>
    <option>Internet Explorer</option>
    <option>Mozilla Firefox</option>
    <option>Opera</option>
    <option>Safari</option>
  </select>
</div>

  Ctrl (və ya ⌘) düyməsini basılı saxlamaqla çoxlu seçim edə bilərsiniz. Bu, ardıcıl olaraq birdən çox checkbox-dan istifadə etmək üçün yaxşı alternativ ola bilər.

### Nümunə: tam bir qeydiyyat formu

{% highlight html %}
<form action="/signup" method="POST">
  <p>
    <label>Title</label>
    <label>
      <input type="radio" name="title" value="mr">
      Mr
    </label>
    <label>
      <input type="radio" name="title" value="mrs">
      Mrs
    </label>
    <label>
      <input type="radio" name="title" value="miss">
      Miss
    </label>
  </p>
  <p>
    <label>First name</label>
    <input type="text" value="first_name">
  </p>
  <p>
    <label>Last name</label>
    <input type="text" value="last_name">
  </p>
  <p>
    <label>Email</label>
    <input type="email" value="email">
  </p>
  <p>
    <label>Phone number</label>
    <input type="tel" value="phone">
  </p>
  <p>
    <label>Password</label>
    <input type="password" value="password">
  </p>
  <p>
    <label>Confirm your password</label>
    <input type="password" value="password_confirm">
  </p>
  <p>
    <label>Country</label>
    <select>
      <option>Canada</option>
      <option>France</option>
      <option>Germany</option>
      <option>Italy</option>
      <option>Japan</option>
      <option>Russia</option>
      <option>United Kingdom</option>
      <option>United States</option>
    </select>
  </p>
  <p>
    <label>
      <input type="checkbox" value="terms">
      I agree to the <a href="/terms">terms and conditions</a>
    </label>
  </p>
  <p>
    <button>
      Sign up
    </button>
  </p>
</form>
{% endhighlight %}

<div class="result">
  <form action="/signup" method="POST">
    <p>
      <label>Title</label>
      <label>
        <input type="radio" name="title" value="mr">
        Mr
      </label>
      <label>
        <input type="radio" name="title" value="mrs">
        Mrs
      </label>
      <label>
        <input type="radio" name="title" value="miss">
        Miss
      </label>
    </p>
    <p>
      <label>First name</label>
      <input type="text">
    </p>
    <p>
      <label>Last name</label>
      <input type="text">
    </p>
    <p>
      <label>Email</label>
      <input type="email">
    </p>
    <p>
      <label>Phone number</label>
      <input type="tel">
    </p>
    <p>
      <label>Password</label>
      <input type="password">
    </p>
    <p>
      <label>Confirm your password</label>
      <input type="password">
    </p>
    <p>
      <label>Country</label>
      <select>
        <option>Canada</option>
        <option>France</option>
        <option>Germany</option>
        <option>Italy</option>
        <option>Japan</option>
        <option>Russia</option>
        <option>United Kingdom</option>
        <option>United States</option>
      </select>
    </p>
    <p>
      <label>
        <input type="checkbox">
        I agree to the <a href="/terms">terms and conditions</a>
      </label>
    </p>
    <p>
      <button>
        Sign up
      </button>
    </p>
  </form>
</div>

Başqa form kontrollerləridə mövcuddur, ancaq biz ən cox istifadə olunanlardan bu mövzuda bəhs etdik.

Səhifəmizi dizayn eləməyimizin vaxtıdır artıq.
