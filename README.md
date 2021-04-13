### Nata or Not Model

Our model uses a convolutional neural network and [TensorFlow][2] to infer if an image is a Pastel de Nata or not.

We took the [Mobilenet V3][1] pre-trained network and trained a new layer on top of it with thousands of Portuguese egg custard tart (Pasteis de Nata) images and other non related images to get the "Nata or Not" classifier. The model was trained on a server with an [NVIDIA A100][4] Tensor Core GPU. Check our Jupyter [notebook][5] for details and code, inspired by the "Retraining an Image Classifier" [tutorial][6].

#### The dataset

To get a reasonable training dataset, we simply used as many Creative Commons images as possible from Google Images using the "[pastel de nata][3]" keywords. We also added a few of our own; the Lisbon Office is quite a fan of the famous pastry.

Finally, we also searched for non-egg tart images, the kind we think would be the most common for people to try out, like other foods, furniture, pets, people, and, of course, hotdogs.

#### How to build your own

Get your dataset and use the following folder structure to place the `pastel` and `not-pastel` images.

```
nata-model
│   notebooks
└───data
    |   pastel
    └───not-pastel
```

Setup your python environment using python 3.7.10:

  ```
  python3 -m venv venv
  source venv/bin/activate
  pip install -r requirements.txt
  ```

Run the notebook:

  ```
  cd notebooks
  jupyter notebook
  ```

#### How to use ours

To perform an inference run this notebook [notebooks/inference.ipynb][10]. You can change the [default image][11] in the `fpath` variable.

#### Demo

We did a little [live demo][7] using this TensorFlow model using Cloudflare Workers and a Cloudflare server which has an [NVIDIA A100][9] Tensor Core GPU in it.

Check our [blog post][8] for more information.

[1]: https://www.tensorflow.org/api_docs/python/tf/keras/applications/mobilenet_v3
[2]: https://www.tensorflow.org/
[3]: https://www.google.com/search?as_st=y&tbm=isch&hl=en&as_q=pastel+de+nata&tbs=sur%3Acl
[4]: https://www.nvidia.com/en-us/data-center/a100/
[5]: notebooks/training.ipynb
[6]: https://www.tensorflow.org/hub/tutorials/tf2_image_retraining
[7]: https://nataornot.com/
[8]: https://blog.cloudflare.com/workers-ai/
[9]: https://www.nvidia.com/en-us/data-center/a100/
[10]: notebooks/inference.ipynb
[11]: https://commons.wikimedia.org/wiki/File:Past%C3%A9is_de_Nata_(49066414092).jpg
