# Skeleton Form

Skeleton gives you a very clean way to organize your forms.
remember the form part of the html?

```html
<form name="todo-form">
  <input type="text" placeholder="What needs to be done?" id="todo-input" />
</form>
```

Let's use skeleton to give readable structure to the javascript:

```js
Skeleton.form({
    name: 'todo-form',
    inputs: {
        text: 'todo-input'
    },
    submit: {
        input: 'text',
        keyCode: 13 // Enter Key Code
    },
    onSubmit(e) {
        let text = this.text.value;
        if(!text) {
          return;
        }
        TodosList.push({ text }); // push and render todo
        Skeleton.form.clear(this.name); // clear form input
    }
});
```

Now, the html peace and the javascript are organized in a very easy-to-understand way.
You only need to provide the 'name' of the form and its 'inputs', the 'submit' button
id or the input submitted with its key code, and an 'onSubmit' function.
> 'Skeleton.form.clear' lets you clean all the inputs text when you provide form name.
