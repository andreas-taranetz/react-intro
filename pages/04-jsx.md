---
layout: section
---

# What if there's a better way?

---

# A better way to write react components <span v-click="1">with JSX</span>

We usually put each component in a separate file named after the component

````md magic-move {lines: true}
```js
function HelloWorld() {
  return React.createElement(
    'div',
    { id: 'boring-example' },
    'Hello World'
  )
}
```

```js
function HelloWorld() {
  return (
    <div id='boring-example'>
      Hello World
    </div>
  )
}
```
````

<div v-click mt-10>

⚠️ A build step is required to transform **JSX** into regular **JS** code which will use `createElement` calls

</div>

---
layout: two-cols
---

# Class Component

the old way

<div mr-10>
```js
class MyComponent extends React.Component {
  render() {
    return (
      <div>
        <h1>This is the old way</h1>
        <p>You might see this in older docs</p>
      </div>
    );
  }
} 
```
</div>

`render` is just one of many functions a component could override

::right::

# Function Component

the modern way

```js
function MyComponent() {
  return (
    <div>
      <h1>This is the new way</h1>
      <p>Much recommended</p>
    </div>
  );
} 
```

introduced in React version 16

---

# What is `React.createElement()` doing?

Inputs:

`type` React component type: tag name (`div`, `span`, ...) or other React component names

`props` Object or null

`children` optional list of child nodes

<v-click>

```js {monaco-run} 
import { createElement } from "react"

console.log(createElement("span", { className: 'bg-red' }, 'Hello World'))
```

</v-click>

---
layout: two-cols
---

# How pixels are made

<v-click>

1. **Trigger**
    - _making an order_
    - during initial render → start at root
    - when state updates → start where the update occured
</v-click>

<v-click>

2. **Render Phase** <small>done by React</small>
    - _cooking the new components_
    - create / update the virtual DOM
    - check for differences to the current tree
</v-click>

<v-click>

3. **Commit Phase** <small>done by ReactDOM</small>
    - _serving the DOM to the browser_
    - create / update / delete DOM elements
    - only those that actually need to change
</v-click>

<v-click>

4. Browser is _painting_ pixels on the screeen
</v-click>

<small>see also [react.dev/learn/render-and-commit](https://react.dev/learn/render-and-commit)</small>

::right::

<div ml-10 flex flex-col gap-3>
<img v-click=1 width="150" alt="" src="https://react.dev/images/docs/illustrations/i_render-and-commit1.png">
<img v-click=2 width="150" alt="" src="https://react.dev/images/docs/illustrations/i_render-and-commit2.png">
<img v-click=3 width="150" alt="" src="https://react.dev/images/docs/illustrations/i_render-and-commit3.png" title="Commit phase"/>
</div>

---

# More on JSX / TSX

A typical component

```tsx
import Logo from "./Logo";

type PageHeaderProps = {
  title: string;
}

function PageHeader(props: PageHeaderProps) {
  return (
    <div>
      <Logo />
      <h2>You are on page: {props.title}</h2>
    </div>
  );
}

export default PageHeader;

// within another component
...
<PageHeader title={"Home"} />;
...
```

---
layout: two-cols
---

# Allowed in JSX / TSX

<span/>

![Expressions](/expressions.png)

::right::

<div mt-14 ml-5>

Other React components

Built in components like HTML elements

Expressions within `{}` e.g.

`<h1>{"Hi" + props.name}<h1>`

Expressions can also return React components as their result, e.g.:

`{guests.map((g) => <Greet name={g.name}/>}`
</div>