# Preprocessor pipeline for filling NAN values

- We Finetuned EfficientNet b5 models for each attribute of each catergory.
- These models were fine tuned based on the available data with NAN values dropped from the dataset of particular catergory and attribute.

# Training and Filling process

- The code is divided into 5 diffrent file, with a new file for each category. 
- The code on running will do the following 
```Bash
    Partition Data on NAN -> Train EffNetB5 foreach Attr -> Fill NAN values based on trained EffNetB5 -> Output filled Dataset into output folder
```