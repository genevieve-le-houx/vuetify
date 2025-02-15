---
disabled: true
meta:
  title: Programmatic scrolling
  description: Programmatic scrolling within an application can be handled using the goTo method included in the vuetify object.
  keywords: programmatic scrolling, vuetify goto, goto
related:
  - /directives/scroll/
  - /styles/content/
  - /components/app-bars/
---

# Programmatic scrolling

You can programmatically trigger scrolling in your application by using the **goTo** method found on the `$vuetify` object. This method supports several different types of target selectors, and options including smooth scrolling using built-in easing functions.

<entry />

## Usage

The **goTo** method takes two parameters **target** and **options**. **target** can be either a pixel offset from the top of the page, a valid css selector, or an element reference. **options** is an object that includes **duration**, **easing**, **container**, and **offset**.

<example file="scroll/usage" />

## API

| Directive | Description |
| - | - |
| [scroll](/api/v-scroll/) | The scroll directive |

<api-inline hide-links />

## Use with router

The **goTo** function can be individually imported and invoked anywhere. This is particularly useful when hooking up to [vue-router](https://router.vuejs.org/).

```js { resource="src/router.js" }
import Router from 'vue-router'
import goTo from 'vuetify/lib/services/goto'

export default new Router({
  scrollBehavior: (to, from, savedPosition) => {
    let scrollTo = 0

    if (to.hash) {
      scrollTo = to.hash
    } else if (savedPosition) {
      scrollTo = savedPosition.y
    }

    return goTo(scrollTo)
  },
  routes: [
    //
  ],
})
```
