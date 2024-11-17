# Inference Pipeline

- For inferencing we load the pre-fintuned models from `../Models` folder.
  
- All available model for each category is loaded and the output of each model in blended toghter to generate the final output in the `output` folder.

# How to run

- Downlaod all the pre-finetuned models from the following google drive link : [Download Models here](https://drive.google.com/drive/folders/1SrynpY35WIkubQekjgfLw4ZuDYf--UYI?usp=sharing)
  
- alternativelly use `gdown` as follow : 
  
- ```Bash
    cd Inferencing && \
    pip install gdown && \
    gdown --folder https://drive.google.com/drive/folders/1SrynpY35WIkubQekjgfLw4ZuDYf--UYI?usp=sharing -O ../Models
    ```

- Run the individual `.ipynb` notebooks for each category to generate the output in the `output` folder.

- One liner to run all the `.ipynb` notebooks from command line :

- ```Bash
    (trap "pkill -P $$" SIGINT; find . -type f -name "*.ipynb" | while read notebook; do jupyter nbconvert --to notebook --execute "$notebook" --output "${notebook%.ipynb}_executed.ipynb" & done; wait)
  ```

  