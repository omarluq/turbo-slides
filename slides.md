---
theme: dracula
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Turbo
drawings:
  persist: false
transition: slide-left
title: Turbo
mdc: true
---
<div class='flex flex-col gap-3 content-center'>
  <img src="/turbo-logo.svg" class="h-60" />
  <h1> Turbo </h1>
</div>

---
transition: slide-left
---

<div class='flex flex-col items-center justify-center'>
  <h1> Presented By </h1>
  <img src="/IMG_1997.jpg" class="h-40 rounded-full" />
  <h2 class='text-2xl font-bold mt-3'>Omar Luq</h2>
  <p class='text-lg'>Software Engineer</p>

  <div class='flex flex-row gap-4 mt-4'>
    <a href="https://github.com/omarluq" target="_blank" class="no-underline">
      <Item text="mygithub">
        <CarbonLogoGithub />
      </Item>
    </a>
    <a href="linkedinhttps://www.linkedin.com/feed/" target="_blank" class="no-underline">
      <Item text="sli.dev">
        <CarbonLogoLinkedin />
      </Item>
    </a>
  </div>
</div>
---
transition: slide-left
---
<h1> Here is the thing </h1>

<div class='flex flex-row'>
<div class='w-1/3'><span style="color: #007bff;">🤔</span> Full-page refreshes aren't slow because of giant HTML files. The real culprit is the constant re-execution of your site's CSS and JavaScript.</div>
<div>
<div class='flex items-center justify-center absolute top-10'>
  <img src="/http-browser.svg" class="h-[500px] w-[500px]" />
</div>
</div>
</div>
---
transition: slide-left
---
<h1>  Why CSS and JavaScript Hurt Performance </h1>

<strong> CSS: The Rendering Burden: </strong>
<div class='pb-2'> The browser must build the CSS Object Model (COM), figuring out the styles for every element. Then, it combines this with the DOM to create the Render Tree, which is used to paint pixels on the screen.</div>

<strong> JavaScript: The Execution Overhead:</strong>
<div class='pb-2'> Execution can modify the DOM/COM, causing the browser to recalculate styles and layout (reflow and repaint) – which is slow. JavaScript can also block page rendering if not handled carefully</div>
---
transition: slide-left
---
<h1> Turbo to the Rescue </h1>

<div class='flex flex-row gap-15'>
<ul class='w-1/3'>
<li>Eliminates bottlenecks: Maintains a persistent process to avoid constant CSS/JavaScript reloads.</li>
<li>Smart interception: Intercepts user actions to prevent full page refreshes.</li>
<li>Targeted updates: Only replaces the parts of the page that actually change.</li>
</ul>
<div>
<div class='flex items-center justify-center absolute top-10'>
  <img src="/turbo-drive.svg" class="h-[500px] w-[500px]" />
</div>
</div>
</div>
---
transition: slide-left
---
<h1> The Power Trio: Drive, Frames, Streams </h1>

<div class="flex flex-col"> 
  <div>
    <strong>Turbo Drive: The Navigator</strong>
    <ul>
      <li>Handles link clicks, form submissions, and manages browser history updates. </li>
      <li>The foundation of Turbo that intercepts traditional web behavior. </li>
    </ul>

  </div>

  <div>
    <strong>Turbo Frames: The Delimiters</strong>
    <ul>
      <li> Define sections of a page that Turbo can update independently. </li>
      <li> Key for achieving those fast partial page updates. </li>
    </ul>

  </div>

  <div>
    <strong>Turbo Streams: The Livewire</strong>
    <ul>
      <li>Surgically target specific portions of the page for updates.</li>
      <li>Enable real-time updates using WebSockets (and more!)</li>
      <li>Perfect for live chats, notifications, dashboards, and anywhere granular changes matter.</li>
    </ul>
  </div>
</div>
