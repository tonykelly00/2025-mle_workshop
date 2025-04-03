# MLE Course 20205-04

Here we learn how to do Machine leanring Engineering Stuff.

what is a dev enviorment and why is git code space better in this regard than google colab

Based on repository by Alexey:
https://github.com/alexeygrigorev/ml-engineering-contsructor-workshop#


DicVectorizer - dictionary to vector and can be useful for jsons


ON the cospace we have a lot of preinstalled packages

PS1="> " to shorten terminal address 

use python package manage 
## install UV - a python package in Rust
from https://docs.astral.sh/uv/getting-started/installation/
curl -LsSf https://astral.sh/uv/install.sh | sh


## Day 1
- create folder day_1 
-cd day_1/ into directory

-initalise python project in 
    -run 'uv init --python 3.10'

### install dependencies
   run uv add scikit-learn==1.2.2 pandas pyarrow
   run dev dependencies only needed during developmen
   uv add --dev jupyter seaborn