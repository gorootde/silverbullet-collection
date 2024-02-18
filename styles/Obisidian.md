This will make silverbullet.md look similar to Obsidian color schema. Author: @whede92

```css
::-webkit-scrollbar {
	width: 15px;
	background: rgba(0, 0, 0, 0.15);
}

::-webkit-scrollbar-track {
	background: transparent;
	border-radius: 15px;
}

::-webkit-scrollbar-thumb {
	-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.2); 
	background: hsla(0,0%,100%,.14);
} 

html {
  --ui-accent-color: #464cfc;
  --highlight-color: rgba(255, 255, 0, 0.5);
  --link-color: #69BAFD;
  --link-missing-color: #9e4705;
  --meta-color: #AC5C3E;
  --meta-subtle-color: #84D9F0;
  --subtle-color: #84D9F0;/
  --subtle-background-color: rgba(105, 105, 105, 0.1);
  --root-background-color: #1A1D22;
  --root-color: #D0D1D2;
  --top-color: #fff;
  --top-background-color: #1A1D22;
  --top-border-color: #3e3e3e;
  --top-sync-error-color: var(--top-color);
  --top-sync-error-background-color: #622626;
  --top-saved-color: #98C379;
  --top-unsaved-color: #c7c7c7;
  --top-loading-color: #c7c7c7;
  --panel-background-color: #fff;
  --panel-border-color: #fff;
  --bhs-background-color: #fff;
  --bhs-border-color: #c1c1c1;
  --modal-color: #ccc;
  --modal-background-color: #1A1D22;
  --modal-border-color: #6c6c6c;
  --modal-header-label-color: var(--ui-accent-color);
  --modal-help-background-color: #333;
  --modal-help-color: #ccc;
  --modal-selected-option-background-color: var(--ui-accent-color);
  --modal-selected-option-color: #eee;
  --modal-hint-background-color: #212476;
  --modal-hint-color: #eee;
  --modal-description-color: #aaa;
  --notifications-background-color: #333;
  --notifications-border-color: #c5c5c5;
  --notification-info-background-color: #1b76bb;
  --notification-error-background-color: #a32121;
  --action-button-background-color: transparent;
  --action-button-color: #adadad;
  --action-button-hover-color: #84D9F0;
  --action-button-active-color: #84D9F0;
  --editor-caret-color: #fff;
  --editor-selection-background-color: #d7e1f630;
  --editor-panels-bottom-color: #40BA66;
  --editor-panels-bottom-background-color: #1A1D22;
  --editor-panels-bottom-border-color: #3e3e3e;
  --editor-completion-detail-color: #555;
  --editor-completion-detail-selected-color: #d2d2d2;
  --editor-list-bullet-color: #969696;
  --editor-heading-color: #d1d1d1;
  --editor-heading-meta-color: var(--meta-subtle-color);
  --editor-hashtag-background-color: #004bbb;
  --editor-hashtag-color: #e2e9ff;
  --editor-hashtag-border-color: #007bff6b;
  --editor-ruler-color: #4c4b4b;
  --editor-naked-url-color: var(--link-color);
  --editor-link-color: var(--link-color);
  --editor-link-url-color: var(--link-color);
  --editor-link-meta-color: var(--meta-subtle-color);
  --editor-wiki-link-page-background-color: #a3bce712;
  --editor-wiki-link-page-color: var(--link-color);
  --editor-wiki-link-page-missing-color: var(--link-missing-color);
  --editor-wiki-link-color: #8f96c2;
  --editor-named-anchor-color: var(--meta-subtle-color);
  --editor-command-button-color: #fff;
  --editor-command-button-background-color: #555;
  --editor-command-button-hover-background-color: #777;
  --editor-command-button-meta-color: var(--meta-subtle-color);
  --editor-command-button-border-color: #666;
  --editor-line-meta-color: var(--meta-subtle-color);
  --editor-meta-color: var(--meta-color);
  --editor-table-head-background-color: rgba(72, 72, 72, 0.4);
  --editor-table-head-color: #eee;
  --editor-table-even-background-color: rgba(72, 72, 72, 0.3);
  --editor-blockquote-background-color: var(--subtle-background-color);
  --editor-blockquote-color: var(--subtle-color);
  --editor-blockquote-border-color: #4a4a4a;
  --editor-code-background-color: var(--subtle-background-color);
  --editor-struct-color: #B40F12;
  --editor-highlight-background-color: var(--highlight-color);
  --editor-code-comment-color: var(--meta-subtle-color);
  --editor-code-variable-color: #41a3ce;
  --editor-code-typename-color: #98C379;
  --editor-code-string-color: #986db9;
  --editor-code-number-color: #986db9;
  --editor-code-info-color: var(--subtle-color);
  --editor-code-atom-color: #61AFEF;
  --editor-admonition-note-border-color: #00b8d4;
  --editor-admonition-note-background-color: rgba(0, 184, 212, 0.2);
  --editor-admonition-warning-border-color: #ff9100;
  --editor-admonition-warning-background-color: rgba(255, 145, 0, 0.2);
  --editor-frontmatter-background-color: rgba(41, 40, 35, 0.5);
  --editor-frontmatter-color: var(--subtle-color);
  --editor-frontmatter-marker-color: #fff;
  --editor-widget-background-color: rgba(72, 72, 72, 0.5);
  --editor-task-marker-color: var(--subtle-color);
}
#sb-main .cm-textfield {
  background-color: #181A1B;
}
#sb-main .cm-button{
  background-image: linear-gradient(rgb(42, 46, 47), rgb(44, 47, 49));
#sb-main ::-webkit-scrollbar {
    background-color: #202324;
    color: #aba499;
}
```