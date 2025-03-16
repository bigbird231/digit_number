# digitnumber
A JavaScript plugin for pixelated digit numbers.<br/>
A JavaScript tool to help you easily draw digit-number on a webpage, which relies on canvas.
![image](https://github.com/user-attachments/assets/f04b38bc-0974-4965-99c5-7db484dc4035)


## Source Files Description
- digitnum.js ---- Plugin source code<br/>
- example.html ---- Example code<br/>
- readme.txt ---- Documentation<br/>
- design.png ---- Design diagram, explaining control variables in the source code

## First Example
The syntax of the plugin closely follows ECharts. The simplest usage requires only the following two lines of JavaScript code:
```
var painter = window.DigitNumber.getInstance(document.getElementById("digit-number"));
painter.draw([2,4]);
```

## Usage Notes
1. The plugin is developed based on HTML5 Canvas, so browser compatibility starts from IE9 and above.<br/>
2. The plugin attaches the `DigitNumber` property to the `window` object. If a naming conflict occurs, the plugin will fail to load.<br/>
3. The plugin listens for page resizing (`resize`) using the DOM3 event method `addEventListener`. Avoid using the DOM1 event `window.onresize` after loading the plugin, as it will override and disable the plugin's method.<br/>
4. `DigitNumber` provides only one method: `getInstance`, which takes a **DOM element with a height value** as an argument and returns a painter instance.<br/>
5. The painter instance provides four methods: `setOption`, `draw`, `clear`, and `resize`.<br/>

> **Painter Instance API Description**<br/>
> **setOption**<br/>
> *This method takes an options object to customize the painter's style. There are a total of 10 configurable parameters, which can be found in `digitnum.js` by searching for `defaultOptions`.*<br/>
> **draw**<br/>
> *This method takes an array object for drawing. For example, to draw the number 24, you should pass `[2,4]`. In addition to numbers, the plugin also supports three special symbols: `%`, `:`, and `.`. The specific usage can be seen in `example.html`.*<br/>
> **clear**<br/>
> *Calling this method will clear all content drawn by the painter. However, it will not destroy the canvas element or the painter instance.*<br/>
> **resize**<br/>
> *This method allows the painter to manually recalculate the graphic coordinates based on the dimensions of the outer element. The plugin already listens to the `window.resize` event to redraw on page resizing. This method is exposed externally to support scenarios where only internal elements are resized without resizing the entire page.*

## Plugin Advantages
1. Digit-numbers implemented using CSS+HTML cannot be made fully responsive because key triangular shapes depend on `border-width`, which does not support percentage values. The plugin, however, achieves full responsiveness.<br/>
2. Graphics are drawn using the Canvas API, avoiding unnecessary browser reflows and repaints.<br/>
3. Supports special symbols "%", ":", and decimal point formatting.<br/>

