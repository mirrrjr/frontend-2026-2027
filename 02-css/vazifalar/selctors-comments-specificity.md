# CSS mashqlari: Selectors, Comments, Specificity

## 1-qism: Selectors

### Mashq 1.1: Element selector (3 daqiqa)

```html
<h1>Sarlavha</h1>
<p>Birinchi paragraf</p>
<p>Ikkinchi paragraf</p>
```

**Vazifa:** Barcha `p` elementlarni ko'k rangga, `h1` ni qizil rangga bo'yang.
**Savol:** Nima uchun ikkala paragraf ham o'zgardi?

### Mashq 1.2: Class selector (5 daqiqa)

```html
<p>Oddiy matn</p>
<p class="muhim">Muhim matn</p>
<p>Yana oddiy matn</p>
<p class="muhim">Yana muhim matn</p>
```

**Vazifa:** Faqat `muhim` classli paragraflarni `orange` rangga bo'yang va `font-size: 24px` bering.

### Mashq 1.3: ID selector (5 daqiqa)

```html
<h1 id="asosiy">Asosiy sarlavha</h1>
<h1>Boshqa sarlavha</h1>
```

**Vazifa:** Faqat `id="asosiy"` elementni yashil qiling.
**Savol:** Bir sahifada ikkita elementga bir xil `id` berish mumkinmi? Sinab ko'ring va muhokama qiling.

### Mashq 1.4: Attribute selector (5 daqiqa)

```html
<button>Yuborish</button>
<button disabled>Yuborish (o'chirilgan)</button>
<input type="text" placeholder="Ism" />
<input type="password" placeholder="Parol" />
```

**Vazifa:**

1. `[disabled]` yordamida o'chirilgan tugmani kulrang qiling.
2. `[type="password"]` yordamida parol inputiga qizil `border` bering.

### Mashq 1.5: Universal selector (3 daqiqa)

**Vazifa:** Mashq 1.1 dagi HTML uchun `*` yordamida barcha elementlarga `color: purple` bering. Keyin `p` ga alohida `color: black` yozing. Qaysi biri g'olib bo'ldi va nima uchun?

### Mashq 1.6: Mustaqil topshiriq (10 daqiqa)

```html
<h1>Mening sahifam</h1>
<p class="intro">Salom, men dasturchiman.</p>
<p>Men Toshkentda yashayman.</p>
<ul>
    <li class="active">HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
<a href="https://google.com" id="link">Google</a>
<input type="email" disabled />
```

**Vazifa:** Quyidagilarni bajaring, har birida **boshqa turdagi** selector ishlating:

1. `h1` ni markazga joylang (`text-align: center`)
2. `.intro` ga katta shrift bering
3. `.active` ni qalin (`font-weight: bold`) qiling
4. `#link` dan `text-decoration` ni olib tashlang
5. `[disabled]` ga `opacity: 0.5` bering

---

## 2-qism: Comments

### Mashq 2.1: Izoh yozish (3 daqiqa)

```css
p {
    color: red;
    color: blue;
}
```

**Vazifa:** Bir qatorli izoh `/* ... */` yordamida `color: red` qatorini "o'chirib qo'ying". Brauzerda rang qanday o'zgardi?

### Mashq 2.2: Ko'p qatorli izoh (3 daqiqa)

**Vazifa:** Quyidagi kodning tepasiga ko'p qatorli izoh yozing: fayl nomi, muallif va sana.

```css
h1 {
    color: red;
}
p {
    color: blue;
}
```

### Mashq 2.3: Xatoni toping (5 daqiqa)

```css
/* Sarlavha stillari
h1 {
  color: red;
}

/* Paragraf stillari */
p {
    color: blue;
}
```

**Savol:** Nima uchun `h1` ning rangi o'zgarmayapti? Xatoni toping va tuzating.
_(Izoh: yopilmagan izoh keyingi `_/` gacha hamma narsani "yeb qo'yadi".)\*

### Mashq 2.4: Kodni bo'limlarga ajratish (5 daqiqa)

**Vazifa:** 1.6-mashqdagi CSS kodini izohlar bilan bo'limlarga ajrating: `/* ===== Matn ===== */`, `/* ===== Ro'yxat ===== */`, `/* ===== Forma ===== */`.

### Mashq 2.5: Debug usuli (3 daqiqa)

**Vazifa:** Istalgan 3 ta qoidani birin-ketin izohga olib, sahifa qanday o'zgarishini kuzating. Izohlar kodni tekshirish uchun qanday foydali ekanini muhokama qiling.

---

## 3-qism: Specificity

### Mashq 3.1: Taxmin qiling, keyin tekshiring (7 daqiqa)

```html
<h1 id="heading1" class="heading">Hello World</h1>
```

```css
h1 {
    color: green;
}
.heading {
    color: yellow;
}
#heading1 {
    color: red;
}
```

**Vazifa:** Avval **daftarga** yozing: sarlavha qaysi rangda bo'ladi? Keyin kodni ishga tushirib tekshiring.
Keyin qoidalarning tartibini almashtiring. Natija o'zgardimi? Nima uchun?

### Mashq 3.2: Tartib muhimmi? (5 daqiqa)

```html
<p class="a b">Matn</p>
```

```css
.a {
    color: red;
}
.b {
    color: blue;
}
```

**Vazifa:** Rang nima bo'ldi? `.a` va `.b` qoidalarining o'rnini almashtiring. Bir xil o'ziga hoslikda nima hal qiladi? _(Javob: oxirgi yozilgan qoida.)_

### Mashq 3.3: Inline style (5 daqiqa)

```html
<p id="text" class="text" style="color: orange;">Matn</p>
```

```css
#text {
    color: red;
}
.text {
    color: blue;
}
p {
    color: green;
}
```

**Vazifa:** Qaysi rang qo'llanadi? Inline stilni olib tashlasangiz-chi?

### Mashq 3.4: Tartiblash o'yini (7 daqiqa)

O'quvchilarga quyidagi selectorlarni **eng kuchsizdan eng kuchliga** tartiblashni bering:

`p` | `.box` | `#box` | `[type="text"]` | `style="..."` | `*`

_(To'g'ri javob: `_`→`p`→`.box`=`[type="text"]`→`#box` → inline.)\*

**Vazifa:** Hisoblab, keyin ularni kuchi bo'yicha tartiblang.

### Mashq 3.5: Yakuniy topshiriq (15 daqiqa)

```html
<div class="card" id="main-card">
    <h2 class="title">Kurs nomi</h2>
    <p class="desc">Kurs haqida qisqacha ma'lumot.</p>
    <button class="btn" disabled>Yozilish</button>
</div>
```

**Vazifa:** Quyidagi shartlarni bajaring (`!important` ishlatish mumkin emas):

1. `.title` qizil, lekin uni `h2` selector ham yashil qilishga urinsin. Qaysi g'olib?
2. `#main-card` ga `background: lightblue`, `.card` ga `background: pink` bering. Qaysi biri ko'rinadi?
3. `.btn` ni `[disabled]` selector bilan kulrang qilmoqchisiz, lekin `.btn` allaqachon ko'k. Natijani oldindan taxmin qiling, so'ng tekshiring.
4. Har bir qoidaga nima uchun shunday natija chiqqanini izoh (`/* */`) bilan yozing.
