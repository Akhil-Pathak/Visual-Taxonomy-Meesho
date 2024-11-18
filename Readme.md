# Team: **Topple my Tiger**
# CODS-COMAD Data Challenge (Sponsored by Meesho) 

## Approach Brief

## How to run the code

- The code is divided into three main pipelines `Preprocessor`, `Training`, and `Inferencing`.

- Each pipeline is run for each category of the products, and creates the artefacts in their respective `output` folders.

### Setup

- Create aand activate a virtual environment as follow:
```Bash
    python3 -m venv cods-venv && source cods-venv/bin/activate
```
- Install all the dependencies
```Bash
    pip install -r ./requirements.txt
```
- downlaod all the pre-finetuned models from the following google drive link : [Download Models here](https://drive.google.com/drive/folders/1SrynpY35WIkubQekjgfLw4ZuDYf--UYI?usp=sharing) and extract the archive into the `./Models` folder.

- alternativelly use `gdown` as follow:
  
```Bash
    pip install gdown && \
    gdown --folder https://drive.google.com/drive/folders/1SrynpY35WIkubQekjgfLw4ZuDYf--UYI?usp=sharing -O ./Models
```
- Download dataset from [Kaggle](https://www.kaggle.com/competitions/visual-taxonomy/data?select=test_images) and unzip the dataset into the `./Dataset` folder. 
- Alternatively use Kaggle CLI as follow: 
```Bash
    kaggle competitions download -c visual-taxonomy -p ./Dataset
```
### Running the preprocessor

- To run the preprocessor, run the individual `.ipynb` notebooks for each category.

- alternatively use the following one-liner from bash shell to run all the preprocessor notebooks at once (Please ensure adequate RAM and CPU power are present in machine to handle all the notebooks at once).

```Bash
    cd Preprocessor-FillNA && \
    (trap "pkill -P $$" SIGINT; for notebook in *.ipynb; do jupyter nbconvert --to notebook --execute "$notebook" --output "${notebook%.ipynb}_executed.ipynb" & done; wait)
```

### Running training of models 

- Ensure you have ran the preprocessor code and the outputs are generated in `./Preprocessor-FillNA/output`.

- Run individual `.ipynb` notebooks for each category.

- The code will save the models in the `./Models/<category>` folder for each category.

### Running inference

- To run inference, please ensure all the models are downloaded from google drive and placed in the correct folder.

- Run the individual `.ipynb` notebooks for each category to generate the output in the `output` folder and respective category folders too.

- One liner to run all the `.ipynb` notebooks from command line :

```Bash
    cd Inferencing && \
    (trap "pkill -P $$" SIGINT; find . -type f -name "*.ipynb" | while read notebook; do jupyter nbconvert --to notebook --execute "$notebook" --output "${notebook%.ipynb}_executed.ipynb" & done; wait)
```

### Building the submission file

- To create the final submission file, run `Submission_File_Prep.ipynb` this will create the `submission.csv` file in the root folder.

- To run the same from command line please use the following:
  
```Bash
     jupyter nbconvert --to notebook --execute ./Submission_File_Prep.ipynb --output Submission_File_Prep_executed.ipynb
```