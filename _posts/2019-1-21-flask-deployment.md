---
layout: post
title: Deep Learning deployment using Flask
---

**[Heroku live web-app][heroku-app-url]**


**Table of Contents**
- [Pre-request][pre-request]
- [Usage / Installation][usage]
- [Code structure][code_structure]
- [Deep Learning Model][ml-model]
- [Flask Webapp code][web-app]
- [Integration of DL model with Flask app][integration]
- [Deployment][deployment]



# <a name="pre-request"></a>Pre-request

You should have basic understanding of:
- Python, pip, virtual environment, Flask
- Machine Learning / Deep Learning
- HTML, CSS, JavaScript



# <a name="usage"></a>Usage / Installation

### Local

Clone/download code for this demo from [mnist-demo github repo][repo_url]

```bash
git clone https://github.com/sumit-kothari/mnist-demo.git
```

Navigate to root of the project and install required dependencies

```bash
cd mnist-demo
pip install -r requirements.txt
```

Run Flask app locally
```bash
python app.py
```

### Deploy to heroku

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/sumit-kothari/mnist-demo/tree/master)



# <a name="code_structure"></a>Code Structure

![_config.yml]({{ site.baseurl }}/images/code_structure.png)



# <a name="ml-model"></a>DL Model

### Training deeplearning model

[train-mnist.py][train-mnist.py] contains the code to train a deeplearning model.

**Last line** in the code helps us in **saving our keras/tensorflow model**.

<script src="https://gist-it.appspot.com/github/sumit-kothari/mnist-demo/blob/master/tensorflow_model/train-mnist.py?slice=-6:"></script>


### Testing deeplearning model

The model saved during training, is used for testing purpose.

Also we have created our testing script (i.e [predict.py][predict.py]) as a module, therefore we can load it easily in other python scripts which we can use during prediction.

Following is the **logic used in [predict.py][predict.py]:**

- Load the model and graph 

<script src="https://gist-it.appspot.com/github/sumit-kothari/mnist-demo/blob/master/tensorflow_model/predict.py?slice=7:13"></script>


- Method `predict_image` takes **image as input** and **returns image label with confidence/probability** 

- In `predict_image`, first we convert image to gray-scale, save in numpy array and re-shape it to 1x28x28  

- Finally in `predict_image`, we pass this test image array to `model.predict` method, which help us in predicting the most probable label with its probability

<script src="https://gist-it.appspot.com/github/sumit-kothari/mnist-demo/blob/master/tensorflow_model/predict.py?slice=14:34"></script>



[pre-request]: #pre-request
[usage]: #usage
[code_structure]: #code_structure
[ml-model]: #ml-model
[web-app]: #web-app
[integration]: #integration
[deployment]: #deployment
[train-mnist.py]: [https://github.com/sumit-kothari/mnist-demo/blob/master/tensorflow_model/train-mnist.py]
[predict.py]: [https://github.com/sumit-kothari/mnist-demo/blob/master/tensorflow_model/predict.py]
[heroku-app-url]: https://mnist-demo-app.herokuapp.com/
[repo_url]: https://github.com/sumit-kothari/mnist-demo
