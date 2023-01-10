# Template for python projects based on devcontainer

## Dependencies

* [Visual Studio Code](https://code.visualstudio.com/download) (with the "Remote containers" extension installed)
* [Docker](https://docs.docker.com/engine/install/)
* (Optional) [Devcontainer CLI](https://code.visualstudio.com/docs/remote/devcontainer-cli) (allows to directly launch devcontainer from commandline, instead of opening VSCode and then clicking on "Reopen in container")

## How to use

1. Clone this repo (or use it as a template for a new one)
2. Open VSCode
3. Either click on "Reopen in container" when the extension detects the devcontainer, or search for it in the command palette (can be opened with `CTRL + SHIFT + P`)

## How to setup access for DVC remote storage (S3)

* generate an AWS credentials file by copying the example one (`cp .aws/credentials.example .aws/credentials`)
* fill the credentials file with your personal information (AWS access key and secret key)
* initialize DVC in the repo with `dvc init`
* configure the DVC default remote storage on AWS S3 with `dvc remote add s3-bucket s3://{BUCKET_NAME} && dvc remote default s3-bucket` (note that you need to change `{BUCKET_NAME}` with the actual name of the S3 bucket you want to use)

## Jupytext guide
Jupytext extension allow to translate common text files (e.g. python or markdown) in jupyter notebooks and viceversa. Jupytext is integrated via this [Jupytext VSCode extension](https://github.com/congyiwu/vscode-jupytext). Below a simple guide on how to use it:

* create a `.py` file 
* insert some code
* when you want to run it as a notebook: 
    - move to file explorer section (top left icon in vs code) 
    - right-clik on the file you want to open
    - click "Open as a Jupyter Notebook"
* modifying the notebook <span style="color: #77dd77">will change</span> also the original file
* modifying the original file <span style="color: #ff6961">will not change</span> the notebook already opened (re-launch to see changes on notebook)

Additional notes:
* jupytext syntax:
    - when the file is opened as a notebook the first time will be formatted automatically
    - to divide cells just add this comment 
    ```
    # %%
    ... code here ...
    ```
* it works with different extensions (`.py`, `.md` etc.)
* <span style="color: #ff6961">NB</span>: By default the jupytext notebook file opened in this way [does not exist on disk](https://github.com/congyiwu/vscode-jupytext), thus modifying the file once the notebook is opened will not affect the file.
* metadata that can be visible on the original file after opening it as a notebook are not considered by this extension (this enhacement is in the [roadmap](https://github.com/congyiwu/vscode-jupytext#roadmap))