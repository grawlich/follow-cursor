# Cursor Follow


> [!NOTE]
> *This project was originally created Mar. 7th, 2023 and recently updated.*


This is a small component built using:

- [SvelteKit (Svelte 5)](https://github.com/sveltejs/kit) (Front-end UI)


> [!WARNING]
> Due to this being a simple component, no support is provided at this time. Updates will come as I deem necessary, but for the foreseeable future, this is how the component will remain.


[Demo](https://follow-cursor-six.vercel.app/)


### Purpose:


Generates an element that automatically follows the mouse cursor around the page with variable delay and animation fill direction.


---


### How to use in your own project


The code for having the element follow the mouse cursor is contained entirely within the Svelte component, minus the demo styles used. All you need to do is simply copy/paste the `FollowCursor.svelte` component into your project, and add a global class to style it! You can add multiple copies if needed and modifying this element is quite simple.


The component only outputs a `<div>` tag and a window event listener to handle detecting mouse movement. It uses native JavaScript APIs to smoothly animate from the current position to the new position, and it even follows the vague curavture of you movements with a long delay.


The default delay is `8000` (8 seconds in milliseconds) and tha can be adjusted via the `duration` prop.

```svelte
<!-- Increase delay to 12 seconds -->
<FollowCursor duration={12000} />
```


Classes are passed by `...restProps`. You can technically insert any arbitrary HTML attribute into this, so anything you need to apply can just be added.


Usage:

```svelte
<FollowCursor
  duration={3000}
  class="dot"
/>
```


---


### Anatomy


Props:

`duration` - *Default: 8000 (8 seconds in milliseconds);* The length of time it takes for the element to animate to the current mouse position.<br>
`fill` - *Default "forwards";* The direction of the animation playback.<br>
`...restProps` - Any arbitrary HTML attributes that can be applied to a `<div>` tag, like `class`.


Example:

```svelte
<FollowCursor
  duration={3000}
  fill="both"
  class="dot"
  id="dot1"
/>
```


---


### Other frameworks

This is a very basic component, all things considered. Porting it to vanilla JavaScript is trivial.

```javascript
// Target element
const blob = document.body.querySelector(".blob");


// Mouse move event listener
document.body.onpointermove = event => {
  // Get cursor position
  const {
    clientX,
    clientY
  } = event;

  // Animate target element properties
  blob.animate({ 
    left: `${clientX}px`,
    top: `${clientY}px`
  }, { duration: 8000, fill: 'forwards' });
};
```

For the output, simply use your framework's own syntax to create the required reactivity and HTML output. Many frameworks offer similar tools to Svelte for doing this.

I will update this section at a later time with more in-depth examples if folks really want a guide for their specific framework.


---


### License


Code is MIT licensed

Copyright © 2025 - 2026 [grawlich](https://github.com/grawlich)
