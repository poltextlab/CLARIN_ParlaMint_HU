# ParlaMint_CLARIN
3.12.	Hungarian Parliament
Characteristics of the national parliament
The Hungarian parliamentary corpus contains the Minutes of the National Assembly of Hungary, Term 7 and 8 (2014.06.10-2020.12.14). It consists of 3086 speeches and 1114495 words. The source of the data is downloaded from the official page of the Hungarian National Assembly (https://www.parlament.hu/), where each day is converted into one XML file with TEI encoding. The unicameral assembly’s data includes regular, special (extraordinary, urgent, ceremonial, commemorative) and continued meetings, in which there are interpellations, urgent questions and regular speeches.

Data source and acquisition
The source for ParlaMint-HU was obtained from the official website of the Hungarian National Assembly (https://www.parlament.hu/). There was no manual correction applied, however normalisation was performed on the meta-data only (e.g. person names). In the source there was no end-of-line hyphens, but quotation marks were present, they have been left in the text and are not explicitly marked up. The texts are segmented into utterances (speeches) and segments (corresponding to paragraphs in the source transcription). The data for each day are available in separated XML files.

Data encoding process
As a first step, the data originally scraped from the Parliament’s official website was cleaned from the HTML tags present in the generated files. As a result, the plain versions of the texts are generated as .txt files. Metadata, including speaker’s name, birth date, political party and so on was stored in separate xlsx. files. 
Next, with the use of Python scripts mostly based on regex solutions, different kinds of annotator comments have been identified as <kinesic> tags. In the same processing step, the <seg> tags and the individually identifiable <u…> tags placed to the future xml file. At last but not least, the basic structure of the TEI xml schema was generated, and then the two part putted together, while inserted also the basic statistics of the given xml’s tag usage, the mentioned speakers etc.
The files were validated using the scripts provided by Tomaz Erjavec to us (https://github.com/clarin-eric/ParlaMint/tree/main/Scripts). 
To create the annotated files, we had to use three different linguistic tools to get the final result, since none of the available NLP tools for Hungarian is capable of providing the needed analysis at once: 
•	For get the syntactic analysis (eg. the dependency relations) we have used UDPipe (available at: https://lindat.mff.cuni.cz/services/udpipe/). 
•	For the appropriate MSD codes at the morphological level, we used an older version of the magyarlanc linguistic toolkit (newest version available at: https://rgai.inf.u-szeged.hu/magyarlanc).
•	For present the Named Entity Recognition, the Named Entity Recogniser tool was used, which originally created by the MTA-SZTE Research Group on Artificial Intelligence in an earlier project (https://rgai.inf.u-szeged.hu/node/109).
As the above mentioned analytical steps finished, the output of the three parsers have merged with a JAVA program, where the baseline of the merging procedure was the UDPipe analysis’ tokenized version of the .txt files. 
Based on this analysed version, the needed XML tags have been added as a final step, including the expected metadata and statistics with a JavaScript method. 
Corpus-specific metadata
Apart from the common structure, original ECPC XML files contain:
As part of speaker metadata:
1)	the specific role of ministers addressing the Chamber; 
2)	the political groups (and not just parties) of the Országgyűlés (National Parliament), for each legislature
3)	constituencies of all MPs

Linguistic annotation
Hungarian is an agglutinative language, thus a word can have hundreds of word forms due to inflectional or derivational affixation. Grammatical information is usually encoded in morphology and Hungarian is a typical morphologically rich language. Hungarian nouns can have about 20 cases1 and – being a headfinal language – case suffixes always occur at the right end of the word.
Case suffixes mark the relationship between the head and its arguments (subject, object, dative etc.). Verbs are inflected for person and number and the definiteness of the object. Conjugational information is sufficient to deduce the pronominal subject or object, hence they are mostly omitted from the sentence.
There are several other linguistic phenomena that are syntactic in nature in English but they are encoded morphologically in Hungarian. For instance, causation and modality are expressed by derivative suffixes and so is passive (although the passive voice is rare in modern Hungarian).
