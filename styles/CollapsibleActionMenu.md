This Will make the ActionMenu collapsible for Mobile Devices


```space-style
/*Mobile Collabsible Menu*/
@media only screen and (max-width: 600px) {
  #sb-top .sb-actions {
    position: fixed;
    border-radius: 5px;
    border: 1px solid #444 ;
    top: 12px;
    right: 20px;
    width: 2.4rem;  /* Collapsed width */
    background: rgba(var(--root-background-color),0));
    backdrop-filter: blur(15px); /* tinted glass-like blur for the background */
    overflow: hidden;  /* Hide overflowing content */
    flex-direction: column; 
    align-items: center;
    z-index: 10; /* Ensure the buttons stay on top */
  }
  /* Button styling */
  .sb-actions button:not(.sb-code-copy-button) {
    display: block;
    height: 1.4rem; /* 1.4 */
    text-align: center;
    margin: 4px 0;
    padding: 0 0;
  }

  /* Hide all buttons except the last one */
  .sb-actions a:not(:first-of-type) {
    display: none;   
  }
  /* Show all buttons when hovering */
  #sb-top .sb-actions:hover a {
     display: block;
  }
}

```