# shoes-classifier

A tensorflow image classifier inspired by the [youtube video](https://www.youtube.com/watch?v=QfNvhPx5Px8) from Siraj Raval and an image classification problem from my work.

I installed tensorflow in virtualenv mode explained in the doc [here](https://www.tensorflow.org/install/install_mac).

This repo contains an image downloader python script (img_dl.py), which can search and download 100 images from Google search. Images can be downloaded by providing related search string and a download path. I wanted to classify three different kinds of shoes namely
ladies shoes, men shoes and children shoes. I used various search string like "ladies shoes", "hills shoes", "men shoes", "men formal shoes", "kids shoes", "kids summer shoes" and so on to download various images and train the classifier to identify shoes
in those three categories.

The trainer script is in image_retraining/retrain.py which is available in tensorflow's official [repo](https://github.com/tensorflow/tensorflow).

To retrain the system, first download enough image using img_dl.py in the following folders:
*tf_images/ladies_shoes*, *tf_images/men_shoes*, *tf_images/children_shoes*. The sub-directory name is important. Because sub directory name will be the class name for the images inside that directory.

To start the retrain, run the following command:
```python image_retraining/retrain.py --bottleneck_dir=tf_files/bottlenecks --how_many_training_steps 500 --model_dir=tf_files/inception --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=tf_images```

If everything goes well, you will see the training accuracy in command line.

Now, the moment of truth :)

Download some random shoes images from the Internet and test how well trained is your shoes classifier is:
```python label_image.py test_images/ladies_shoes_with_feet.jpg```

It gave me quite perfect result:
```
ladies shoes (score = 0.97416)
children shoes (score = 0.02114)
men shoes (score = 0.00470)
```



