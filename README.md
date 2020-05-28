<div dir="rtl" style="padding:0 20% 0 20%">

# ברוכים הבאים ל Vue.js !!! <img src="Vue.js_Logo.png" width="50" height="43.3" alt="Vue.js Logo">

## הכנה

עבור המעבדה הזאת אני ממליץ לכם:

1. להוריד את כלי הפיתוח עבור vue בתוך הדפדפן:
   - [עבור הדפדפן של Chrome](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
   - [עבור הדפדפן של Firefox](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
2. לייבא את הקוד [מgithub](https://github.com/SISE-Web-Development-Environments/LAB10)
3. להוריד את התוספים הבאים לvscode:
   - Markdown All in One
   - Live Server
4. לפתוח את [הדוקומנטציה של Vue](https://vuejs.org/v2/guide/)

> _בזמנכם הפנוי לראות את [הדוקומנטרי של Vue](https://www.youtube.com/watch?v=OrxmtDw4pVI)_

## מבוא

**המטרה** שלכם במעבדה היא **ללמוד ולהתנסות ב Vue.js** בפעם הראשונה ובעזרתה ליצור **עמוד Register**.

**לעומת עבודה 2**, שבה יצרתם עמוד Register באמצעות שימוש בjavascript בסיסי ובספרייה JQuery, כעת אנחנו ניעזר ביכולת של Vue.js בנוסף לjavascript הבסיסי.

**Vue.js (או בקיצור - Vue) היא ספריית javascript מתקדמת שעוזרת לנו ליצור אתרים דינאמים בצד הלקוח.**

**הקובץ שאיתו תעבדו הוא [register.html](task/register.html) שכרגע ריק.**

(דף Login יהיה בנוי בצורה דומה רק שלא נבדוק בו קלט. אתם מוזמנים ליצור אותו לאחר מכן ולבדוק שהצלחתם)

## צורת הייבוא של Vue

את Vue אנחנו יכולים לייבא בכמה דרכים.\
במעבדה הזאת נייבא את Vue על ידי תג script (מומלץ להכריז עליו בhead):

<div id="import" dir="ltr" style="padding-left:15%;">

```html
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

</div>

> אפשר לראות שזה דומה לצורה בא ייבאנו את ספריית JQuery ש Vue באה להחליף.

## אפליקציית Vue

כאשר אנחנו רוצים ליצור _אפליקציית Vue_, ניצור **אובייקט Vue** על ידי:

<div id="new" dir="ltr" style="padding-left:15%;">

```javascript
new Vue({
  // options
  el: "#app" // selector for template
  // data: ,
  // methods: ,
  // ... ,
});
```

</div>

קובץ HTML שבו משולב אובייקט Vue יראה כך:

<div dir="ltr" style="padding-left:15%;">

```html
<!DOCTYPE html>
<!-- The View -->
<html>
  <head>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  </head>

  <body>
    <!-- The Template -->
    <div id="app">
      hello world vue
    </div>
  </body>
</html>

<!-- The Logic -->
<script>
  // The Vue instance
  var app = new Vue({
    el: "#app"
  });
</script>

<!-- The Style -->
<style></style>
```

</div>

**[קישור לדוגמאת הקוד הראשונה](examples/1_hello_world_vue.html)**

## <span id="task1" style="color:green;"> <-- משימה 1 --> </span>

**בקובץ [register.html](task/register.html) יש ליצור את השלד של המסמך.**

**כמו בדוגמא מעל ראינו שהשל מורכב משלושה חלקים -**

1. **התצוגה - תחת תג HTML, שתייבא את Vue בhead ובbody תכיל אלמנט (לדוגמא div) שיהיה הtemplate של אובייקט הVue**

2. **הלוגיקה - תחת תג script, שתיצור אובייקט Vue המקושר לאלמנט שיצרתם ב (1)**
3. **עיצוב - (אופציונלי) תג style, שבתוכו נציין את העיצוב של המסמך שלנו**

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

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

כאשר הערכים של אותם פרמטרים משתנים, התצוגה תגיב ותתעדכן לפי הערכים החדשים.

אחת האפשרויות לתצוגה של אותם ערכים ניתנת באמצעות שימוש בסוגריים מסולסלים ובתוכם הפרמטר:

<div dir="ltr" style="padding-left:15%;">

```html
{{ message }}
```

</div>

**[קישור לדוגמאת הקוד השנייה](examples/2_vue_object_properties.html)**

## <span id="task2" style="color:green;"> <-- משימה 2 --> </span>

**בקובץ [register.html](task/register.html) יש להגדיר משתנים שיחזיקו לנו את קלטי המשתמש של הform**

<div dir="ltr"">

```
username: "",
first_name: "",
last_name: "",
country: "",
password: "",
confirmation_password: "",
email: "",
profile_image_url: ""
```

</div>

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

- ## methods

<div dir="ltr" style="padding-left:15%;">

```javascript
methods: {
  plus: function () {
    this.message += " And ";
    console.log(message);
  }
}
```

</div>

כל הפונקציות שבתוך methods נוספות כפונקציות של האובייקט, והפנייה אליהם בתוך האובייקט היא דרך הפוינטר this.

<div dir="ltr" style="padding-left:15%;">

```javascript
this.plus();
```

</div>

הפנייה לפונקציה מתוך התצוגה תעשה תהיה מתוך expression שנרשום באחד הdirectives.\
_**דוגמא**_ לכך היא על ידי directive בשם [v-on](#v-on) (שנדבר עליו בהמשך):

<div dir="ltr" style="padding-left:15%;">

```html
<button v-on:click="plus">plus button</button>
```

</div>

**[קישור לדוגמאת הקוד השנייה](examples/2_vue_object_properties.html)**

## <span id="task3" style="color:green;"> <-- משימה 3 --> </span>

**בקובץ [register.html](task/register.html) יש ליצור:**

1. **אלמנט form שלו נגדיר את v-on בצורה הבאה:**

<div dir="ltr" style="padding-left:15%;">

```html
<form v-on:submit="FUNCTION_NAME">
  ...
</form>
```

</div>

1. **אלמנט input מסוג <input type="submit" value="Submit">**
2. **פונקציה בתוך הפרמטר methods שתקרא בעת לחיצה על הכפתור. אתם יכולים לאתחל את הפונקציה שתעשה alert למחרוזת מסוימת.**

> **_תזכורות:_**

- שלוחצים על submit בform, הevent שיהיה זה submit של האלמנט form
- מומלץ להשתמש ב `e.preventDefault();` כדי למנוע מהפעולה המקורית של הform להתבצע

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

## directives

סימונים על אלמנט DOM שאומרים לספרייה של Vue לחבר התנהגות מסוימת לאותו אלמנט.

לרוב הסימונים האלה בVue יתחילו ב **-v**.

היום במעבדה נדבר על directives מפורסמים שגם נעשה בהם שימוש במעבדה.

> אני ממליץ לכם לקרוא על עוד directives ולהעשיר את הידע.

ההתנהגות יכולה להיות:

- פעולה שתקרא ברגע שevent מסוים יתקיים
- הvalue של הElement יהיה שווה לפרמטר של האובייקט
- הElement יופיע רק כאשר ערך בוליאני (שיכול להתחשב בפרמטר של האובייקט) יהיה true

* ## <div id="v-on">v-on</div>

מאפשר להאזין לDOM events, ולהפעיל פעולה כשהevent קורה.

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-on:EventName="Function | Inline Statement | Object"

או

@EventName="Function | Inline Statement | Object"
```

</div>

> טיפ: באנגלית קוראים לסימן @ = at, אז אפשר לזכרור את זה כ - at EventName, do somthing

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

**[קישור לדוגמאת הקוד השלישית](examples/3_data_bindings.html)**

[עוד על v-on](https://vuejs.org/v2/api/#v-on)

## <span id="task4" style="color:green;"> <-- משימה 4 - _רשות_ --> </span>

> **תזכורת: כאשר יצרנו את הכפתור submit השתמשנו בv-on.**

**כעת ב[register.html](task/register.html) אתם יכולים להוריד את :v-on ולהשאיר רק את @ כמו שראינו בדוגמא למעלה**

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

- ## v-model

מאפשר לנו ליצור two-way binding בין משתנה של אובייקט Vue לאלמנטי input.

אלמנטי input שקיימים בhtml הם:

- input
- select
- textarea

> מאחורי הקלעים, v-model הוא סוכר תחבירי המשתמש בv-on לevent של קלט עבור אלמנטיי input

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-model="variable"
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

**[קישור לדוגמאת הקוד השלישית](examples/3_data_bindings.html)**

[עוד על v-model](https://vuejs.org/v2/api/#v-model)

## <span id="task5" style="color:green;"> <-- משימה 5 --> </span>

**בקובץ [register.html](task/register.html) יש ליצור את כל התגים הדרושים בתוך תג הform ולקשר אותם למשתנים שהגדרתם ב[משימה 2](#task2)**

<div dir="ltr">

```
* username - type=input.text
* first_name - type=input.text
* last_name - type=input.text
* country - type=select
* password - type=input.password
* confirmation_password - type=input.password
* email - type=input.email
* profile_page_url - type=input.text
```

</div>

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

- ## v-if (and) v-else (and) v-else-if

מרנדר לפי תנאי אלמנט בהתבסס על אמיתות של ערך הביטוי שמקבל.\
האלמנט והרכיבים הכלולים בו נוצרים ונהרסים בין שינויים של ערך הביטוי.

v-else ו v-else-if בעלות **אותו הגיון כמו בשאר שפות תכנות** בכך שelse או else-if יופיע רק לאחר if.

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-if="expression"
v-else-if="expression"
v-else
```

</div>

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<div v-if="flag">
  ***somthing for if***
</div>
<div v-else-if="flag2">
  ***somthing for else-if***
</div>
<div v-else>
  ***somthing for else***
</div>
```

Inside Vue object:

```javascript
data(){
  return {
    flag: false,
    flag2: true
  };
}
```

</div>

**[קישור לדוגמאת הקוד הרביעית](examples/4_conditions.html)**

[עוד על v-if](https://vuejs.org/v2/api/#v-if)\
[עוד על v-else](https://vuejs.org/v2/api/#v-else)\
[העשרה: v-else-if](https://vuejs.org/v2/api/#v-else-if)

## <span id="task6" style="color:green;"> <-- משימה 6 --> </span>

**בקובץ [register.html](task/register.html) יש ליצור:**

1. **משתנה של שגיאות (מסוג מערך)**

2. **בפונקציה שמטפלת בsubmit יש להוסיף בדיקות ובמידה ובדיקה יצאה שגויה יש להוסיף אותה למשתנה השגיאות.**\
   **הבדיקות יהיו:**
> - **שם משתמש יהיה באורך בין 3 ל- 8 תווים (בעבודה יש להוסיף בדיקת הכלה של אותיות בלבד)**

> - **הסיסמה תהיה באורך של בין 5 ל- 10 תווים (בעבודה יש להוסיף בדיקת הכלה של לפחות מספר אחד ותו מיוחד אחד)**

1. **תג div שמציג את השגיאות אם הsubmit לא עבר בהצלחה ונתקל בשגיאות**

2. **תג div שמציג הודעת הצלחה - "ההרשמה האחרונה שלך עברה בהצלחה" במקרה והsubmit קרה בלי שגיאות**

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

- ## v-for

מרנדר אלמנט מספר פעמים על פי קלט איטרטיבי.

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

<div dir="ltr" style="padding-left:15%;">

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
      "Eran: hey! 😁",
      "Yossi: hey! whats up? 🤷‍♂️",
      "Eran: i'm good ✌"
    ]
  };
}
```

</div>

כדי שVue יוכל לעקוב אחרי הזהות של כל אלמנט שנוצר מ v-for, ולמרות שינויים שיכולים להיות במשתנה שאנחנו רצים עליו כמו סידור מחדש או מחיקה של איבר מהאמצע, אם נתן לכל אלמנט **key ייחודי**, Vue ידע לא ליצור אותם שוב פעם

את הkey נקח מתוך האיברים של המשתנה.

לדוגמא, אם נקח את הדוגמא ממקודם, מה שיכול להיות ייחודי עבור הודעה היא הזמן שבו היא נשלחה (הסדר יכול להשתנות כי יכולה להיות אפשרות למחוק הודעות).\
לכן אם נשמור את ההודעות בצורה הבאה:

<div dir="ltr" style="padding-left:15%;">

Inside Vue object:

```javascript
data(){
  return {
    messages: [
      { time:1, sender:"Eran", message: "hey! 😁"},
      { time:2, sender:"Yossi", message: "hey! whats up? 🤷‍♂️"},
      { time:3, sender:"Eran", message: "i'm good ✌"}
    ]
  };
}
```

</div>

נוכל להגדיר את v-for בצורה הבאה:

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<ol>
  <li v-for="message in messages" :key="message.time">
    {{ message.sender }}: {{message.message}} (time={{message.time}})
  </li>
</ol>
```

</div>

**[קישור לדוגמאת הקוד החמישית](examples/5_loops.html)**

[עוד על v-for](https://vuejs.org/v2/api/#v-for)

## <span id="task7" style="color:green;"> <-- משימה 7 --> </span>

**יש לשנות את התצוגה של השגיאות לתצוגה שמשתמשת בv-for**

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

## form in Vue

בעזרת כל מה שלמדנו עד עכשיו נוכל לראות שיצרנו form element שבזמן submit יעשה ואלידציה לקלט.\
אם הקלט לא עבר את הואלידציה, נציג למשתמש מה הטעויות שלו.

במידה וכל הקלט תקין, נוכל להוסיף באמצעות axios שליחה של בקשה עם כל הנתונים ששמרנו.

קישור לקוד של שרת [אפשר למצוא פה](https://github.com/SISE-Web-Development-Environments/LAB10_SERVER)

**[קישור לדוגמאת הקוד השישית](examples/6_form.html)**

[מידע על שימוש בform inputs ב Vue](https://vuejs.org/v2/guide/forms.html)\
[מידע על form validations ב Vue](https://vuejs.org/v2/guide/forms.html)

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

- ## computed

בדומה ל#c שבו אנחנו יכולים ליצור property שייצר לנו משתנה שלו מוגזר getter ו setter:

<div dir="ltr" style="padding-left:15%;">

```c#
// c# code
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

אנחנו יכולים ליצור משתנים כמו בdata אבל עם getter ו setter.\
**הדיפולט הוא משתנה שמאפשר רק get כמו עבור lowerCase_message:**

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

**[קישור לדוגמאת הקוד השנייה](examples/2_vue_object_properties.html)**

- ## created (and) beforeDestroy
  במחזור החיים של אובייקט Vue, ישנם שני eventים שמעניינים אותנו:

> - **created:** מסמל את הרגע בו האובייקט נוצר ואנחנו יכולים להריץ קוד
>   &#09;  
>   **<span style="color:green;">מתי נשתמש --> שליחת בקשה לשרת והשמת התוצאה למשתנה של האובייקט ברגע שהיא חוזרת</span>**

> - **beforeDestroy:** מסמל את הרגע לפני שהאובייקט נהרס ומאפשר לנו להריץ קוד
>   &#09;  
>   **<span style="color:green;">מתי נשתמש --> ניקוי נתונים שאנחנו לא צריכים מהזיכרון</span>**

**[קישור לדוגמאת הקוד השנייה - יש להוציא מהערה את הפרמטר created כדי לראות דוגמא](examples/2_vue_object_properties.html)**

[link to life cycle image](#lifecycle)

**בקובץ עליכם להדפיס לconsole שהאובייקט עבור העמוד (register או login) נוצר**

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

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
<button v-bind:disabled="!message" @click="addMessage">
  Add new message
</button>

או

<button :disabled="!message" @click="addMessage">
  Add new message
</button>
```

Inside Vue object:

```javascript
data(){
  return {
    message: ""
  };
},
methods: {
  addMessage(){
    // Adds a new Message
  }
}
```

</div>

**[קישור לדוגמאת הקוד השלישית](examples/3_data_bindings.html)**

[עוד על v-bind](https://vuejs.org/v2/api/#v-bind)

</div>
