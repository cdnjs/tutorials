## Usage with plain JavaScript via CDN

HTML:

```html
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.2.6/vue.min.js"></script>
    <!-- Flow Form -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vue-flow-form/1.1.0/vue-flow-form.umd.min.js"></script>
    <!-- Flow Form base CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/vue-flow-form/1.1.0/vue-flow-form.min.css">
    <!-- Optional theme.css -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/vue-flow-form/1.1.0/vue-flow-form.theme-minimal.min.css">
  </head>
  <body>
    <div id="app">
      <flow-form v-bind:questions="questions" v-bind:language="language" />
    </div>
    <script src="app.js"></script>
  </body>
</html>
```

JavaScript (content of app.js):

```js
var app = new Vue({
  el: '#app',
  data: function() {
    return {
      language: new FlowForm.LanguageModel({
        // Your language definitions here (optional).
        // You can leave out this prop if you want to use the default definitions.
      }),
      questions: [
        new FlowForm.QuestionModel({
          title: 'Question',
          type: FlowForm.QuestionType.MultipleChoice,
          options: [
            new FlowForm.ChoiceOption({
              label: 'Answer'
            })
          ]
        })
      ]
    }
  }
});
```

## Project Documentation

* [Guide](https://www.ditdot.hr/en/docs/vue-flow-form-guide)
