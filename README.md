# MNIST-ML-API

This project demonstrate how to deploy and use a Flask application for image classification trained using Convolutional Neural Network (CNN) model on the MNIST dataset. The model was trained using PyTorch and then saved to a .pt file. This .pt file is then loaded and used for predictions in the Flask app. The Flask app allows users to upload an image of a hand-written digit, which will then be classified and the predicted number will be displayed to the user.

## Prerequisites
- Python 3
- Docker
- Docker Compose
- Flask
- Torch
- Numpy
- Matplotlib



## Directory Structure
The project has the following structure:<br>

MNIST/<br>
|<br>
|-- `app.py` <br>
|-- `model.pt`<br>
|-- `templates`/<br>
|-- |-- `index.html`<br>
|-- |-- `prediction.html`<br>
|-- `requirements.txt`<br>
|-- `model.py` <br>
|-- `docker-compose.yml` <br>
|-- `Dockerfile` <br>
|-- `mnist_png` <br>

- `app.py` contains the main code for the Flask application and serves as ML model API.
- `model.py` contins the model code that was used to train CNN model.
- `model.pt` is the trained PyTorch model saved as pickle file.
- `templates/` contains the HTML templates for the Flask application.
- `requirements.txt` lists all the required packages for the project.
- `docker-compose.yml`and `Dockerfile` are used to create a Docker container for the project.
- `mnist_png` contais the folders for all hand written digits.

## API Deployment Steps:

1. Clone the project repository.
```
$ git clone https://github.com/rajvyas32/MNIST-ML-API.git
```

2. Change into the project directory.
```
$ cd MNIST-ML-API/MNIST
```

3. Start the Docker containers using Docker Compose.
```
$ docker-compose up
```

## Docker Compose
The above Docker Compose command sets up a service named "app" built using Dockerfile. The service maps the host's port 5000 to the container's port 5000, and runs the command python3 app.py when the container is launched. 
The Dockerfile creates a Docker image for a Python application. It is set up in a way that if there are no changes in requirement.txt than it will skip installing all dependencies in next built.

## API Usage:

Once the flask application is up and running on container you can go to following endpoint:

```
http://127.0.0.1:5000/
```

This will redirect you to the index.html where you can upload the image (from MNIST dataset) and click predict button.

![image](https://user-images.githubusercontent.com/124141023/216219311-e68e1b56-343b-46c3-bfa8-ab679889d141.png)

If you click predict button without uploading the image it will prompt following message:

![image](https://user-images.githubusercontent.com/124141023/216219616-4b18eb42-dc64-4c2a-a7e2-f8382285810d.png)

If you upload an image other than MNIST dataset or image with improrer dimensions it will return you following message on clicking predict button:

![image](https://user-images.githubusercontent.com/124141023/216220821-001b95d9-2a6f-4f93-b3aa-c8683ac8c53f.png)


The images to upload can be found in "mnist_png" folder of this repo. Otherwise, you can go to https://huggingface.co/datasets/severo/mnist and download the image for testing.
Once, you upload the correct image and click predict button it will redirect you to the prediction.html page which shows your uploaded image and the predicted number:

![image](https://user-images.githubusercontent.com/124141023/216219834-cd0e1f59-f504-439e-b485-033aadc00626.png)

From here, you can click the button "Back to Home" which will redirect you back to index.html

Hurrah!!! I hope you like it.
