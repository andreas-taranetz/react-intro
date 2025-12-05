---
layout: section
transition: view-transition
---

# Why are we building websites? {.inline.view-transition-title}

---
clicks: 1
---

## Why are we building websites? {.inline.view-transition-title}

<section text-6xl mt-30 text-center>
<span inline-block
  v-motion
  :initial="{x: 118}"
  :click-1="{x: -14}">to provide</span>
<span inline-block 
  v-motion
  :initial="{opacity: 0}"
  :click-1="{opacity: 1}">interactive</span>
<span inline-block
  v-motion
  :initial="{x: -118}"
  :click-1="{x: 14}">content</span>
<br/>
<button @click="$slidev.nav.next" title="Next slide" class="slidev-icon-btn" v-motion :initial="{opacity: 1}" :click-1="{opacity: 0}">
  <carbon:caret-right />
</button>
</section>

---

<img m-auto src="https://imgs.xkcd.com/comics/installing.png">

But still, my scheme for creating and saving user config files and data locally to preserve them across reinstalls might be useful for--wait, that's cookies.

---

# Websites provide a common platform

to render pixels on all kinds of screens

<section mt-20 flex justify-center gap-20>
<logos-html5 w-40 h-40
  v-motion
  :initial="{x: -500}"
  :enter="{x: 0, transition: {delay: 500}}"/>
<logos-css3 w-40 h-40
  v-motion
  :initial="{y: 500}"
  :enter="{y: 0, transition:{ delay: 1000}}"/>
<logos-javascript w-32 h-32 mt-8
  v-motion
  :initial="{x: 500}"
  :enter="{x: 0, transition: {delay: 1700}}"/>
</section>

---
layout: section
transition: view-transition
---

# When and where do we render the HTML, CSS and JS? {.inline.view-transition-title}

---

## When and where do we render the HTML, CSS and JS? {.inline.view-transition-title}

There are so many options

<v-clicks mt-10 text-xl>

- Server side rendering (SSR) <small ml-5>← how the web worked in the beginning</small>
- Client side rendering (CSR) <small ml-5>← how <logos-angular/> and <logos-react/> worked in the beginning</small>
- Static site generation (SSG) <small ml-5>← how <logos-astro/> / <logos-eleventy/> / <logos-hugo/> / <logos-jekyll/> work </small>
- All of the above <small ml-31>← how most of the web should work</small>
</v-clicks>

<img abs-br src="/why-not-both.png" width=400 v-click=4>

---

## It depends...

on your specific use case

<v-clicks text-xl>

- How often is your content changing
- How personalized is the content
How big is your website / individual pages
- How much compute is available
- How high is the bandwidth
- Does it need to work without <logos-javascript />
</v-clicks>

<img abs-tr m-5 v-click=1 width=500 src="/dimensions.png"/>
