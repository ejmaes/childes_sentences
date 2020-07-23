Repository for parsing childes transcriptions, preparing data for speech act prediction.

# Requirements
* xmltodict

# Generating data for classification
Data is downloaded from [Childes](https://childes.talkbank.org/access/) then converted to XML:
```
$ java -cp chatter.jar org.talkbank.chatter.App -inputFormat cha -outputFormat xml -tree -outputDir [outdirname] [inputdir]
```

**Extraction pipelines:**
* *raw XML to raw JSON* - either in the same or a separate folder
* *raw (XML/JSON) to individual files (JSON)* with extracted data
* *extracted data to individual DSV* with selected features
* *extracted data to aggregated train/test/valid DSV* with selected features

**Extracted features:**
* Uttered sentence (main words, no fillers, without correction)
* Lemmas and POS tags
* Speech act if exists

**Organisation:**
```
/data
    /NewEngland
    /Bates
    ... transcripts in xml format
/formatted
    /NewEngland
    /Bates
    ... json/xml individual files with extracted features
/ttv
    newEngland_train.tsv
    ... train/test/valid files
xml_to_json.py: raw XML to raw JSON (1)
format_data.py: raw to formatted JSON (2)
extract_data.py: formatted JSON to desired columnar format (3)
utils.py: useful functions for extraction from raw data
```

# Sources
* Childes - Download and transform to xml: https://talkbank.org/share/data.html 
* Speech Acts: https://talkbank.org/manuals/CHAT.pdf