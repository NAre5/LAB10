<div dir="rtl">

# ברוכים הבאים ל Vue.js :rocket:

## הכנה

עבור המעבדה הזאת אני ממליץ לכם:


1. להוריד את כלי הפיתוח עבור vue בתוך הדפדפן:
   * [עבור הדפדפן של Chrome](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
   * [עבור הדפדפן של Firefox](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
2. לייבא את הקוד מ[github](***ENTER_URL***)
3. להוריד את התוספים הבאים לvscode:
   * Markdown Preview Enhanced
   * Live Server
4. לפתוח את [הדוקומנטציה של Vue](https://vuejs.org/v2/guide/)


<!-- ## מבוא

בנתיים ריק*** -->


## צורת הייבוא של Vue

את המודולים של Vue אנחנו יכולים לייבא בכמה דרכים.
הדרך הראשונה שנדבר עליה היא על ידי תג script: (מומלץ להכריז עליו בhead)

<div id="import" dir="ltr">

```javascript
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```
</div>
אפשר לראות שזה דומה לצורה בא ייבאנו את ספריית JQuery ש Vue באה להחליף.

## אפליקציית Vue

כאשר אנחנו רוצים ליצור *אפליקציית Vue*, היא חייבת להכיל **אובייקט Vue שיהיה הRoot**, על ידי:
<div id="new" dir="ltr">

```javascript
new Vue({options})
```
</div>

אפליקציית Vue יכולה להיות מאורגנת בצורת עץ מקונן שמכיל קומפוננטות אחרות של Vue.
***לדוגמא*** אפליקציית משימות יכולה להראות בצורה הזאת:
<div dir="ltr">

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

[קישור לדוגמאת הקוד הראשונה](codes/2_hello_world_vue.html)

## פרמטרים של אובייקט Vue

לאובייקט Vue יש מספר רחב של פרמטרים עליהם אנחנו מצהירים בזמן יצירת האובייקט ([options](#new) כמו שרשום למעלה)

במעבדה הזאת אנחנו נדבר על מספר פרמטרים:

- ### data

<div dir="ltr" style="overflow: hidden;width:100%;display: block">
<!-- <div dir="ltr" style="float:left">
צורה ישנה - אובייקט

```javascript
data: {
    message: "Hello Vue!"
};
```
</div> -->
<div dir="ltr" style="float:left">
<!-- <b>צורה מועדפת</b> - פונקציה שמחזירה אובייקט -->

```javascript
data() {
  return {
    message: "Hello Vue!"
  };
}
```
</div>
</div>

כל הפרמטרים שחוזרים מdata נוספים כפרמטרים של האובייקט, והפנייה אליהם בתוך האובייקט היא כמו במחלקה בjava - דרך הפוינטר this.

כאשר אובייקט Vue נוצר, הוא מוסיף את כל הפרמטרים שנמצאים באובייקט data אל המערכת הריאקטיבית של Vue. כאשר הערכים של אותם פרמטרים משתנים התצוגה תגיב, ותתעדכן לפי הערכים החדשים

תצוגה של אותם ערכים ניתמת באמצעות שימוש בסוגריים מסולסלים ובתוכם הפרמטר:
```
{{ message }}
```

[קישור לדוגמאת הקוד השנייה](codes/3_vue_object_properties.html)

- ### methods

<div id="new" dir="ltr">

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

<div id="new" dir="ltr">

```javascript
this.plus();
```
</div>

הפנייה לפונקציה מתוך התצוגה תעשה בצורה הבאה על ידי directive בשם v-on:

<div id="new" dir="ltr">

```javascript
<button v-on:click="plus"> plus button </button>
```
</div>

- ### computed

כל מני מילים על 

<!-- <img src="./lifecycle.png"> -->

## directives

סימונים על אלמנט DOM שאומרים לספרייה של Vue לחבר התנהגות מסוימת לאותו אלמנט.
ההתנהגות יכולה להיות:
- פעולה שתקרא ברגע שevent מסוים יתקיים
- הvalue של הElement יהיה שווה לפרמטר של האובייקט
- הElement יופיע רק כאשר ערך בוליאני (שיכול להתחשב בפרמטר של האובייקט) יהיה true

לרוב הסימונים האלה בVue יתחילו ב **-v**.

היום במעבדה נדבר על directives מפורסמים שגם נעשה בהם שימוש במעבדה.
> אני ממליץ לכם לקרוא על עוד directives ולהעשיר את הידע.

- ### v-on

כל מני מילים כל v-on

- ### v-bind

כמה מילים... one way binding

- ### v-model

כמה מילים... two way binding

- ### v-if

כל מני מילים על v-if

- ### v-for

כל מני מילים על v-for



