## Usage with plain JavaScript via CDN

<p>cdnjs does not provide the latest version URL, so check <a href="https://www.npmjs.com/package/@ditdot-dev/vue-flow-form">npm</a> or <a href="https://github.com/ditdot-dev/vue-flow-form">GitHub</a> for the latest version of the library.
</p>

HTML:

```html
<html>
  <head>
    <meta charset="UTF-8">
    <!-- Requires Vue version 3.x -->
    <script src="https://unpkg.com/vue@next"></script>
    <!-- Flow Form -->
    <script src="https://unpkg.com/@ditdot-dev/vue-flow-form@2.1.0"></script>
    <!-- Flow Form base CSS -->
    <link rel="stylesheet" href="https://unpkg.com/@ditdot-dev/vue-flow-form@2.1.0/dist/vue-flow-form.min.css">
    <!-- Optional theme.css -->
    <link rel="stylesheet" href="https://unpkg.com/@ditdot-dev/vue-flow-form@2.1.0/dist/vue-flow-form.theme-minimal.min.css">
    <!-- Optional font -->
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;900&amp;display=swap">
  </head>
  <body>
    <div id="app"></div>
    <script src="app.js"></script>
  </body>
</html>
```

JavaScript (content of app.js):

```js
var app = Vue.createApp({
  el: '#app',
  template: '<flow-form v-bind:questions="questions" v-bind:language="language" />',
  data: function() {
    return {
      language: new VueFlowForm.LanguageModel({
        // Your language definitions here (optional).
        // You can leave out this prop if you want to use the default definitions.
      }),
      questions: [
        new VueFlowForm.QuestionModel({
          title: 'Question',
          type: VueFlowForm.QuestionType.MultipleChoice,
          options: [
            new VueFlowForm.ChoiceOption({
              label: 'Answer'
            })
          ]
        })
      ]
    }
  }
}).component('FlowForm', VueFlowForm.FlowForm);

const vm = app.mount('#app');
```

## Project Documentation

* [Guide](https://www.ditdot.hr/en/docs/vue-flow-form-guide)
