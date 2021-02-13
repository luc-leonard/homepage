+++
title = "How to make your image dataset"
Date = "2021-01-25"
+++



# How to make your image dataset

I am following the [fastai course](https://course.fast.ai/), wich is really awesome.

In chapter two, we learn to train an image classifier to classify bears. This requires some images of bear.
The book uses the Bing search API.

I did not want to create an azure account, give my credit card number just to run search of bears.
So I started to look for alternative solutions. 

After trying many tools, I found this little gem: https://github.com/deliton/idt


It is very easy to use.
It will automatically download images, and store them in a folder whose nane match their label

Here is the config file I used for the fastai course:
```shell
API_KEY: NONE
CLASSES:
- CLASS_NAME: black_bear
  SEARCH_KEYWORDS: black bear
- CLASS_NAME: grizzly
  SEARCH_KEYWORDS: grizzly
- CLASS_NAME: teddy_bear
  SEARCH_KEYWORDS: teddy bear
DATASET_NAME: bears
ENGINE: duckgo
IMAGE_SIZE: 512
RESIZE_METHOD: smartcrop
SAMPLES_PER_SEARCH: 150

```
I just had to run `idt run` and voila ! a very nice labelled image dataset  !
Now, I have a folder 'bears' which contains 3 subfolders 'teddy_bear', 'grizzly' and 'black bear'

Each of this folder contains 150 images. All images were cropped to by 512 * 512.

