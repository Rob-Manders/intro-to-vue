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
const score = 5
```

If you look at your app now, you should see the score being displayed.

## 3. Track State Using `ref()`



## 4. Output an Event
