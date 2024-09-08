This is a custom command to insert an attachment as a embed in your current cursor position
You can map this command in your `SETTINGS` to `/embed` to have it more accesible

```space-script
silverbullet.registerCommand({name: "Attachment: Embed"}, async () => {
  const byteFormatter = Intl.NumberFormat("en", {
    notation: "compact",
    style: "unit",
    unit: "byte",
    unitDisplay: "narrow",
  });
  const files = await space.listAttachments()
  const selected = await editor.filterBox(
    'Select',
    files.map((f) => {
      const size = byteFormatter.format(f.size)
      const date = new Date(f.lastModified).toLocaleString()
      return {
        name: f.name,
        description: `${date} - ${size} - ${f.contentType}`
      }
    }),
    'select a file from the list to insert a link embed in the cursor position',
    'File'
  )
  if (selected) {
    await editor.insertAtCursor(`![[${selected.name}|x400]]`)  
  }
});
```
