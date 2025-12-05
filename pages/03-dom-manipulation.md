---
layout: section
---

# What is our main issue when building web based UIs?

---
layout: center
zoom: 1.3
---

Me: "Can we have DOM manipulation?"

Mom: "We have DOM manipulation at home"

<span v-click>
DOM manipulation at home: <logos-jquery m-1/>
</span>

---

<style>
.bg-red{
 background: red;
}
</style>

# Manipulate the DOM without any libaries

```js {monaco-run} {autorun:false}
const root = document.getElementById("root");

console.log(root.textContent);
//console.log(root.outerHTML)
```

<div id="root" class="my-10 border">
    🚧 Root div under construction 🚧
</div>

<div v-click>

```js {monaco-run} {autorun:false}
const root = document.getElementById("root");

const span = document.createElement("span");
span.textContent = ["🙈", "🙊", "🙉"].at(Math.random() * 3);
span.className = "bg-red";

root.append(span);
```

</div>

---

# Let's do this using React

````md magic-move {lines: true}
```js
const root = document.getElementById("root");

const span = document.createElement("span");
span.textContent = "Hello World";
span.className = "bg-red";

root.append(span);
```

```js {1,2|6-8}
import React from "react";
import ReactDOM from "react-dom/client";

const root = document.getElementById("root");

const span = document.createElement("span");
span.textContent = "Hello World";
span.className = "bg-red";

root.append(span);
```

```js {6-10|4}
import React from "react";
import ReactDOM from "react-dom/client";

const root = document.getElementById("root");

const SpanComponent = React.createElement(
  "span",
  { className: "bg-red" },
  "Hello World",
);

root.append(span);
```

```js {4|12}
import React from "react";
import ReactDOM from "react-dom/client";

const appRoot = ReactDOM.createRoot(document.getElementById("root"));

const SpanComponent = React.createElement(
  "span",
  { className: "bg-red" },
  "Hello World",
);

root.append(span);
```

```js {12|*}
import React from "react";
import ReactDOM from "react-dom/client";

const appRoot = ReactDOM.createRoot(document.getElementById("root"));

const SpanComponent = React.createElement(
  "span",
  { className: "bg-red" },
  "Hello World",
);

appRoot.render(SpanComponent);
```
````

---

<style>
.bg-red {
 background: red;
}
</style>

# Demo time

```js {monaco-run} {autorun:false}
import React from "react";
import ReactDOM from "react-dom/client";

const appRoot = ReactDOM.createRoot(document.getElementById("root2"));

const SpanComponent = React.createElement(
  "span",
  { className: "bg-red" },
  "Hello World",
);

appRoot.render(SpanComponent);
```

<div id="root2" class="my-10 border">
    🚧 Root div under construction 🚧
</div>

---

<style>
.bg-red{
 background: red;
}

.spaced-out {
    display: flex;
    justify-content: space-around;
}
</style>

# Demo time with composition

```js {monaco-run} {autorun:false}
import React from "react";
import ReactDOM from "react-dom/client";

const appRoot = ReactDOM.createRoot(document.getElementById("root3"));

const SpanComponent = React.createElement(
  "span",
  { className: "bg-red" },
  "Hello World",
);
const TextBlock = React.createElement("p", { className: "spaced-out" }, [
  SpanComponent,
  SpanComponent,
  SpanComponent,
]);

appRoot.render(TextBlock);
```

<div id="root3" class="my-10 border">
    🚧 Root div under construction 🚧
</div>

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
layout: section
---
# How pixels are made

<small abs-br m-5>
The next slide is a bit graphic
</small>

---
layout: two-cols
zoom: 1.2
---

1. **Trigger**
    - _"making an order"_
    - initial render → start at root
    - state updates → start where the update occured

<v-click>

2. **Render Phase** <small>done by React</small>
    - _"cooking the new components"_
    - create / update the virtual DOM
    - check for differences to the current tree
</v-click>

<v-click>

3. **Commit Phase** <small>done by ReactDOM</small>
    - _"serving the DOM to the browser"_
    - create / update / delete DOM elements
    - only those that actually need to change
</v-click>

<v-click>

4. Browser is _painting_ pixels on the screen
</v-click>

::right::

<div ml-15 flex flex-col gap-3>
<img width="120" alt="" src="https://react.dev/images/docs/illustrations/i_render-and-commit1.png">
<img v-click=1 width="120" alt="" src="https://react.dev/images/docs/illustrations/i_render-and-commit2.png">
<img v-click=2 width="120" alt="" src="https://react.dev/images/docs/illustrations/i_render-and-commit3.png" title="Commit phase"/>
</div>

<small v-click=3>
see also <a href="https://react.dev/learn/render-and-commit">react.dev/learn/render-and-commit</a>
</small>

---