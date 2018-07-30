[![Published on NPM](https://img.shields.io/npm/v/@polymer/iron-a11y-keys.svg)](https://www.npmjs.com/package/@polymer/iron-a11y-keys)
[![Build status](https://travis-ci.org/PolymerElements/iron-a11y-keys.svg?branch=master)](https://travis-ci.org/PolymerElements/iron-a11y-keys)
[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://webcomponents.org/element/@polymer/iron-a11y-keys)

## &lt;iron-a11y-keys&gt;
`iron-a11y-keys` provides a cross-browser interface for processing
keyboard commands. The interface adheres to [WAI-ARIA best
practices](http://www.w3.org/TR/wai-aria-practices/#kbd_general_binding).
It uses an expressive syntax to filter key presses.

See: [Documentation](https://www.webcomponents.org/element/@polymer/iron-a11y-keys),
  [Demo](https://www.webcomponents.org/element/@polymer/iron-a11y-keys/demo/demo/index.html).

## Usage

### Installation
```
npm install --save @polymer/iron-a11y-keys
```

### In an html file
```html
<html>
  <head>
    <script type="module">
      import '@polymer/iron-a11y-keys/iron-a11y-keys.js';
    </script>
  </head>
  <body>
    <iron-a11y-keys id="keys" keys="left right down up"></iron-a11y-keys>

    <script>
      // Where to listen for the keys.
      keys.target = document.body;
      keys.addEventListener('keys-pressed', function(event) {
        console.log(event.detail);
      });
    </script>
  </body>
</html>
```
### In a Polymer 3 element
```js
import {PolymerElement, html} from '@polymer/polymer';
import '@polymer/iron-a11y-keys/iron-a11y-keys.js';

class SampleElement extends PolymerElement {
  static get properties() {
    return {
      target: {
        type: Object,
        value: function() {
          return this.$.input;
        }
      },
    }
  }

  static get template() {
    return html`
      <iron-a11y-keys id="a11y"
          target="[[target]]" keys="enter"
          on-keys-pressed="onEnter"></iron-a11y-keys>
      <input id="input" placeholder="Type something. Press enter. Check console.">
    `;
  }

  function onEnter() {
    console.log(this.userInput);
  }
}
customElements.define('sample-element', SampleElement);
```

## Contributing
If you want to send a PR to this element, here are
the instructions for running the tests and demo locally:

### Installation
```sh
git clone https://github.com/PolymerElements/iron-a11y-keys
cd iron-a11y-keys
npm install
npm install -g polymer-cli
```

### Running the demo locally
```sh
polymer serve --npm
open http://127.0.0.1:<port>/demo/
```

### Running the tests
```sh
polymer test --npm
```
