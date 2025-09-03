# topic-document-to-text

goal is to develop text extractor tools for common file formats that is compatible with MIT, BSD or Apache 2.0.

|format|solution|compatibility|licensing|parser|
|:-:|-|:-:|-|-|
|pdf|[PDFium](https://github.com/PDFium/PDFium)|✅|BSD|[pdfium-parser](https://github.com/miyako/pdfium-parser)
|pdf|[Xpdf](https://www.xpdfreader.com)|🚫|GPL||
|pdf|[poppler](https://poppler.freedesktop.org)|🚫|GPL||
|pdf|[MuPDF](https://github.com/ArtifexSoftware/mupdf)|🚫|AGPL||
|pdf|[PoDoFo](https://github.com/podofo/podofo)|⚠️|LGPL-2||
|docx|[OPC](https://github.com/freuter/libopc)|✅|BSD|[opc-parser](https://github.com/miyako/opc-parser)|
|eml|[GMime](https://github.com/jstedfast/gmime)|⚠️|LGPL-2.1||
|eml|[mimetic](https://github.com/tat/mimetic)|✅|MIT||
|eml|[libcmime](https://www.libcmime.org)|✅|MIT||
|msg|[libpff](https://github.com/libyal/libpff)|⚠️|LGPL-3.0||

## remarks

⚠️ conditionally compatible

LGPL 2.1 says

> Provide the object code or source code needed to relink the application with a modified version of the Library, so users can replace the Library in a statically linked or dynamically linked work.”

each repository shall provide the object code (`.a` for macOS and `.lib` for Windows) and build tools (Xcode project for macOS and Visual Studio solution for Windows) for compatibility.

✅ fully compatible

BSD or MIT is permissive. 

🚫 not compatible

GPL is copyleft; the library licensing propagates to the whole program.

## next step

once we have a reasonable set of parsers, we could consider using rust-based tools for chunking.

* https://crates.io/crates/langextract-rust
* https://crates.io/crates/text-splitter
