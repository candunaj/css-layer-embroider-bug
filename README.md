# layer-test-2

This is a demo app to show a bug in embroider when using CSS layers.

When you specify CSS layers at the top of `app.css` then imports below it disappear in the production build. The development build works as expected (nothing is removed from app.css).

So when you specify the following `app.css` file

```css
/* app.css */
@layer base, components;
@import 'global.css' layer(base);

h1{
  color: red;
}
```

when you run `ember serve --environment=production` then you get the following `app.css` in the `dist/assets` directory:

```css
/* app.css */
@layer base, components;
h1{
  color: red;
}
```
> Import disappeared!

When you move defining layers under the imports then everything works as expected and nothing is removed from `app.css`

## Prerequisites

You will need the following things properly installed on your computer.

* [Git](https://git-scm.com/)
* [Node.js](https://nodejs.org/) (with npm)
* [Ember CLI](https://cli.emberjs.com/release/)
* [Google Chrome](https://google.com/chrome/)

## Installation

* `git clone <repository-url>` this repository
* `cd layer-test-2`
* `npm install`

## Running / Development

* `ember serve`
* Visit your app at [http://localhost:4200](http://localhost:4200).
* Visit your tests at [http://localhost:4200/tests](http://localhost:4200/tests).

### Code Generators

Make use of the many generators for code, try `ember help generate` for more details

### Running Tests

* `ember test`
* `ember test --server`

### Linting

* `npm run lint`
* `npm run lint:fix`

### Building

* `ember build` (development)
* `ember build --environment production` (production)

### Deploying

Specify what it takes to deploy your app.

## Further Reading / Useful Links

* [ember.js](https://emberjs.com/)
* [ember-cli](https://cli.emberjs.com/release/)
* Development Browser Extensions
  * [ember inspector for chrome](https://chrome.google.com/webstore/detail/ember-inspector/bmdblncegkenkacieihfhpjfppoconhi)
  * [ember inspector for firefox](https://addons.mozilla.org/en-US/firefox/addon/ember-inspector/)
