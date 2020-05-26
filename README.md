<div dir="rtl" style="padding:0 20% 0 20%">

# ברוכים הבאים ל Vue.js ! :rocket:

## הכנה

עבור המעבדה הזאת אני ממליץ לכם:

1. להוריד את כלי הפיתוח עבור vue בתוך הדפדפן:
   - [עבור הדפדפן של Chrome](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
   - [עבור הדפדפן של Firefox](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
2. לייבא את הקוד [מgithub]()
3. להוריד את התוספים הבאים לvscode:
   - Markdown Preview Enhanced
   - Live Server
4. לפתוח את [הדוקומנטציה של Vue](https://vuejs.org/v2/guide/)

## מטרה

**המטרה שלנו בסוף התרגול זה לייצר עמוד Register ועמוד Login (כרגע נפרדים)**

## צורת הייבוא של Vue

את המודולים של Vue אנחנו יכולים לייבא בכמה דרכים.
הדרך הראשונה שנדבר עליה היא על ידי תג script (מומלץ להכריז עליו בhead):

<div id="import" dir="ltr" style="padding-left:15%;">

```html
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

</div>

> אפשר לראות שזה דומה לצורה בא ייבאנו את ספריית JQuery ש Vue באה להחליף.

## אפליקציית Vue

כאשר אנחנו רוצים ליצור _אפליקציית Vue_, היא חייבת להכיל **אובייקט Vue שיהיה הRoot**, על ידי:

<div id="new" dir="ltr" style="padding-left:15%;">

```javascript
new Vue({
  // options
  el: "#app",// query selector
  data: ,
  methods: ,
  // ... ,
})
```

</div>

אפליקציית Vue יכולה להיות מאורגנת בצורת עץ מקונן שמכיל קומפוננטות אחרות של Vue.

**_לדוגמא_** אפליקציית משימות יכולה להראות בצורה הזאת:

<div dir="ltr" style="padding-left:15%;">

```
Root Instance
└─ TodoList
   ├─ TodoItem
   │  ├─ DeleteTodoButton
   │  └─ EditTodoButton
   └─ TodoListFooter
      ├─ ClearTodosButton
      └─ TodoListStatistics
```

</div>

> **<span style="color:green;">מתי נשתמש --> בכל קובץ ניצור אובייקט Vue שיכיל את כל המידע שאנחנו צריכים ובTemplate נייצר form שיקבל מהמשתמש את המידע הנחוץ</span>**

**[קישור לדוגמאת הקוד הראשונה](codes/2_hello_world_vue.html)**

## פרמטרים של אובייקט Vue

לאובייקט Vue יש מספר רחב של פרמטרים עליהם אנחנו מצהירים בזמן יצירת האובייקט ([options](#new) כמו שרשום למעלה)

במעבדה הזאת אנחנו נדבר על מספר פרמטרים:

- ## data

<div dir="ltr" style="padding-left:15%;">

```javascript
data() {
  return {
    message: "Hello Vue!"
  };
}
```

</div>

כל הפרמטרים שחוזרים מdata נוספים כפרמטרים של האובייקט, והפנייה אליהם בתוך האובייקט היא כמו במחלקה בjava - דרך הפוינטר this.

כאשר אובייקט Vue נוצר, הוא מוסיף את כל הפרמטרים שנמצאים באובייקט data אל המערכת הריאקטיבית של Vue. כאשר הערכים של אותם פרמטרים משתנים התצוגה תגיב, ותתעדכן לפי הערכים החדשים

אחת האפשרויות לתצוגה של אותם ערכים ניתנת באמצעות שימוש בסוגריים מסולסלים ובתוכם הפרמטר:

<div dir="ltr" style="padding-left:15%;">

```html
{{ message }}
```

</div>

> **<span style="color:green;">מתי נשתמש --> כאשר נגדיר משתנים שיחזיקו לנו את השם משתמש והסיסמא בform</span>**

**[קישור לדוגמאת הקוד השנייה](codes/3_vue_object_properties.html)**

- ## methods

<div id="new" dir="ltr" style="padding-left:15%;">

```javascript
methods: {
  plus: function () {
    this.message += " and ";
    console.log(message);
  }
}
```

</div>

כל הפונקציות שבתוך methods נוספים כפונקציות של האובייקט, והפנייה אליהם בתוך האובייקט היא דרך הפוינטר this.

<div id="new" dir="ltr" style="padding-left:15%;">

```javascript
this.plus();
```

</div>

הפנייה לפונקציה מתוך התצוגה תעשה בצורה הבאה על ידי directive בשם [v-on](#v-on):

<div id="new" dir="ltr" style="padding-left:15%;">

```html
<button v-on:click="plus">plus button</button>
```

</div>

> **<span style="color:green;">מתי נשתמש --> כאשר נגדיר פעולה שתרוץ כאשר נלחץ על כפתור submit בform</span>**

**[קישור לדוגמאת הקוד השנייה - יש להוציא מההערה את הפרמטר methods ואת הכפתור](codes/3_vue_object_properties.html)**

- ## computed

בדומה ל#c שבו אנחנו יכולים ליצור property שייצר לנו משתנה שלו מוגזר getter ו setter -

<div id="new" dir="ltr" style="padding-left:15%;">

```c#
class Mail
{
  //Data members:
  private string message;

  //Properties:
  public string LowerCase_Message
  {
    get { return message.ToLower(); }
    set { message = value; }
  }
}
```

</div>

אנחנו יכולים ליצור משתנים כמו בdata אבל עם getter ו setter.
**הדיפולט הוא משתנה שמאפשר רק get כמו עבור lowerCase_message**

<div dir="ltr" style="padding-left:15%;">

```javascript
computed: {
  lowerCase_message: function(){
    return this.message.toLowerCase();
  }
}
```

</div>

> [קישור להרחבה עבור משתנה עם setter](#computed_with_setter)

כל המשתנים שהגדרנו בתוך computed נוספים לתוך האובייקט, והפנייה אליהם בתוך הקוד היא דרך הפוינטר this.

אחת האפשרויות לתצוגה של אותם ערכים ניתנת באמצעות שימוש בסוגריים מסולסלים ובתוכם הפרמטר:

<div dir="ltr" style="padding-left:15%;">

```html
{{ lowerCase_message }}
```

</div>

> **<span style="color:green;">מתי נשתמש --> ##########ENTER_ANSWER_HERE###########</span>**

**[קישור לדוגמאת הקוד השנייה - יש להוציא מהערה את הפרמטר computed ואת ההערה בbody שמתייחסת לlowerCase_message ](codes/3_vue_object_properties.html)**

- ## created (and) beforeDestroy
  במחזור החיים של אובייקט Vue, ישנם שני eventים שמעניינים אותנו:

> - **created:** מסמל את הרגע בו האובייקט נוצר ואנחנו יכולים להריץ קוד
>   &#09;  
>   **<span style="color:green;">מתי נשתמש --> שליחת בקשה לשרת והשמת התוצאה למשתנה של האובייקט ברגע שהיא חוזרת</span>**

> - **beforeDestroy:** מסמל את הרגע לפני שהאובייקט נהרס ומאפשר לנו להריץ קוד
>   &#09;  
>   **<span style="color:green;">מתי נשתמש --> ניקוי נתונים שאנחנו לא צריכים מהזיכרון</span>**

[link to life cycle image](#lifecycle)

**[קישור לדוגמאת הקוד השנייה - יש להוציא מהערה את הפרמטר created](codes/3_vue_object_properties.html)**

## directives

סימונים על אלמנט DOM שאומרים לספרייה של Vue לחבר התנהגות מסוימת לאותו אלמנט.
ההתנהגות יכולה להיות:

- פעולה שתקרא ברגע שevent מסוים יתקיים
- הvalue של הElement יהיה שווה לפרמטר של האובייקט
- הElement יופיע רק כאשר ערך בוליאני (שיכול להתחשב בפרמטר של האובייקט) יהיה true

לרוב הסימונים האלה בVue יתחילו ב **-v**.

היום במעבדה נדבר על directives מפורסמים שגם נעשה בהם שימוש במעבדה.

> אני ממליץ לכם לקרוא על עוד directives ולהעשיר את הידע.

- ## <div id="v-on">v-on</div>

מפשר להאזין לDOM events, ולהפעיל פעולה כשהevent קורה.

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-on:EventName="Function | Inline Statement | Object"

או

@EventName="Function | Inline Statement | Object"
```

</div>

> טיפ: באנגלית קוראים לסימן @ = at, אז אפשר לזכרור את זה כ - at EventName

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<a v-on:click="handleClick">Click me!</a>

או

<a @click="handleClick">Click me!</a>
```

Inside Vue object:

```javascript
methods: {
  handleClick: function() {
    alert('Clicked');
  }
}

```

</div>

[עוד על v-on](https://vuejs.org/v2/api/#v-on)

- ## v-bind

מאפשר לנו ליצור one-way binding בין משתנה של אובייקט Vue ל attribute

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-bind:AttributeName="expression"

או

:AttributeName="expression"
```

</div>

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<button v-bind:disabled="buttonFlag">
  Button
</button>

או

<button :disabled="buttonFlag">
  Button
</button>
```

Inside Vue object:

```javascript
data(){
  return {
    buttonFlag: true
  };
}
```

</div>

[עוד על v-bind](https://vuejs.org/v2/api/#v-bind)

- ## v-model

יוצר two-way binding לאלמנטי input

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-bind:AttributeName="variable"
```

</div>

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<input v-model="message" />
```

Inside Vue object:

```javascript
data(){
  return {
    message: ""
  };
}
```

</div>

[עוד על v-model](https://vuejs.org/v2/api/#v-model)

- ## v-if (and) v-else

מרנדר לפי תנאי אלמנט בהתבסס על אמיתות של ערך הביטוי שמקבל.\
האלמנט והרכיבים הכלולים בו נוצרים ונהרסים בין שינויים של ערך הביטוי.

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-if="expression"
v-else
```

</div>

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<div v-if="flag">
  ***somthing for if***
</div>
<div v-else>
  ***somthing for else***
</div>
```

Inside Vue object:

```javascript
data(){
  return {
    flag: true
  };
}
```

</div>

[עוד על v-if](https://vuejs.org/v2/api/#v-if)\
[עוד על v-else](https://vuejs.org/v2/api/#v-else)\
[העשרה: v-else-if](https://vuejs.org/v2/api/#v-else-if)

- ## v-for

מרנדר אלמנט מספר פעמים על פי הקלט.

צורת הכתיבה חייבת להיות בצורה `alias in expression` , כדי לספק כינוי לאלמנט הנוכחי באיטרציה.

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-for="alias in Array | Object | number | string | Iterable"
```

</div>

לחלופין, אפשר לציין כינוי לאינדקס (וגם למפתח אם עוברים על אובייקט):

<div dir="ltr" style="padding-left:15%;">

```
v-for="(item, index) in items"
v-for="(val, key) in object"
v-for="(val, name, index) in object"
```

</div>

<div dir="ltr" style=";">

Inside template:

```html
<div v-for="(message, i) in messages">
  {{ i }}) {{ message }}
</div>

<ol>
  <li v-for="message in messages">
    {{ message }}
  </li>
</ol>
```

Inside Vue object:

```javascript
data(){
  return {
    messages: [
      "eran: hey! 😁",
      "yossi: hey! whats up? 🤷‍♂️",
      "i'm good ✌"
    ]
  };
}
```

</div>

[עוד על v-for](https://vuejs.org/v2/api/#v-for)

&nbsp;
&nbsp;

---

## נספחים

- ## <div id="computed_with_setter">computed with setter</div>

<div dir="ltr" style="padding-left:15%;">

```javascript
computed: {
  fullName: {
    // getter
    get: function () {
      return this.firstName + ' ' + this.lastName
    },
    // setter
    set: function (newValue) {
      var names = newValue.split(' ')
      this.firstName = names[0]
      this.lastName = names[names.length - 1]
    }
  }
}
```

</div>

עבור fullName, שכאשר נריץ:

<div dir="ltr" style="padding-left:15%;">

```javascript
this.fullName = "John Doe";
```

</div>
firstName ו lastName יתעדכנו ב John ו Doe בהתאמה

- ## <div id="lifecycle">lifecycle image</div>

<img src="./lifecycle.png">

</div>
