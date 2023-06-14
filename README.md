# MAX78000_prepare_dataset.
Prepare dataset before train AI with MAX78000 object detection ssd by use ai85net-tinierssd model
## Prepare dataset.
![](custom_data.png)

In this case, the preparation of the Dataset Finger Number is given as an example.
### You can labeling images by roboflow and export dataset YOLO v4 PyTorch.
![](roboflow.png)

### After exporting, place that file in your directory.

![](images/export_file.png)

### Extract file .

![](images/extrct_file.png)

### In folder `test` .

![](images/check_in_zip.png)

### 1) Create `test_label` folder.

![](images/create_label_folder.png)

### 2) Select `_annotation.txt` and `_class.txt` .

![](images/move_anno.png)

### 3) Move to `test_label` folder.

![](images/moved_anno.png)

### In `_class.txt` .

![](images/in_class.png)

### In `_annotation.txt` .
![](images/in_anno.png)

### 4) You can use `finger_dataset_convert_format.py` to get renamed images and csv file(all parameter must be use to train an AI).
download `finger_dataset_convert_format.py here: https://github.com/WeerawatW/MAX78000_custom_dataset/blob/cf44a8066d831074396bc79ce04c0f4347fa6c13/github%20python%20file/finger_dataset_convert_format.py
Change your paths for images, text, and csv files, and changes any file names.

![](images/finger_convert.png)

However, in our project, I would ship label +1 of any class because label must also match the output of `finger_number.py` .
### Ship label.

![](images/finger_convert_ship_label.png)

### `finger_number.py` output.
how to place `finger_number.py` see here: https://github.com/WeerawatW/MAX78000-hand_gesture_control#1-ai8x-training

![](images/config_output.png)

The fields have the following meanings:
*  `name`: The dataset name, the name passed in when training the neural network
*  `input`: The size of the neural network input, indicates: the width of the input picture is 74, the height is 74, and 3 represents the three channels of RGB(3, 74, 74)
*  `output`: The neural network outputs classification results , in this project we need to identify 6 classes fingers,and there is 6 output class here.
*  `loader`: A function that loads a dataset and needs to return a tuple. Each dataset has to be implemented and magical. Returns the size of the dataset. Returns a training sample in the format of a tuple. For neural networks with images as input, a three-dimensional array representing the input images. For the object detection task, tuples, composed of all callout boxes, each labeled box is, where coordinates are normalized. 
*   Since each image may have a different number of objects, we need a collate function
        (to be passed to the DataLoader).
        This describes how to combine these tensors of different sizes. We use lists.
        :param batch: an iterable of N sets from __getitem__()
        :return: a tensor of images, lists of varying-size tensors of bounding boxes and labels

Then , Run `finger_dataset_convert_format.py` .

![](images/finger_convert_shiped_label.png)

### Result.
Renamed images.

![](images/rename_images.png)

You'll get `test_info.csv` .

![](images/converted.png)

### Repeat steps 1 through 4 to get `train_info.csv` too, we must be use for training AI step.
step 1) Create `train_label` folder .

step 2) Select `_annotation.txt` and `_class.txt` .

step 3) Move to `test_label` folder .

step 4) Change your paths for images, text, and csv files, and changes any file names from `test` to `train` path.

You will got an same result is renamed images and get `train_info.csv` .

![](images/train_info.png)

### Open `train_info.csv` and `test_info.csv` with Text Editor.

![](images/open_with_text_editor.png)

### In `train_info.csv` and `test_info.csv` .

![](images/in_test_info.png)

### 5) Delete `'` by this step.

![](images/find_and_replace.png)

Click `Replace All`

![](images/replaced.png)

Save file and repeat step 5) for `train_info.csv`

### Create `processed` folder

![](images/create_processed_folder.png)

### Move `train_info.csv` and `test_info.csv` to `processed` folder .

### Congratulation!! , now you have  `processed`, `test`, `train` folder.
Follow the next steps to train AI and generate c code : https://github.com/WeerawatW/MAX78000-hand_gesture_control#1-ai8x-training
