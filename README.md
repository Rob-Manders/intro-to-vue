# Introduction Vue JS

In this project we will be using simple components and state management in Vue JS to build a simple game of 'Squash-A-Bug'.

This is only an introduction to Vue which should serve as a starting point, but will not cover all elements of Vue.

I highly recommend looking through the [Vue Documentation](https://vuejs.org/guide/introduction.html) to learn more.

This introduction uses the Vue 3 composition API and will not cover using the Options API.

## Project Setup

Install the node dependencies:

```sh
npm install
```
Run the development build:

```sh
npm run dev
```
You can now open the build in the browser using the link provided in your console.

Your browser will (usually) automatically refresh each time you save a file with your updated changes.

## 1. Build a Header Component

Let's get started building our simple header component. This component will not have any Javascript, just a template and some CSS styling.

### Build the Component

Within `src/components/Header.vue`, add some markup to the `<template>` tags for a header and sub-header.

Here is an example:

```javascript
<template>
  <header class="header">
    <h1 class="title">...</h1>
    <p class="sub-title">...</p>
  </header>
</template>
```

Next, add some styling to the `<style>` tags using CSS. You can use the example styles provided, or create your own.

The styling here is just standard CSS, but Vue projects can also be set up to use SASS or SCSS.

> The **scoped** keyword in the style tag ensures the styles will only affect this component. Without the **scoped** keyword, the styles you define in this component will be available globally to all components.
>
> I generally use scoped styles in all of my components and keep global styled seperated. There are many ways to do this, but in this project I have defined my global styles in the `src/assets/styles` folder and imported them in the `main.js` file.

### Add the Component to the App

With our component created, it's time to add it to our application.

Do do this, we first need to import our component within the `<script>` tag using a standard `import` statement.

```javascript
<script setup>
import Header from './components/Header.vue'
...
</script>
```

> We use `<script setup>` here to allow us to define our script without using a `setup()` function. This makes for much cleaner components with less boilerplate.

Once imported, we now simply need to add the component to our template.

Don't forget to close your markup with the `/` at the end of the tag.

```javascript
<template>
  <Header />
	...
</template>
```

## 2. Build the Score Board Component

With our header built, we now need to build our score component. This will take the players score in as a 'prop' and display this on screen.

### Define Props

In order to take a prop, we mush first define this within our `<script setup>` tags.

```javascript
<script setup>
const props = defineProps({ score: Number })
</script>
```

Props can be used within our scripts, or directly within our template. In this instance, we will pass this directly to our template to display.

### Use Props in a Template

We can show props between tags in our markup using double curly-braces, for example:

```javascript
<p>{{ yourProp }}</p>
```

Let's build our markup now, using the double curly-braces to include our prop:

```javascript
<template>
  <div class="score-container">
    <p class="score-header">Score</p>
    <p class="score">{{ score }}</p>
  </div>
</template>
```

Then, as we did with our header component, add some CSS styling to the `<style>` tags.

### Add the Score Component to the App

Just as we did with the Header component, we first need to import the component and add it to our template.

With this added, however, we now need to pass our prop into it. This is done with the `v-bind:` keyword like so:

```javascript
<Component v-bind:prop="variable" />

```

The variable goes directly between the quotes with no other decoration required. 

It's very rare to see `v-bind:` written directly in Vue applications though, as we typically use the shorthand `:`. We will do this on our app with our score component:

```javascript
<Score :score="score" />
```

To test this works, quickly create a `score` variable in your script. We will be replacing this later, but this will do the job for now:

```javascript
let score = 5
```

If you look at your app now, you should see the score being displayed.

## 3. Track State Using `ref()`

In the previous step, we set a variable to hold our score and pass this to our Score component. However, holding value in this way is not recommended in Vue applications as it is not considered to be reactive state.

Vue has a few methods of managing reactive state, the simplest of which is by using the `ref()` function.

The `ref()` function holds our value in an object which can be accessed vie the `.value` property.

For example:

```javascript
const state = ref('Some State')

console.log(state.value)
```

The state can be accessed, and updated, in Javascript by using the value property.

> When passing values to your template, Vue will automatically access the `.value` property on the state. This means we can pass state directyly to our template like so:
>
> ```javascript
> <p>{{ state }}</p>
> ```

### Add Score State to our App

To keep track of our score we will want to replace our score variable with a `ref()`:

```javascript
const score = ref(0)
```

If you refresh your broser, you will see the score now showing the value '0'.

### Create a Function to Update our Score

Now we have our reactive state set up, we need a method to update the score when a buch is squished. We will write a simple function within our `<script setup>` tags to do this:

```javascript
function updateScore() {
  score.value += 1
}
```

Note that we are using the `.value` property here as we are working within Javascript.

## 4. Emit and Use Events

Now we have an `updateScore` function, we need a way to trigger this in response to scoring. This brings us to events.

### Use an `@click` Event

One of the most common events you may use is a click event on a button. We will set one of these up now to test our `updateScore` function.

Create a button in your template within App.vue:

```javascript
<button>Score!</button>
```

No we want to trigger our function when it's clicked. For a click event, this is done simply by using the `@click` handler. The `@` syntax can be used for most events on elements in your template.

Let's add a click event handler to your button:

```javascript
<button @click="updateScore">Score!</button>
```

If you click the button you've created, you will see your score increment.

Go ahead and delete this button now.

### Emit a Custom Event

In addition to consuming built in events on elements in your template, you can also have your component emit custom events. This is what we will do to increase your score when a bug a squished.

To emit an event, we first need to define the events we want to emit.

Go to Bug.vue and define an emitter like so:

```javascript
const emit = defineEmits(['scored'])
```

With our emitter defined, we can now write a function to emit this event when we score:

```javascript
function score() {
  if (showing.value) {
    showing.value = false
    emit('scored')
  }
}
```

> You can pass additional arguments to the `emit()` method to forward values to the parent component, but instance we are emitting just an event as that's all we need.

### Hook Up our Events

No we have defined and can emit and event, lets hook everything up.

First, let's trigger our new `score` function when we click the bug:

```javascript
<template>
  <div class="bug-container" @click="score">
  ...
</template>
```

Now we need to add some bugs to your app. Got to App.vue, then import and add a few Bug components. Don't forget to trigger your score function with the `@scored` event.

```javascript
@scored="updateScore"
```

With that all set up, you should now have a working game of 'Squish-a-Bug'.

## 5. Conditionals and List Rendering Challenges

If you got this far, well done! Here are a couple of challenges to take it further with a couple of other essential Vue skills.

### Use `v-for` to Render Multiple Bugs

Currently, we just have several bug components in our App. Let's streamline this by having just one, and rendering several using the [v-for attribute](https://vuejs.org/guide/essentials/list).

### Use `v-if` to Build a Start Button

We don't want our game to start right away. Let's build a Start button, then have our bugs and scoreboard only show when we click the button by using the [v-if attribute](https://vuejs.org/guide/essentials/conditional.html).

We will need to track the 'started' state and hide the button if the game is started.
