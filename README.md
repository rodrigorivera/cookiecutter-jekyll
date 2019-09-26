# Docker Cookiecutter Jekyll

## Getting Started
1. Install Docker: 
    - For Mac: https://store.docker.com/editions/community/docker-ce-desktop-mac
    - For Windows: https://store.docker.com/editions/community/docker-ce-desktop-windows
    - For Linux: Go to this page and choose the appropriate install for your Linux distro: https://www.docker.com/community-edition
        - Install Docker Compose (https://docs.docker.com/compose/install/#install-compose):
            ```bash
            $ sudo curl -L https://github.com/docker/compose/releases/download/1.21.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
            ```
            ```bash
            $ sudo chmod +x /usr/local/bin/docker-compose
            ```
            Test the installation:
            ```bash
            $ docker-compose --version
            docker-compose version 1.21.0, build 1719ceb
            ```
2. Install Python Cookiecutter package: http://cookiecutter.readthedocs.org/en/latest/installation.html >= 1.4.0
    ``` bash
    $ pip install cookiecutter
    ```
    It is recommended to set up a central virtualenv or condaenv for cookiecutter and any other "system" wide Python packages you may need.
3. Run the cookiecutter docker data science template to scaffold your new project:
    ``` bash
    $ cookiecutter https://github.com/rodrigorivera/cookiecutter-jekyll.git
    ```
4. Answer all of the cookiecutter prompts for project name, description, license, etc.
5. Run the start script from the level of your new project directory:
    ``` bash
    $ ./start.sh
    ```
6. After the project image builds check which host port is being forwarded to the Jupyter notebook server inside the running container:
    ``` bash
    $ docker ps 
    ```
7. Using any browser access your notebook at localhost:{port}
8. Start working!

For more details on what packages are available pre-installed in the base image see the manifoldai/docker-ml-dev repository page on [Docker Hub](https://hub.docker.com/r/manifoldai/docker-ml-dev/).
### Project Structure
The directory structure of your new project looks like this: 

```
├── LICENSE
├── Dockerfile            <- New project Dockerfile that sources from base ML dev image
├── docker-compose.yml    <- Docker Compose configuration file
├── docker_clean_all.sh   <- Helper script to remove all containers and images from your system
├── start.sh              <- Script to run docker compose and any other project specific initialization steps 
├── Makefile              <- Makefile with commands like `make data` or `make train`
├── README.md             <- The top-level README for developers using this project.
├── data
│   ├── external          <- Data from third party sources.
│   ├── interim           <- Intermediate data that has been transformed.
│   ├── processed         <- The final, canonical data sets for modeling.
│   └── raw               <- The original, immutable data dump.
│
├── docs                  <- A default Sphinx project; see sphinx-doc.org for details
│
├── models                <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks             <- Jupyter notebooks. Naming convention is a number (for ordering),
│                            the creator's initials, and a short `-` delimited description, e.g.
│                            `1.0-jqp-initial-data-exploration`.
│
├── references            <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports               <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures           <- Generated graphics and figures to be used in reporting
│
├── requirements.txt      <- The requirements file for reproducing the analysis environment, e.g.
│                            generated with `pip freeze > requirements.txt`
│
├── src                   <- Source code for use in this project.
│   ├── __init__.py       <- Makes src a Python module
│   │
│   ├── data              <- Scripts to download or generate data
│   │   └── make_dataset.py
│   │
│   ├── features          <- Scripts to turn raw data into features for modeling
│   │   └── build_features.py
│   │
│   ├── models            <- Scripts to train models and then use trained models to make
│   │   │                    predictions
│   │   ├── predict_model.py
│   │   └── train_model.py
│   │
│   └── visualization  <- Scripts to create exploratory and results oriented visualizations
│       └── visualize.py
│
└── tox.ini            <- tox file with settings for running tox; see tox.testrun.org
```

## Video Demo
[![Torus Demo Youtube](http://img.youtube.com/vi/RgRmT4W8nTY/0.jpg)](http://www.youtube.com/watch?v=RgRmT4W8nTY)

## Helpful Resources 
- Docker command cheatsheet: https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf
- Dockerfile reference: https://docs.docker.com/engine/reference/builder/
- Docker Compose reference: https://docs.docker.com/compose/compose-file/
- Kitematic (GUI interface to work with Docker. Highly recommended if you are new to Docker!): https://kitematic.com/
