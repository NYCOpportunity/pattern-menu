The Menu Pattern is an `aside` element that slides in from the end of the screen. It contains the Navigation items that do not fit within the [Navigation Pattern](navigation) in mobile viewports. It uses the <a href="https://github.com/CityOfNewYork/patterns-scripts/tree/main/src/toggle" target="_blank" rel="noopener nofollow">Patterns Scripts toggle utility</a> to achieve the showing and hiding effects. The animation for the sliding uses CSS and will be disabled by devices using the <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion" target="_blank" rel="noopener nofollow">prefers-reduced-motion</a> `@media` query.

---

The Menu element will be hidden from screen readers using the `aria-hidden` attribute, and potentially focusable children will have their `tabindex` attribute set to `-1` when the Menu is hidden. When the Menu is open, the focus will shift from the "Menu" button to the "Close" button inside the Menu. After this event, the focus will be trapped, meaning the tabbing will cycle through elements within the Menu.

The opening "Menu" button must have the `data-js-menu="open"` attribute. The closing button must have the `data-js-menu="close"` attribute.

---

We recommended placing the Menu element inside the [Navigation Pattern](navigation) next to the Menu button.

---

We recommended placing the Close button in the Menu before the nav items.

---

Use the `aria-label="Menu"` attribute on the `nav` element inside the Menu distinguish the `nav` element from others.

---

The Menu below is displayed block for demonstration purposes. You must add the `o-menu-fixed` next to the `o-menu` class when you use this pattern in production.
