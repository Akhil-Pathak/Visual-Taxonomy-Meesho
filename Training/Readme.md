# Model training

- For each category multiple models are trained and during inference the outputs from each model are blended togther. 

# How to run

- Ensure you have ran the preprocessor code and the outputs are generated in `../Preprocessor-FillNA/output`.
- Run individual `.ipynb` notebooks for each category.
- The code will save the models in the `../Models/<category>` folder for each category.
- Pre-Finetuned models can be downloaded from GDrive link: [Download Models here](https://drive.google.com/drive/folders/1SrynpY35WIkubQekjgfLw4ZuDYf--UYI?usp=sharing)
- alternativelly use `gdown` as follow : 
  
- ```Bash
    cd Inferencing && \
    pip install gdown && \
    gdown --folder https://drive.google.com/drive/folders/1SrynpY35WIkubQekjgfLw4ZuDYf--UYI?usp=sharing -O ../Models
    ``` 