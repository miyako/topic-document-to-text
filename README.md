# topic-document-to-text

goal is to develop text extractor tools for common file formats that is compatible with MIT, BSD or Apache 2.0.

|format|solution|compatibility|licensing|parser|
|:-:|-|:-:|-|-|
|pdf|[PDFium](https://github.com/PDFium/PDFium)|✅|BSD|[pdfium-parser](https://github.com/miyako/pdfium-parser)
|pdf|[Xpdf](https://www.xpdfreader.com)|🚫|GPL||
|pdf|[poppler](https://poppler.freedesktop.org)|🚫|GPL||
|pdf|[MuPDF](https://github.com/ArtifexSoftware/mupdf)|🚫|AGPL||
|pdf|[PoDoFo](https://github.com/podofo/podofo)|⚠️|LGPL||
|docx|[OPC](https://github.com/freuter/libopc)|✅|BSD|[opc-parser](https://github.com/miyako/opc-parser)|
|eml|[GMime](https://github.com/jstedfast/gmime)|⚠️|LGPL||
|eml|[mimetic](https://github.com/tat/mimetic)|✅|MIT||
|eml|[libcmime](https://www.libcmime.org)|✅|MIT||
