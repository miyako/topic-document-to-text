# topic-document-to-text

goal is to develop text extractor tools for common file formats that is compatible with permissive BSD licensing.

|format|solution|compatibility|licensing|implementation|
|:-:|-|:-:|-|-|
|pdf|[PDFium](https://github.com/PDFium/PDFium)|✅|[BSD](https://github.com/PDFium/PDFium/blob/master/LICENSE)|[pdfium-parser](https://github.com/miyako/pdfium-parser)
|pdf|[Xpdf](https://www.xpdfreader.com)|🚫|GPL||
|pdf|[poppler](https://poppler.freedesktop.org)|🚫|GPL||
|pdf|[MuPDF](https://github.com/ArtifexSoftware/mupdf)|🚫|AGPL||
|pdf|[PoDoFo](https://github.com/podofo/podofo)|⚠️|[LGPL-2](https://github.com/podofo/podofo/blob/master/COPYING)||
|docx|[OPC](https://github.com/freuter/libopc)|✅|[BSD](https://github.com/freuter/libopc/blob/master/LICENSE)|[opc-parser](https://github.com/miyako/opc-parser)|
|xls|[libxls](https://github.com/libxls/libxls)|✅|[BSD](https://github.com/libxls/libxls/blob/dev/LICENSE)||
|xls|[FreeXL](https://www.gaia-gis.it/fossil/freexl/index)|⚠️|[LGPL-2](http://www.gnu.org/licenses/lgpl-2.1.html)||
|xlsx|[OPC](https://github.com/freuter/libopc)|✅|[BSD](https://github.com/freuter/libopc/blob/master/LICENSE)|[opc-parser](https://github.com/miyako/opc-parser)|
|pptx|[OPC](https://github.com/freuter/libopc)|✅|[BSD](https://github.com/freuter/libopc/blob/master/LICENSE)|[opc-parser](https://github.com/miyako/opc-parser)|
|eml|[GMime](https://github.com/jstedfast/gmime)|⚠️|LGPL-2.1||
|eml|[mimetic](https://github.com/tat/mimetic)|✅|[MIT](https://github.com/tat/mimetic/blob/master/COPYING)||
|eml|[libcmime](https://www.libcmime.org)|✅|MIT||
|ost|[libpff](https://github.com/libyal/libpff)|⚠️|[LGPL-3.0](https://github.com/libyal/libpff/blob/main/COPYING)|[pff-parser](https://github.com/miyako/pff-parser)|
|pst|[libpff](https://github.com/libyal/libpff)|⚠️|[LGPL-3.0](https://github.com/libyal/libpff/blob/main/COPYING)|[pff-parser](https://github.com/miyako/pff-parser)|
|pab|[libpff](https://github.com/libyal/libpff)|⚠️|[LGPL-3.0](https://github.com/libyal/libpff/blob/main/COPYING)|[pff-parser](https://github.com/miyako/pff-parser)|
|msg|[libgsf](https://github.com/GNOME/libgsf)|⚠️|LGPL-2.1||
|msg|[libolecf](https://github.com/libyal/libolecf)|⚠️|[LGPL-3.0](https://github.com/libyal/libolecf/blob/main/COPYING)|[olecf-parser](https://github.com/miyako/olecf-parser)|
|html|[tidy-html5](https://github.com/htacg/tidy-html5)|✅|[W3C](https://github.com/htacg/tidy-html5/blob/next/README/LICENSE.md)|[tidy-parser](https://github.com/miyako/tidy-parser)|
|html|[lexbor](https://github.com/lexbor/lexbor)|✅|[Apache 2.0](https://github.com/lexbor/lexbor/blob/master/LICENSE)|[lexbor-parser](https://github.com/miyako/lexbor-parser)|
|doc|[antiword](https://web.archive.org/web/20221207132720/http://www.winfield.demon.nl/)|🚫|GPL||
|doc|~~[librevenge](https://sourceforge.net/p/libwpd/librevenge/ci/master/tree/)~~[^librevenge]|✅|Apache-2.0|
|doc|[catdoc](http://wagner.pp.ru/~vitus/software/catdoc/)|🚫|GPL||
|doc|[wvWare](https://wvware.sourceforge.net)|🚫|GPL||
|rtf|[UnRTF](https://www.gnu.org/software/unrtf/)|🚫|GPL||
|rtf|~~[librtf](https://librtf.sourceforge.net/)~~[^librtf]|⚠️|LGPL-2.1|[rtf-parser](https://github.com/miyako/rtf-parser)
|rtf|platform api|✅️||[rtf-parser](https://github.com/miyako/rtf-parser)
|rtf|[rtfreader](https://github.com/kuhumcst/rtfreader)|🚫|GPL||
|ppt|[libolecf](https://github.com/libyal/libolecf)|⚠️|[LGPL-3.0](https://github.com/libyal/libolecf/blob/main/COPYING)|[olecf-parser](https://github.com/miyako/olecf-parser)|

## compatibility

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

* ~~https://crates.io/crates/langextract-rust~~ [^lx-rs]
* https://crates.io/crates/text-splitter

## final step

once we have a set of parsers and a tool to chunk extracted plain text, we can develop a tool that extracts, chunks, and vectorises text using [4D AIKit](https://github.com/4d/4D-AIKit). the idea is to use the offical component, not develop a custom fork.

[^librevenge]: `librevenge` is a CFBF parser library. reportedly the `libmwaw` filter supports MacWrite, AppleWorks, etc. the`libwps` filter supports Microsoft Works. there are no known filters for Microsoft Word (`.doc`) documents.
[^librtf]: even with UTF-8 and surrogate pair patches, `librtf` is fundamentatlly flawed and not reliable for processing `.rtf` especially Microsoft Outlook messages. the parser implementation now uses platform APIs (`NSAttributedString` and `Riched20.dll`).
[^lx-rs]: this CLI utility internally uses `semchunk-rs` to chunk text before extrating meaningful information thanks to AI. it is not designed for chunking only.
