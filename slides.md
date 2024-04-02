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

## transition: slide-left

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

## <div class='pb-2'> Execution can modify the DOM/COM, causing the browser to recalculate styles and layout (reflow and repaint) – which is slow. JavaScript can also block page rendering if not handled carefully</div>

## transition: slide-left

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
---
transition: slide-left
---
<h1> Turbo Streams </h1>

<div class='flex flex-col'>
  <strong> How it works </strong>
  <p> Turbo Streams similar to Turbo Frames, are special HTML elements that wraps the HTML we wanna deliver to our frontend. <br /> They differ from Turbo Frames in a couple aspects: </p>
  <ul>
    <li> Streams allow us to update multiple, unrelated parts on the page. </li>
    <li> While Turbo Frames only allow us to replace/morph a frame, Streams gives us greater controller over the page behavior with 9 different actions. </li>
    <li> Streams can integrate with asynch transports such as WebSockets or SSE to allow async delivery to the browser. </li>
    <li> A Common misconception about Turbo Streams is that they only work with WebSockets, that's not true, streams work with the classic HTTP responses, that means we can use streams with normal CRUD requests (POST, PATCH, GET, DELETE). </li>
  </ul>
</div>
---
transition: slide-left
---
<h1> Turbo Stream Actions: </h1>
<ul>
  <li>Append: Appends the stream content to the targeted element.</li>
  <li>Prepend: Prepends the stream content to the targeted element.</li>
  <li>Replace: Replaces the targeted element with the stream content.</li>
  <li>Update: Updates the targeted element content with the stream content.</li>
  <li>Remove: Removes the targeted element.</li>
  <li>Before: Inserts the stream content before the targeted element.</li>
  <li>After: Inserts the stream content after the targeted element.</li>
  <li>Morph: Replaces the element designated by the target dom id via morph. (only available in turbo >= 8.0.5)</li>
  <li>Refresh: Initiates a Page Refresh to render new content with morphing. (only available in turbo >= 8.0.0)</li>
</ul>
---
transition: slide-left
---
<h1> Broadcasting and Turbo Stream Source element</h1>
<p>Turbo can connect to any form of stream to receive and process stream actions as long as the stream source provides a JS adapter that listens to incoming messages from the server and dispatches a MessageEvent on the frontend that contain the stream action (aka a stream element) in the data attribute of said event.<br/> Rails' preferred method of streaming Turbo stream actions is through WebSockets, the <code>turbo-rails</code> gem ships with a cable adapter implemented in the form of a yet another special element called <code>TurboCableStreamSourceElement</code>, it also ships with a ruby helper <code>turbo_stream_from</code> to render said element.</p>
<p>Other tools such as mercure (real-time SSE communications client) or Anycable (A Go WS client) implement the same paradiagm to serve as an alternative streaming source for Turbo Stream Actions</p>
---
transition: slide-left
---
<h1>Anycable</h1>
<p>AnyCable is a high-performance WebSocket server designed to replace Action Cable as the real-time communication solution for Ruby on Rails applications. It's written in Go for optimal performance and leverages gRPC for efficient internal communication between itself and puma.</p>
  <div>
    <strong>Why Anycable?</strong>
    <ul>
      <li>Guaranteed Message Delivery: Provides a durable mechanism for message persistence.</li>
      <li>Enhanced Scalability: The combination of Redis as a memory broker and AnyCable's Go-based architecture allows for efficient horizontal scaling.</li>
    </ul>
  </div>
  <div class='flex items-center justify-center absolute top-35 left-50'>
    <img src="/anycable.svg" class="h-[500px] w-[500px]" />
  </div>
---
transition: slide-left
---
<h1> Morph!! </h1>
<div class='flex flex-row gap-15'>
<div class='w-1/3'>
<p>The "Morph DOM algorithm" mirrors the concept of morphing from graphics in web development, transforming HTML elements by identifying the minimal changes needed for a seamless transition between DOM states. It compares current and desired DOM trees, calculating the least operations—like adding, removing, or updating elements and attributes—to efficiently achieve the new state.</p> 
</div>
<div>
<div class='flex items-center justify-center absolute top-10'>
  <img src="/morphdom.svg" class="h-[500px] w-[500px]" />
</div>
</div>
</div>
