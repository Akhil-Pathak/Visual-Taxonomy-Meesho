# Preprocessor pipeline for filling NAN values

- We Finetuned EfficientNet b5 models for each attribute of each catergory.
- These models were fine tuned based on the available data with NAN values dropped from the dataset of particular catergory and attribute.

# Training and Filling process

- The code is divided into 5 diffrent file, with a new file for each category. 
- The code on running will do the following 
```Bash
    Partition Data on NAN -> Train EffNetB5 for each Attr. -> Fill NAN values based on trained EffNetB5 -> Output filled Dataset into output folder
```
# How to run

- Follow instructions in main `../Readme.md` file to create the environment and install dependencies. 
- Run individual `ipynb` notebooks to get the output in `./output` folder.
- Command to run all the `.ipynb` files from the command line: 
- 
  ```Bash
  (trap "pkill -P $$" SIGINT; for notebook in *.ipynb; do jupyter nbconvert --to notebook --execute "$notebook" --output "${notebook%.ipynb}_executed.ipynb" & done; wait)
  ```  