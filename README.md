# MAX78000_prepare_dataset
Prepare dataset before train AI with MAX78000 object detection ssd by use ai85net-tinierssd model
## Prepare dataset
![](custom_data.png)

In this case, the preparation of the Dataset Finger Number is given as an example.
### You can labeling images by roboflow and export dataset YOLO v4 PyTorch.
![](roboflow.png)

### After exporting, place that file in your directory.

![](images/export_file.png)

### Extract file .

![](images/extrct_file.png)

### In folder `test`

![](images/check_in_zip.png)

### Create `test_label` folder

![](images/create_label_folder.png)

### Select `_annotation.txt` and `_class.txt`

![](images/move_anno.png)

### Move to `test_label` folder

![](images/moved_anno.png)

### In `_class.txt`

![](images/in_class.png)

### In `_annotation.txt`
![](images/in_anno.png)

### You can use `finger_dataset_convert_format.py` to get renamed images and csv file(all parameter must be use to train an AI)
download `finger_dataset_convert_format.py here: https://github.com/WeerawatW/MAX78000_custom_dataset/blob/cf44a8066d831074396bc79ce04c0f4347fa6c13/github%20python%20file/finger_dataset_convert_format.py
Change your paths for images, text, and csv files, and changes any file names.

![](images/finger_convert.png)

However, in our project, I would ship label +1 of any class because label must also match the output of `finger_number.py`.
### Ship label

![](images/finger_convert_ship_label.png)

### `finger_number.py` output
how to place `finger_number.py` see here: https://github.com/WeerawatW/MAX78000-hand_gesture_control#1-ai8x-training

![](images/config_output.png)

Then , Run `finger_dataset_convert_format.py`.

![](images/finger_convert_shiped_label.png)

### Result
Renamed images.

![](images/rename_images.png)

You'll get `test_info.csv`.

![](images/converted.png)

### Repeat with these steps to get `train_info.csv` too, we must be use for training step.

![](images/train_info.png)
