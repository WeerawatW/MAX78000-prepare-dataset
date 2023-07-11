# MAX78000_prepare_dataset.
Prepare dataset before train AI with MAX78000 object detection ssd by use ai85net-tinierssd model
## Prepare dataset.
![](custom_data.png)

If you don't have `data` folder create it.

In this case, the preparation of the Dataset Finger Number is given as an example.
You can labeling images by roboflow and export dataset YOLO v4 PyTorch.
![](roboflow.png)

After exporting, place that file in your directory.

![](images/export_file.png)

Open that file and move `test` and `train` folder from into your directory . 

![](images/extrct_file.png)

Inside  `test` folder.

![](images/check_in_zip.png)


In `_class.txt` .

![](images/in_class.png)

In `_annotation.txt` .
![](images/in_anno.png)

### A step) You can use `finger_dataset_convert_format.py` to get renamed images and csv file(all parameter must be use to train an AI).

Download [finger_dataset_convert_format.py](https://github.com/WeerawatW/MAX78000-prepare-dataset/blob/main/github%20python%20file/finger_dataset_convert_format.py) here,
 This script use for 1)convert .txt  to .csv format 2)rename images files. 

Note: Change ***mode*** to `test`and change ***path*** to extracted directory, `finger_dataset_convert_format.py` file can convert limit only 2 object in 1 image, if you want to add object more than 2 you can modify `finger_dataset_convert_format.py` code.

![](images/finger_convertV2.png)

### Ship label.
For example we have 6 class `finger_number.py` output(1,2,3,4,5,6) but we have labels (0,1,2,3,4,5),
we would ship label +1 of any class because label must also match the output of `finger_number.py` .
> After ship label we have label (1,2,3,4,5,6).... ok this labels match `finger_number.py` output(1,2,3,4,5,6).

![](images/finger_convert_ship_label.png)


Then , Run `finger_dataset_convert_format.py` .

![](images/finger_convert_shiped_label.png)

Result.
After run `finger_dataset_convert_format.py` that program generate `test_rename` folder and `test_info.csv` file.

test_rename (images)

![](images/rename_images.png)

test_info.csv. (annotations)

![](images/converted.png)

### Repeat A step) to get `train_info.csv` too, we must be use for training AI step.
* changes ***mode** `test` to `train`.

You will got an same result is renamed images and get `train_info.csv` .

![](images/train_info.png)

Open `train_info.csv` and `test_info.csv` with Text Editor.

![](images/open_with_text_editor.png)

In `train_info.csv` and `test_info.csv` .

![](images/in_test_info.png)

### 5) Delete `'` by this step.

![](images/find_and_replace.png)

Click `Replace All`

![](images/replaced.png)

Save file and repeat step 5) for `train_info.csv`

than delete these file `test` and `train`, rename `test_rename` folder -> `test` and `train_rename` folder -> `train` folder.

Create `processed` folder

![](images/create_processed_folder.png)

Move `train_info.csv` and `test_info.csv` to `processed` folder .

### Congratulation!! , now you have  `processed`, `test`, `train` folder.
Follow the next steps to train AI and generate c code : https://github.com/WeerawatW/MAX78000-hand_gesture_control#1-ai8x-training
