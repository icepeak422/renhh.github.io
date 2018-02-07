## Welcome to Hang Ren Personal page

<title>
	Hang Ren
</title>
Here are my posts!!!!!!!!!!!!
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)

```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/renhh/renhh.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

# lane_detection_alex
## Download the dataset
The dataset is from Caltech website: http://www.mohamedaly.info/datasets/caltech-lanes

## dl_alexnet
I choose alexnet from matlab nerual network tool box to finish this task. Here I have to modify the structure of alexnet.

```
% Replace the last few fully connected layers with suitable size layers
layers(20:25) = [];
outputLayers = [ ...
fullyConnectedLayer(16, 'Name', 'fcLane1');
reluLayer('Name','fcLane1Relu');
fullyConnectedLayer(12, 'Name', 'fcLane2');
regressionLayer('Name','output')];
untrained_net = [layers; outputLayers];

```


## How to deal with the raw image
First, compress the image to 227x227x3 using image_compress.m which is the input of alexnet.

Second, open labeler.m to label the image, we initially label three points for each lane. When you are labeling different folder, remember to change the directory's name.

Here I have already labeled two folder: cordova1 and washington1, the ground truth label all in gt_c1w1.m file.

## Train the alexnet

1. Divide the whole dataset to different poportion to train, validate, and test the network

```
[trainInd,valInd,testInd] = dividerand(num_slice,0.8,0.1,0.1);
```

 2.run train_dl_network.m to see the training process.
 
 ## Test the alexnet
run test_dl.m to see the network performance on testset. the little red line on the right is the part of the ground truth of the image.

