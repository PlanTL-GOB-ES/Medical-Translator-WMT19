# Neural Machine Translation for the Biomedical Domain - WMT19   


## Introduction

This package contains the files needed to use the Neural Machine Translation (NMT) system
for the Biomedical Domain.

The available language directions for translation are:
* English to Spanish
* Spanish to English
* English to Portuguese
* Portuguese to English
* Spanish to Portuguese
* Portuguese to Spanish

Translation models must be downloaded from the Zenodo repository: https://doi.org/10.5281/zenodo.3346802


## Prerequisites

This package uses the Torch implementation of the OpenNMT-py system (http://opennmt.net/OpenNMT-py/). Instructions to install the 
system are found in: http://opennmt.net/OpenNMT-py/main.html#installation  
This package also uses the SentencePiece package for python.  
To download it, use pip install sentencepiece


## Directory structure

<pre>
Tokenize_SP.sh 	 - Utility script to tokenize the input file using BPE (needed for translation)
</pre> 
In Zenodo you will find the following files:
<pre>
enes_pt.bpe32000 	 - SP encoding where source language are either EN/ES and target is PT
enpt_es.bpe32000 	 - SP encoding where source language are either EN/PT and target is ES
espt_en.bpe32000 	 - SP encoding where source language are either ES/PT and target is EN
enes_pt_model.pt  - OpenNMT-py model in original format (EN/ES) -> PT
pten_es_model.pt  - OpenNMT-py model in original format (EN/PT) -> ES
espt_en_model.pt  - OpenNMT-py model in original format (ES/PT) -> EN
</pre> 


## Usage

Tokenize.sh [options] 

Options:
<pre>
-d : Data directory where the BPE models and translation models are stored
-s : Language of the source file. Valid options are: en, es, or pt
-t : Language of the target file. Valid options are: en, es, or pt
-f : Path to the file that will be translated
</pre>


## Examples

<pre>
$ .Tokenize_SP.sh -d /home/user/data -s en -t es -f /home/user/text.txt
$ cd /home/user/OpenNMT-py
$ python3 translate.py -model /home/user/data/espt_en_model.pt -gpu 0 -src /home/user/text.txt.tok -replace_unk -output /home/user/text.translated
$ spm_decode --model=/home/user/data/espt_enSP32k.model < /home/user/text.translated> /home/user/text.translated.detokenized;
</pre>


## Contact

Felipe Soares (felipe.soares@bsc.es)


## License

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

Copyright (c) 2018 Secretaría de Estado para el Avance Digital (SEAD)
