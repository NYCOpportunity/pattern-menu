# Menu Pattern

The Menu Pattern is a sliding menu that contains the navigation items that do not fit within the [Navigation Pattern](https://github.com/NYCOpportunity/pattern-navigation) in mobile view ports. It uses the [Patterns Scripts toggle utility](https://github.com/CityOfNewYork/patterns-scripts/tree/main/src/toggle) to achieve the showing and hiding effects. The animation for the sliding uses CSS and will be disabled by devices using the [prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion) @media query.

The menu element will be hidden from screen readers using the `aria-hidden` attribute and potentially focusable children will have their tabindex set to `-1` when the modal is hidden. When the menu is opened, focus will shift from the `data-js-menu="open"` trigger to the `data-js-menu="close"` trigger inside the menu. The focus will be trapped, meaning tabbing focus will cycle through elements within the menu.

## Usage

### Installation

```shell
$ npm install @nycopportunity/pattern-menu
```

### ES Module

The pattern uses JavaScript to sho This method is a wrapper around the [Patterns Scripts toggle utility](https://github.com/CityOfNewYork/patterns-scripts/tree/main/src/toggle) which is included as a dependency of this project. The utility can be imported as an ES module and instantiated.

```javascript
import Menu from '@nycopportunity/pattern-menu/src/menu';

new Menu();
```

### Styles

The Menu Pattern includes two stylesheets. One that sets default design tokens and display properties using [CSS Custom Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties) and one that applies the tokens to the menu CSS selectors. The tokens can be used as is or overridden.

```scss
@import '@nycopportunity/pattern-menu/src/tokens';
@import '@nycopportunity/pattern-menu/src/menu';
```

### Markup

#### Opening Trigger

The following markup is the minimum required for an opening trigger of the Menu.

```html
<button data-js="menu" data-js-menu="open" aria-controls="aria-c-menu" aria-expanded="false">
  Open Menu
</button>
```

Attribute                    | Description
-----------------------------|-
`data-js="menu"`             | Adds the toggling utility to open the menu.
`data-js-menu="open"`        | Indicates that this is the primary opening button for the menu. Focus will shift from the close button to the open button when the menu is closed.
`aria-controls`              | Targets the Menu ID for toggling.
`aria-expanded="true/false"` | Indicates to screen readers that the button is active or not. This attribute will be toggled when the trigger is clicked.

#### Menu

The menu ID should be same as the `aria-controls` attribute for the opening and closing trigger.

##### Potentially Focusable Elements

The script uses the [toggling utility](https://github.com/CityOfNewYork/patterns-scripts/tree/main/src/toggle#attributes) from the Patterns Scripts library. Potentially focusable elements inside the menu will need to have their `tabindex` set to `-1` before the menu is toggled open. A full list of elements can be found in the documentation for the Toggle Utility.

```html
<aside id="aria-c-menu" class="o-menu" aria-hidden="true">
  <!-- aria-label Ensures landmarks are unique -->
  <nav class="o-menu__nav" aria-label="Mobile Menu">
    <!-- tabindex Add tabindex="-1" to insure focusable elements are not visible when parent is hidden -->
    <a class="o-menu__nav-item" tabindex="-1" href="/">Home</a>

    <a class="o-menu__nav-item" tabindex="-1" href="/programs">Programs</a>

    <a class="o-menu__nav-item" tabindex="-1" href='/newsletter'>Newsletter</a>

    <!-- Focus will be trapped inside the menu. The text for the closing menu should be descriptive for screen readers -->
    <button tabindex="-1" data-js="menu" data-js-menu="close" aria-controls="aria-c-menu" aria-expanded="false">
      Close and return to site
    </button>
  </nav>
</aside>
```

#### Closing Trigger

The closing trigger should have the same attributes as the opening trigger, however, `data-js-menu` should be set to `close`. The closing trigger inside the menu should be placed towards the bottom of the menu to assist with thumb reach. Once the opening trigger is clicked focus will shift to the closing trigger and then the focus will be trapped inside the menu.
