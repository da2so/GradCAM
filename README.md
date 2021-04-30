# GradCAM PyTorch

![Python version support](https://img.shields.io/badge/python-3.6-blue.svg)
![PyTorch version support](https://img.shields.io/badge/pytorch-1.7.0-red.svg)

:star: Star us on GitHub — it helps!!

PyTorch implementation for *[Grad-CAM: Visual Explanations from Deep Networks via Gradient-based Localization](https://arxiv.org/abs/1610.02391)*

![2](./assets/fig1.png)

## Install

You will need a machine with a GPU and CUDA installed.  
Then, you prepare runtime environment:

   ```shell
   pip install -r requirements.txt
   ```

## Use

```shell
CUDA_VISIBLE_DEVICES=0 python main.py --model_path=resnet50 --img_path=examples/catdog.png --select_t_layer=False
```

Arguments:

- `model_path` - Choose a pretrained model in torchvision.models or saved model (.pt) 
	- Examples of available list: ['alexnet', 'vgg19', 'resnet50', 'densenet169', 'mobilenet_v2' ,'wide_resnet50_2', ...]
- `img_path` - Image Path
- `select_t_layer` -  Choose a target layer manually?
	- If True, you can select a layer and get GradCAM for the layer.
	- Elif False, you can get GradCAM automatically.


### Guide for selecting a target layer manually 

If you want to select a target layer manually, you run the following code:

```shell
CUDA_VISIBLE_DEVICES=0 python main.py --model_path=resnet50 --img_path=examples/catdog.png --select_t_layer=True
```

You can get system print such as the following figure (left).  
Suppose that you select(type) 'number' or 'name' of a target layer like as the figure (middle).
And then, you can get GradCAM result. 

![2](./assets/fig2.png)

### How to use your customized model

If you want to use a customized model that has a data type 'OrderedDict', you shoud type a code that loads model object.

Search 'load model' function in utils.py and type a code such as:

```shell
from yourNetwork import yourNetwork())
model=yourNetwork()
```


## Understanding GradCAM

:white_check_mark: Check my blog!!
[GradCAM in da2so](https://da2so.github.io/2020-08-10-GradCAM/)