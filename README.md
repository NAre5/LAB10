<div dir="rtl" style="padding:0 20% 0 20%">

# ברוכים הבאים ל Vue.js ! :rocket:

## הכנה

עבור המעבדה הזאת אני ממליץ לכם:

1. להוריד את כלי הפיתוח עבור vue בתוך הדפדפן:
   - [עבור הדפדפן של Chrome](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
   - [עבור הדפדפן של Firefox](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
2. לייבא את הקוד [מgithub](https://github.com/SISE-Web-Development-Environments/LAB10)
3. להוריד את התוספים הבאים לvscode:
   - Markdown Preview Enhanced
   - Live Server
4. לפתוח את [הדוקומנטציה של Vue](https://vuejs.org/v2/guide/)

## מטרה

**המטרה שלכם בסוף התרגול זה לייצר עמוד Register ועמוד Login (כרגע נפרדים).**

**הקבצים האלה הם הקבצים [register.html](task/register.html) ו [login.html](task/login.html) (שכרגע ריקים).**

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
  el: "#app",// selector for template
  // data: ,
  // methods: ,
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

דוגמא לקובץ HTML שבו משולב אובייקט Vue:

<div dir="ltr" style="padding-left:15%;">

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My first Vue app</title>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  </head>

  <body>
    <div id="app"> <!-- The template -->
      hello world vue
    </div>

    <script>
      var app = new Vue({ // The Vue instance
        el: "#app",
      });
    </script>
  </body>
</html>
```

</div>

## <span id="task1" style="color:green;"> <-- משימה 1 --> </span>
**בכל קובץ יש ליצור:**
1. **תג שיכיל את הTemplate של האובייקט (שבו בעתיד ניצור form שיקבל מהמשתמש את המידע הנחוץ)**
2. **אובייקט Vue (שיכיל את הלוגיקה של הטופס)**

*קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7) [8](#task8)*


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

## <span id="task2" style="color:green;"> <-- משימה 2 --> </span>
**בכל קובץ יש להגדיר משתנים שיחזיקו לנו את קלטי המשתמש של הform (כמו שם המשתמש והסיסמא)**

*קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7) [8](#task8)*

**[קישור לדוגמאת הקוד השנייה](codes/3_vue_object_properties.html)**

- ## methods

<div dir="ltr" style="padding-left:15%;">

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

<div dir="ltr" style="padding-left:15%;">

```javascript
this.plus();
```

</div>

הפנייה לפונקציה מתוך התצוגה תעשה בצורה הבאה על ידי directive בשם [v-on](#v-on):

<div dir="ltr" style="padding-left:15%;">

```html
<button v-on:click="plus">plus button</button>
```

</div>

## <span id="task3" style="color:green;"> <-- משימה 3 --> </span>
**בכל קובץ יש ליצור:**
1. **תג form ובו תג input מסוג <input type="submit" value="Submit">**
2. **פונקציה בתוך הפרמטר methods שתקרא בעת לחיצה על הכפתור**

*קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7) [8](#task8)*

**[קישור לדוגמאת הקוד השנייה](codes/3_vue_object_properties.html)**

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

> **<span style="color:green;">מתי נשתמש --> ##########ENTER_ANSWER_HERE###########</span>**

**[קישור לדוגמאת הקוד השנייה](codes/3_vue_object_properties.html)**

- ## created (and) beforeDestroy
  במחזור החיים של אובייקט Vue, ישנם שני eventים שמעניינים אותנו:

> - **created:** מסמל את הרגע בו האובייקט נוצר ואנחנו יכולים להריץ קוד
>   &#09;  
>   **<span style="color:green;">מתי נשתמש --> שליחת בקשה לשרת והשמת התוצאה למשתנה של האובייקט ברגע שהיא חוזרת</span>**

> - **beforeDestroy:** מסמל את הרגע לפני שהאובייקט נהרס ומאפשר לנו להריץ קוד
>   &#09;  
>   **<span style="color:green;">מתי נשתמש --> ניקוי נתונים שאנחנו לא צריכים מהזיכרון</span>**

## <span id="task4" style="color:green;"> <-- משימה 4 --> </span>
**בכל קובץ עליכם להדפיס לconsole  שהאובייקט עבור העמוד (register או login) נוצר**

*קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7) [8](#task8)*

[link to life cycle image](#lifecycle)

**[קישור לדוגמאת הקוד השנייה - יש להוציא מהערה את הפרמטר created כדי לראות דוגמא](codes/3_vue_object_properties.html)**

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

## <span id="task5" style="color:green;"> <-- משימה 5 - *רשות* --> </span>
> **תזכורת: כאשר יצרנו את הכפתור submit השתמשנו בv-on.**

**כעת אתם יכולים להוריד את :v-on ולהשאיר רק את @ כמו שראינו בדוגמא למעלה**

*קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7) [8](#task8)*

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

## <span id="task6" style="color:green;"> <-- משימה 6 --> </span>
**בכל קובץ יש ליצור את כל התגים הדרושים בתוך תג הform ולקשר אותם למשתנים שהגדרתם ב[משימה 2](#task2)**

*קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7) [8](#task8)*

[עוד על v-model](https://vuejs.org/v2/api/#v-model)

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
<div v-if="flag2">
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

## <span id="task7" style="color:green;"> <-- משימה 7 --> </span>
**בכל קובץ יש ליצור:**
1. **משתנה של שגיאות (כרגע מסוג string)**

2. **בפונקציה שמטפלת בsubmit בדיקות ששם המשתמש רשום כולו באותיות קטנות ואורך הסיסמא בין 3 ל6 תווים. במידה ובדיקה יצאה שגויה יש להוסיף אותה למשתנה השגיאות**

3. **תג div שמציג את השגיאות אם הsubmit לא עבר בהצלחה ונתקל בשגיאות**

4. **תג div שמציג הודעת הצלחה במקרה והsubmit קרה בלי שגיאות**

*קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7) [8](#task8)*

[עוד על v-if](https://vuejs.org/v2/api/#v-if)\
[עוד על v-else](https://vuejs.org/v2/api/#v-else)\
[העשרה: v-else-if](https://vuejs.org/v2/api/#v-else-if)

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
      "eran: hey! 😁",
      "yossi: hey! whats up? 🤷‍♂️",
      "i'm good ✌"
    ]
  };
}
```

</div>

## <span id="task8" style="color:green;"> <-- משימה 8 --> </span>
**בכל קובץ יש ליצור:**
1. **תג שיכיל את הTemplate של האובייקט (שבו בעתיד ניצור form שיקבל מהמשתמש את המידע הנחוץ)**
2. **אובייקט Vue (שיכיל את הלוגיקה של הטופס)**

*קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7) [8](#task8)*

[עוד על v-for](https://vuejs.org/v2/api/#v-for)

## form in Vue

איך מייצרים form בVue


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
