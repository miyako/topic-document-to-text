# topic-document-to-text

goal is to develop text extractor tools for common file formats that is compatible with permissive BSD licensing.

|format|solution|compatibility|licensing|implementation|
|:-:|-|:-:|-|-|
|pdf|[PDFium](https://github.com/PDFium/PDFium)|✅|[BSD](https://github.com/PDFium/PDFium/blob/master/LICENSE)|[pdfium-parser](https://github.com/miyako/pdfium-parser)
|pdf|[Xpdf](https://www.xpdfreader.com)|🚫|GPL||
|pdf|[poppler](https://poppler.freedesktop.org)|🚫|GPL||
|pdf|[MuPDF](https://github.com/ArtifexSoftware/mupdf)|🚫|AGPL||
|pdf|[PoDoFo](https://github.com/podofo/podofo)|⚠️|[LGPL-2](https://github.com/podofo/podofo/blob/master/COPYING)||
|docx,xlsx,pptx|[OPC](https://github.com/freuter/libopc)|✅|[BSD](https://github.com/freuter/libopc/blob/master/LICENSE)|[opc-parser](https://github.com/miyako/opc-parser)|
|eml|[GMime](https://github.com/jstedfast/gmime)|⚠️|LGPL-2.1||
|eml|[mimetic](https://github.com/tat/mimetic)|✅|[MIT](https://github.com/tat/mimetic/blob/master/COPYING)||
|eml|[libcmime](https://www.libcmime.org)|✅|MIT||
|ost,pst,pab|[libpff](https://github.com/libyal/libpff)|⚠️|[LGPL-3.0](https://github.com/libyal/libpff/blob/main/COPYING)|[pff-parser](https://github.com/miyako/pff-parser)|
|msg|[libgsf](https://github.com/GNOME/libgsf)|⚠️|LGPL-2.1||
|msg|[libolecf](https://github.com/libyal/libolecf)|⚠️|[LGPL-3.0](https://github.com/libyal/libolecf/blob/main/COPYING)||
|html|[tidy-html5](https://github.com/htacg/tidy-html5)|✅|[W3C](https://github.com/htacg/tidy-html5/blob/next/README/LICENSE.md)|[tidy-parser](https://github.com/miyako/tidy-parser)|
|html|[lexbor](https://github.com/lexbor/lexbor)|✅|[Apache 2.0](https://github.com/lexbor/lexbor/blob/master/LICENSE)|[lexbor-parser](https://github.com/miyako/lexbor-parser)|
## remarks

⚠️ conditionally compatible

LGPL 2.1 says

> Provide the object code or source code needed to relink the application with a modified version of the Library, so users can replace the Library in a statically linked or dynamically linked work.”

each repository shall provide the object code (`.a` for macOS and `.lib` for Windows) and build tools (Xcode project for macOS and Visual Studio solution for Windows) for compatibility.

✅ fully compatible

BSD or MIT is permissive. 

🚫 not compatible

GPL is copyleft; the library licensing propagates to the whole program.

### parser implementation

* CLI for macOS (`arm64` `x86_64` universal library) and Windows (`x86_64`)
* supoort both `stdIn`/`stdOut` and input/output file
* support unicode file path
* structured data in JSON
 
## next step

once we have a reasonable set of parsers, we could consider using rust-based tools for chunking.

* https://crates.io/crates/langextract-rust
* https://crates.io/crates/text-splitter

## final step

once we have a set of parsers and a tool to chunk extracted plain text, we can develop a tool that extracts, chunks, and vectorises text using [4D AIKit](https://github.com/4d/4D-AIKit). the idea is to use the offical component, not develop a custom fork.
