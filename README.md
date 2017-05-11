# Open XML Chunking
This Java library supports fragmenting and reassembling [Office Open XML \(OOXML)](https://en.wikipedia.org/wiki/Office_Open_XML_file_formats) 
formatted documents including Microsoft Office such as PowerPoint (pptx) or Word (docx) and Apache Open Office such as Presentations (odp) and Text (odt). Fragmenting documents into chunks is currently only supported on the desktop/server JDK. Reassembling document chunks is supported on both the desktop/server JDK and Android SDK. 

## About Chunking
### Fragmenting Documents into Chunks
Fragmenting a document produces multiple smaller copies of the document by reducing the resolution of the media embedded within the document. Each smaller copy of the document is called a **_chunk_**. Each chunk is complete in that it contains all of the text, formatting, and media from the original. The only difference between a chunk and its original document is that a portion of the data from each embedded image is removed - resulting in a lower resolution, yet still complete, copy of the image. 

### Reassembling Documents from Chunks
The fragmenting process is done in such a way that any two of the resulting fragments can be reassembled to produce a copy of the original with twice the resolution for each image. In this way, all of the chunks can be reassembled to restore the full quality of the original document.

## Using this Library
### Interfaces
The 'us.ihmc.chunking' package contains the 'Fragmenter' and 'Reassembler' interfaces that are meant to be applicable to any document type.

### JDK
The 'us.ihmc.chunking.server' package includes the 'OoxmlFragmenter' and 'OoxmlReassembler' implemetation of the 'Fragmenter' and 'Reassembler' interfaces specific to Office Open XML documents. This implementation depends upon the 'javax.imageio' and 'java.awt.image' packages that are _only_ currently available on the JDK and _not_ the Android platform.

### Android SDK
The 'us.ihmc.chunking.android' package includes the 'OoxmlReassembler' implemetation specific to Office Open XML documents. This implementation depends upon the 'android.graphics' package is _only_ available on the Android platform and _not_ the JDK.
