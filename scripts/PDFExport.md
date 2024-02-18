# PDF Converter
This space script will use `pandoc` to convert markdown pages to PDFs.

Dependencies:
- [Pandoc](https://pandoc.org) is installed and in your path
- PDF engine required by Pandoc is installed (pdflatex)

Limitations:
- Exported PDF will only contain things that are directly hardcoded in your markdown. Queries or anything added dynamically by Silverbullet will not be included.
  - This limitation will be lifted as soon as [silverbulletmd/silverbullet#708](https://github.com/silverbulletmd/silverbullet/issues/708) was implemented.

```space-script
silverbullet.registerCommand({name: "Export: As PDF"}, async () => {
  
  const pageName=await syscall("editor.getCurrentPage")
  const mdFileName=`${pageName}.md`
  const pdfFileName=`${pageName}.pdf`

  await syscall("shell.run","pandoc",
    [
    //"--pdf-engine=pdflatex",
    //"-V",
    //"mainfont='WenQuanYi Micro Hei'",
    mdFileName,
    "-o",
    pdfFileName
    ]
  )
  await syscall("editor.downloadFile",pdfFileName,pdfFileName)
  
  await syscall("editor.flashNotification", "PDF Created!");
});
```
