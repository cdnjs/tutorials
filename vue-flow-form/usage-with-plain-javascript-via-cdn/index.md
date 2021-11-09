## Usage with plain JavaScript via CDN

<p>cdnjs does not provide the latest version URL, so check <a href="https://www.npmjs.com/package/@ditdot-dev/vue-flow-form">npm</a> or <a href="https://github.com/ditdot-dev/vue-flow-form">GitHub</a> for the latest version of the library.
</p>

HTML:

```html
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/3.2.20/vue.global.prod.min.js"></script>
    <!-- Flow Form -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vue-flow-form/2.1.0/vue-flow-form.umd.min.js"></script>
    <!-- Flow Form base CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/vue-flow-form/2.1.0/vue-flow-form.min.css">
    <!-- Optional theme.css -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/vue-flow-form/2.1.0/vue-flow-form.theme-minimal.min.css">
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
