# Lifecycle

You can be notified when a virtual node is created, updated or removed via lifecycle events. Use them for animation, data fetching, accessing the real DOM, etc.

## `oncreate`

This event is fired after the element is created and attached to the DOM. Use it to manipulate the DOM node directly, make a network request, start an animation, etc.

```jsx
function Textbox({ placeholder }) {
  return (
    <input
      type="text"
      placeholder={placeholder}
      oncreate={element => element.focus()}
    />
  )
}
```

## `onupdate`

This event is fired every time we update the element attributes. This event will fire even if the attributes have not changed. You can use `oldProps` inside the event handler to check if they changed or not.

```jsx
function Textbox({ placeholder }) {
  return (
    <input
      type="text"
      placeholder={placeholder}
      onupdate={(element, oldProps) => {
        if (oldProps.placeholder !== placeholder) {
          // Handle changes here!
        }
      }}
    />
  )
}
```

## `onremove`

This event is fired before the element is removed from the DOM. Use it for cleaning up resources, creating slide out animations, etc.

```jsx
function MessageWithFadeout({ title }) {
  return (
    <div
      onremove={element => done => fadeout(element).then(done)}>
      <h1>{title}<h1>
    </div>
  )
}
```
