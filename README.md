# Objects as Points + HarDNet:
Task: Train the model for 3 categories: 1) person 2) Vehiclels - car,truck 3) Vehicles - cat,dog
Selecting the category:
1. Collect the person, car, truck, dog, cat as categories person, vehicle and animal. with person as category 1, vehicle as category 2 and animal as category 
2. create a json file accordingly.


# Filtering categories for custom dataset from json file 

The following command will filter the input instances json to only include images and annotations for the categories person, car, truck, cat and dog: 
~~~
python category_filter.py --input_json path\to\annotations\instances_train2017.json --output_json path\to\annotations\percartruckdogcat.json --categories person car truck dog cat
~~~
The json file created looks like the annotations below.

"categories": [{"supercategory": "person", "id": 1, "name": "person"}, {"supercategory": "vehicle", "id": 2, "name": "car"}, {"supercategory": "vehicle", "id": 2, "name": "truck"}, {"supercategory": "animal", "id": 3, "name": "cat"}, {"supercategory": "animal", "id": 3, "name": "dog"}]

# Changes made for training
1. Edited the coco.py, 
   Figure below shows how to edit the coco.py
   <p align="center"> <img src='readme/coco1.png' align="center" height="44px" width="724" > </p>
   <p align="center"> <img src='readme/coco2.png' align="center" height="230px"> 
    
# Changes made for testing   
3. Edit the test.py as the following images   
   <p align="center"> <img src='readme/prefetch_test.png' align="center" height="230px">
   <p align="center"> <img src='readme/test.png' align="center" height="230px">   
4. Edited the hardnet.py - while testing (no need to edit the hardnet.py while training)
   figure below shows where to edit hardnet.py while testing
   <p align="center"> <img src='readme/hard_posttraining.png' align="center" height="230px"> 



## Training on Windows

We have packed all the training scripts in the [experiments](../experiments) folder.

~~~
python main.py ctdet --exp_id coco_h68 --arch hardnet_68 --batch_size 6 --master_batch 3 --lr 1e-2 --gpus 0 --num_workers 0 --num_epochs 300 --lr_step 230,280
~~~

To evaluate COCO object detection with HarDNet-85
run

~~~
python test.py ctdet --exp_id coco_h68 --arch hardnet_68 --load_model \path\to\model_last.pth
~~~



  

## Citation

For CenterNet Citation, please see [original CenterNet repo](https://github.com/xingyizhou/CenterNet)

For HarDNet Citation, please see [HarDNet repo](https://github.com/PingoLH/Pytorch-HarDNet)
