---
layout: section
---

# What if there is a better way to write components?

---

# A better way to write react components <span v-motion :initial="{opacity: 0}" :click-1="{opacity: 1}">with JSX</span>

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

# JSX + TypeScript = TSX

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

```

```tsx
// within another component
...
<PageHeader title={"Home"} />;
...
```

---
layout: image-left
image: /expressions.png
backgroundSize: contain
---

## Allowed in JSX / TSX

<span/>

- Other React components
- Built in components like HTML elements
- Expressions within `{}` e.g.:
  * `<h1>{"Hi" + props.name}<h1>`
  * `{count > 1 ? 'likes' : 'like'}`


<div mt-2 v-click>
<small>
Expressions can also return React components as their result, e.g.:
</small>

```
{guests.map((g) => <Greet name={g.name}/>)
```
</div>

<div mt-10 v-click>
<strong>But no statements</strong>

- if
- switch
- for
</div>