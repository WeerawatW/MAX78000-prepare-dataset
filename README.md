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

Why we create test_label ? , because we want to keep the image folder and the .txt format folder separate.

### 2) Select `_annotation.txt` and `_class.txt` .

![](images/move_anno.png)

### 3) Cut `_annotation.txt` and `_class.txt` file to `test_label` folder.

![](images/moved_anno.png)

### In `_class.txt` .

![](images/in_class.png)

### In `_annotation.txt` .
![](images/in_anno.png)

### 4) You can use `finger_dataset_convert_format.py` to get renamed images and csv file(all parameter must be use to train an AI).
download `finger_dataset_convert_format.py here: https://github.com/WeerawatW/MAX78000_custom_dataset/blob/cf44a8066d831074396bc79ce04c0f4347fa6c13/github%20python%20file/finger_dataset_convert_format.py

Change your paths for images, text, and csv files, and changes any file names.

Note: that file can convert limit only 2 object in 1 image, if you want to add object more than 2 you can modify `finger_dataset_convert_format.py` code.

![](images/finger_convert.png)

However, in our project, I would ship label +1 of any class because label must also match the output of `finger_number.py` .
### Ship label.

![](images/finger_convert_ship_label.png)


Then , Run `finger_dataset_convert_format.py` .

![](images/finger_convert_shiped_label.png)

### Result.
After run `finger_dataset_convert_format.py` that program generate `test_rename` folder and `test_info.csv` file.

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
than delete these file `test` and `train`, rename `test_rename` folder -> `test` and `train_rename` folder -> `train` folder.

### Congratulation!! , now you have  `processed`, `test`, `train` folder.
Follow the next steps to train AI and generate c code : https://github.com/WeerawatW/MAX78000-hand_gesture_control#1-ai8x-training
