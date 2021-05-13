[![CircleCI](https://circleci.com/gh/mdominovic/DevOps_Microservices.svg?style=svg)](https://circleci.com/gh/mdominovic/DevOps_Microservices)

## Project Overview

In this project it was needed to operationalize a given Python flask app, with provided pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). Flask app serves out predictions about housing prices through API calls.

---

Project files:

 * model_data --> directory which contains pre-trained model for predicting housing prices in Boston
 * .circleci --> directory contains `config.yml` file used to configure CirclCI to run pipeline which lints code after every push to a repo
 * output_txt_files --> directory containing outputs needed to pass this project in Udacity's nanodegree course
 * app.py --> flask app written in python used for predicting housing prices
 * Dockerfile --> used to create a Docker container for this project, it setups the environment and runs flask app
 * make_prediction.sh --> script for sending request to API created in this project
 * Makefile --> file for automatization of steps used to setup environment for app and run list and test
 * requirements.txt --> file contains all python pip packages needed to setup environment for flask app
 * run_docker.sh --> bash script for building and running Docker image
 * run_kubernetes.sh --> bash script for deploying app using kubectl, downloads docker container, runs it and forwards container port to host port
 * upload_docker.sh --> uploads Docker image to Docker hub, which is later used by `run_kubernetes.sh` script


---

## Setup the Environment

* Create a virtualenv and activate it
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl

---

Start with genereating docker container by running:
`./run_docker-sh`

After that, verify that flask app is working by running script for sending prediction request:
`./make_repdiction.sh`

If prediction data is returned you are ready to upload your newly created Docker image by running following script:
`./upload_docker.sh`

Now you are ready to deploy your newly created Docker image with kubernetes, run script designed for it:
`./run_kubernetes.sh`

After everything is deployed as expected, you can verify that app is working properly by executing `./make_prediction.sh` script.
