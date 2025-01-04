# Mobile friendly collapsible (Hamburger-style) ActionMenu

## Too many ActionButtons?
Here is a solution!

These `space-style` & `space-config` converts the Menu row to a Hamburger-style menu when viewed on a mobile device (screens narrower than 600px), but it keeps the normal menu on bigger screens or in landscape mode.

## See it in action:

![Preview](https://i.postimg.cc/Dz50Rn6V/screengrab.gif)


## Here is the `space-style`:
```css
/*   Mobile Collapsible Menu V 1.2   */

/*Hide menu button in Landscape mode*/
@media only screen and (min-width: 600px) {
   .sb-actions a:first-of-type {
     display: none; 
   }
}

@media only screen and (max-width: 600px) {

/* Position the menu relative to .cm-scroller */
  .cm-scroller {
    position: relative; /* This is the positioning context */
}
#sb-top .sb-actions {
  position: absolute;  /* Now positioned relative to .cm-scroller */
  top: 3px; /* 12px from the top of .cm-scroller */
  right: 20px; /* 20px from the right edge of .cm-scroller */
  border-radius: 5px;
  border: 1px solid #444;
  width: 2.8rem;  /* Collapsed width */
  background: rgba(var(--root-background-color), 1);
  backdrop-filter: blur(20px);
  overflow: hidden;
  flex-direction: column;
  align-items: center;
  z-index: 10;  /* Ensure the buttons stay on top */
  transition: max-height 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
  max-height: 2.2rem; /* Initial collapsed height */
}

  #sb-top .sb-actions:hover {
    max-height: 33rem; /* Expanded height (adjusted for 13 buttons) */
    box-shadow: 0px 2px 15px rgba(0, 0, 0, 0.5); /* Smooth shadow on hover */
  }

  /* Button styling and size */
  .sb-actions button:not(.sb-code-copy-button) {
    display: block;
    height: 1.8rem;
    text-align: center;
    margin: 4px 0;
    padding: 4px 0;
  }

  /* Initially hide buttons */
  .sb-actions a:not(:first-of-type) {
    opacity: 0; /* Start as hidden */
    transform: translateY(-5px);  /* Slightly shifted upward */
    transition: opacity 0.05s ease-in-out 0.3s, transform 0.3s ease-in-out 0.05s;
  }

  /* Show all buttons with animation when hovering */
  #sb-top .sb-actions:hover a {
    opacity: 1;
    transform: translateY(0);
  }
}

```

For this to work properly you also need to add an empty action button as the first action button.
I also recommend hiding the Sync and Edit buttons in the space-config:

## Here is the `space-config`:
```space-config
hideSyncButton: true
hideEditButton: true

actionButtons:
- icon: more-vertical
  command: "{[]}"
  description: Open Tool Menu
```

Hope you like it & feel free to give your feedback on [Silverbullet Community Page](https://community.silverbullet.md/t/collapsible-vertical-action-menu-for-mobilescreens-but-not-only/1552/3)
