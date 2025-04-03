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
UV is a python package and enviorment manager in Rust
we then create a local virtual enviorment that satisfies the dependencies and code runs in this local virtual enviroment rather than the global enviorment on codespace

from https://docs.astral.sh/uv/getting-started/installation/
curl -LsSf https://astral.sh/uv/install.sh | sh


## Day 1
- create folder day_1 
- cd day_1/ into directory


-initalise python project in day 1 that will be the virtual env we use.
    -run 'uv init --python 3.10'

creates:    project.toml file - contains dependencies and updated
            uv.lock
            .venv - the virtual enviorment

### install dependencies
   run 'uv add scikit-learn==1.2.2 pandas pyarrow'
   run --dev dependencies only needed during developmen
   'uv add --dev jupyter seaborn'
   run uv add numpy==1.26.4 #to fix the issues with sklearn  
    as default the uv init python installs numpy2.??? which is not compatible

    need to select this enviorment in python bottom left corner of VS code when a .py file selected and enter the interpreter path (copy and paste the location to .venv directory created by  UV)

    How to select the .venv to run the .ipynb notebook?
    This is tricky and not sure how to get it to work


make sure everthing is installed and set
pip install notebook ipykernel
python -m ipykernel install --user --name=.venv

Verify that your workspace settings in the Codespace allow for multiple kernels to be detected. Open your workspace settings () and ensure there are no restrictions. Specifically, check for
        "python.defaultInterpreterPath": "/workspaces/2025-mle_workshop/day_1/.venv/bin/python



### lets convert the notebook to a script
- uv run jupyter nbconvert --to=script notebooks/duration-prediction.ipynb

### lets make the script nicer
see the git commits for the intermediate steps:

- remove top level statements
- make function parameterized
- introduce argparse
    - make it run via 'uv run python duration_prediction/train.py --train-date 2022-01 --val-date 2022-02 --model-save-path models/2022-01.bin'
with argparse you now input the variables from command line. 

- add docstrings: eg use autodocstring extension in vscode or chatgpt
    this is """   """" with a structured description at beginign of function that is shown when you hover over a call of the function

- add logging
    this tracks events that happen during execution to give information about what is happening


### makefile
create a file called Makefile and insert content. now we can run training via  
 'make train'

### add tests
- run 'uv add pytest'
    this is need to install pytest, pip install not the same

- create a tests folder. this is the folder where pytest looks for the files (named test_*.py or *_test.py, functions starting with test_) to automatically test the code

- in the test folder create a file test_train.py

- in the folders duration_prediction and tests create empty files named __init__.py
    THE presence of an empty ___init__ file indicates to Python that the directory should be treated as a package. This enables you to import modules and submodules within the folder structure.
    In the case of the Test folder, having an __init__ ensures that your test files can be recognized as part of the package when running test frameworks like pytest.

- run 'uv run pytest'
    now that test folder has an __init__ file the pytest discovers test files in the folder and runs them. In the test_train.py file it calls train function from duratio_prediction folder and having a __init__ means it was added as a package and is available.

- you can also run the tests via 'make tests' thanks to the Makefile