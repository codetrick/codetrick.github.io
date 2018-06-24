---
layout: post
title:  "Online Resources of Chinese Pre-Modern Texts"
date:   2018-06-23 18:44:52 -0700
published: true
categories: chinese
---

It goes without saying that any Chinese pre-modern texts ever existed did not have a digital version to start with. They were either handwritten, printed with woodblocks, or inscribed on a variety of objects (鐘鼎文, 石鼓文, 甲骨文, etc.). However, for the convenience of both research and education, there are significant governmental and academic efforts to convert those texts into a format that is more accessible. Building and keeping an electronic archive of Chinese Texts serves many purposes:
1. Easier search, annotation, and cross-reference.
2. [Natural language processing (NLP)][nlp] of [Classical Chinese][classical_chinese] texts. The accuracy of models used in NLP (if taken a statistical approach) will directly benefit from a large corpus of well-structured texts.
3. Batch processing and digital publication of Chinese texts in different platforms with minimal effort.
4. Certain types of books, for example dictionaries (字書, 韻書), could be processed with metadata attached to each entry, which would facilitate complex queries. This would allow for character lookup across many dictionaries with one click (or shall I say one SQL query?), possibly even with example usage pulled directly from the full corpus.
5. Related with the previous point, easier query of dictionaries enables students to study Chinese etymology, phonology and dialectology, as well as researchers to compare phonology of dialects and conduct field studies.

This list can go on for much longer, but I'll stop here for brevity.

<!--more-->

Obviously the task of digitization is no small feat. As I mentioned, there are governmental and academic efforts that took innumerable graduate students, typists and copy-editors hours upon hours of work to compile the corpora that are available today. Because of the high cost of production, often the work is outsourced to companies, which then would brand the corpora / database and put behind a paywall.

There are many problems associated with paywalls. Amateur researchers may not be able to afford the subscription fee and get discouraged. For researchers working at a University that subscribes to the services, the query interface might not be transparent and easy to use. Batch download and processing of texts may also be restricted. These companies aren't at fault - the data came from their investment on time and effort, and it is their right to safeguard them to certain extent. Still, government and academic institutions should have done better, especially those of Mainland China, should have done better to make more Classical Chinese corpora freely available to the general public.

Luckily, all pre-modern Chinese texts are in the public domain now. Many digital texts that were first digitalized by companies are now circulating in online Sinology communities. There are also laudable efforts by certain individuals and academic entities to make texts available in an easily accessible format. The following is an incomplete list of sites that I find quite useful.

### Full texts 文集
[Chinese Text Project](https://www.ctext.org/)
: This site is very well-known among Sinology students and researchers. It has a large corpus of more than 30k books. For many titles both scanned pictures and digital texts are available. A dictionary with example usage from the textual database that is closely-knit with the text viewer pages. A wiki section that allows for crowd-sourcing OCR correction. And an API!

[漢籍リポジトリ Kanseki Repository](http://www.kanripo.org)
: I recently stumbled upon this site. It is by no means close to CTP in scale, but the nice thing about it is that its data are freely available [on GitHub](https://github.com/kanripo), and so is the [code for textual manipulation](https://github.com/mandoku/mandoku)!

[書格](https://shuge.org)
: 書格 Shuge is a growing collection of scanned pre-modern Chinese books in PDF format. It does not provide digital text for the books.

### Dictionaries 字書 韻書

[漢典](http://www.zdic.net/)
: 漢典 is a well-known Chinese dictionary site that provides character definitions in modern Chinese, as well as in classical Chinese from 康熙字典 and 說文解字, along with phonetic information from 廣韻, pronounciation in certain dialects, and more.

[說文解字](http://www.shuowen.org)
: As the name suggests, this is a nice query interface for the authoritative dictionary 說文解字 on the etymology of Chinese characters.

[韻典網](http://ytenx.org)
: Comprehensive Chinese phonology lookup tool. Data from 廣韻, 中原音韻, 洪武正韻牋, 分韻撮要 and 上古音系 are available.

[古今文字集成](http://www.ccamc.co/)
: Comprehensive Chinese dictionary with data from 漢語大字典, 說文解字, 康熙字典, and more. It also incorporates phonology data from the same sources as 韻典網. There's also an etymology section showing variations of the same character. A dialect section that is vastly bigger in scope than that of 漢典, and interestingly, dictionaries of the Tangut script (西夏文), Jurchen script (女真文), Khitan script (契丹文) and the 'Phags-pa script (八思巴文) are also available.

[搜韻](https://sou-yun.com/)
: A Chinese phonology dictionary lookup tool designed for 詩 *Shi* and 詞 *Ci* writing, with a large *Shi* and *Ci* corpus.

[漢字古今音資料庫](http://xiaoxue.iis.sinica.edu.tw/ccr/)
: Database for historic and dialectal Chinese phonology. Developed by National Taiwan University and Funded by The Ministry of Science and Technology of the Republic of China.

I will keep updating this page for web resources I find useful in the future.

[classical_chinese]: https://en.wikipedia.org/wiki/Classical_Chinese
[nlp]: https://en.wikipedia.org/wiki/Natural_language_processing
