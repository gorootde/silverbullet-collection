# Selection to CodeBlock toggle

## What does it do:
This script will wrap the current selections in code block delimiters.
When you trigger it either by command or by your shortcut key:
* If the selection is not wrapped, it will add the delimiters (e.g., ```bash).
* If the selection is already wrapped, it will recognize the delimiters and remove them.

This script makes your workflow intuitive and saves you time when editing. No more manually removing ```bash lines and backticks when you want to undo a code block!

## How to use it:

![Preview](https://i.postimg.cc/JnxMF04Z/Screenrecording.gif)

## Customization:
Want a different language?
Just change the CODE_BLOCK_SYNTAX constant at the top of the script. Super simple!

* `CODE_BLOCK_SYNTAX = "bash";`

Change also the Name and Shortcut-Keys for your use case:
* `name: "Selection to Bash"`
* `key: "Alt-Cmd-1"`

## Here’s the `space-script`:

```typescript
//-------------------Toggle selection to Codeblock--------------------
silverbullet.registerCommand({
  name: "Selection to Bash",
  key: "Alt-Cmd-1"
}, async () => {
  // Define the syntax for the code block to add
  const CODE_BLOCK_SYNTAX = "bash"; // Change this to your desired language

  // Get the current selection and editor content
  const selection = await syscall("editor.getSelection");
  const from = selection.from;
  const to = selection.to;
  const content = await syscall("editor.getText");
  const lines = content.split("\n");

  // Determine the start and end line numbers of the selection
  const startLine = content.slice(0, from).split("\n").length - 1;
  const endLine = content.slice(0, to).split("\n").length - 1;

  // Get the line above and below the selection
  const lineAboveIndex = Math.max(startLine - 1, 0);
  const lineBelowIndex = Math.min(endLine + 1, lines.length - 1);
  const lineAbove = lines[lineAboveIndex]?.trim();
  const lineBelow = lines[lineBelowIndex]?.trim();

  // Check for existing delimiters with a wildcard for code block names (including hyphens)
  const delimiterPattern = /^```([\w-]+)?$/;  
  const startsWithDelimiter = delimiterPattern.test(lineAbove);
  const endsWithDelimiter = lineBelow === "```";

  if (startsWithDelimiter && endsWithDelimiter) {
    // If the selection is already wrapped, remove the delimiters
    const startOfLineAbove = content.split("\n").slice(0, lineAboveIndex).join("\n").length + (lineAboveIndex > 0 ? 1 : 0);
    const endOfLineBelow = content.split("\n").slice(0, lineBelowIndex + 1).join("\n").length;

    await syscall("editor.dispatch", {
      changes: [
        { from: startOfLineAbove, to: startOfLineAbove + lineAbove.length + 1, insert: "" },
        { from: endOfLineBelow - "\n```".length, to: endOfLineBelow, insert: "" },
      ],
    });
  } else {
    // Otherwise, add the new delimiters around the selection
    const beforeSelection = content.slice(0, from);
    const afterSelection = content.slice(to);

    // Find the line boundaries for adding delimiters
    const startOfLineBefore = beforeSelection.lastIndexOf("\n") + 1;
    const endOfLineAfter = to + (afterSelection.indexOf("\n") === -1 ? afterSelection.length : afterSelection.indexOf("\n"));

    await syscall("editor.dispatch", {
      changes: [
        { from: startOfLineBefore, to: startOfLineBefore, insert: `\`\`\`${CODE_BLOCK_SYNTAX}\n` },
        { from: endOfLineAfter, to: endOfLineAfter, insert: "\n```" },
      ],
    });
  }
});
```

Hope this makes your workflow smoother!  

Feedback and ideas are welcome on [Silverbullet Community Page](https://community.silverbullet.md/t/space-script-selection-bash-codeblock/1544)

Happy silverbulleting 🚀 !
