# animation-proto
## Substitute function for animation without GSAP

### Rules for `HTML`
- frame div needs to have the `.js-frame` class and `data-transition-added="false` attribute  
`<div class="frame js-frame" data-transition-added="false">`
- for making the animateed frame with inner elements fading in one after another add `js-fadeIn` class and additional
class `js-fadeOrder-1` with and incrementing number at the end. This number is presenting the order in which user wants
multiple elements to appear:  
```
  <div class="frame__heading js-fadeIn js-fadeOrder-1">Frame 2 heading</div>
  <div class="frame__subheading js-fadeIn js-fadeOrder-2">Frame 2 subheading</div>
  ```
### Required `CSS` code
```
.js-frame { transition: 1s all; }

.js-fadeIn { opacity: 0; }

.frame.frame--show .js-fadeIn {
    animation-name: fadeIn;
    animation-duration: 4s;
    animation-fill-mode: forwards;
}

/* We can add as many elements as needed and just use animation-delay to set the time when they will appear */
.frame.frame--show .js-fadeOrder-2 { animation-delay: 1s; }
.frame.frame--show .js-fadeOrder-3 { animation-delay: 2s; }

.frame--show { opacity: 1; }

@-webkit-keyframes fadeIn {
    from {opacity: 0;}
    to {opacity: 1;}
}

@keyframes fadeIn {
    from {opacity: 0;}
    to {opacity: 1;}
}```
