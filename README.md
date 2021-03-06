# AI Tools
- [formula.md](./formula.md) : AI相关公式
- [grid.xlsx](./grid.xlsx) ：可打印的网络格子
- [img_resize.py](./img_resize.py) ：图像缩放(注意`Annotations`为二级文件夹，即里面还有一层文件夹)       
    ```shell
    python img_resize.py /home/data/Annotations /home/data/JPEGImages /home/data/output_draw
    ```
- [video2pic.py](./video2pic.py) ： 将视频切割为图像(h264、mkv视频格式，保存为png图像)，其中`video_folders`的文件结构为`video_folders/video_folder/video.h264`，即`20181013_city/dw_20181013_132808_0.000000_0.000000/video_first.h264`
  ```shell
    input: 
        python video2pic.py \
        /home/andy/data/train/video_folders \
        /home/andy/data/train/output_folder
    output: 
        /home/andy/data/train/output_folder/video_folder/
    ```
- [files2folders.py](./files2folders.py) ： 将图像/文件按照制定数量放到按照命名规则的文件夹中
  ```shell
    input: 
        python files2folders.py /home/andy/data/image_folder ./result_folder
    output: 
        ./result_folder
    ```
- [drawbox.py](./drawbox.py) ： 将label绘制在图中并存储在指定文件夹(注意`json`为二级文件夹，即里面还有一层文件夹)      
  ```shell
  input : python drawbdd.py  /home/data/json /home/data/img /home/data/output_draw
  output:
	     /home/data/output_draw
  ```
- [pick_ROI.py](./pick_ROI.py) ： 提取标注好的ROI区域
  ```shell
  input : python3 pick_ROI.py  /home/andy/data/ann_dir  /home/andy/data/img_dir
  output:
	     ./ROIs/
  ```
- [pick_ROI.py](./processpublicdata.py) ： 处理公共数据集数据(提取ROI区域、绘制外界边框)
  ```shell
  input : python processpublicdata.py /home/andy/data/txt /home/andy/data/img  /drawout /ROIs
  output:
	    ./drawout
        ./ROIs
  ```
- [create_train_data.py](./create_train_data.py) ： 训练数据加强，其中`ROIs`文件夹下保存的是`pick_ROI.py`程序执行后比较理想的结果
  ```shell
  input : python3 create_train_data.py /home/andy/data/ann_dir /home/andy/data/img_dir /home/andy/data/ROIs --num 1000
  output:  
        ./new_img
        ./new_label
  ```
- [abspath2txt.py](./abspath2txt.py) : 将文件夹中文件的绝对路径保存到txt中
    ```shell
    input: 
        python3 abspath2txt.py /home/andy/Data/img
    output: 
        ./imgPath.txt
    ```
- [json2yolo.py](./json2yolo.py) ： 将json标注文件转换为yolo格式，其中`json_folders`的文件结构为`json_folders/json_folder/json`，即`json/072901/20180729_0001_500.json`
    ```shell
    input: 
        python3 json2yolo.py /home/andy/data/json_folders ./output_folder
    output: 
        ./output_folder
    ```
- [img2train.py](./img2train.py) ： 将图像分为训练和验证集，保存为train.txt和val.txt
    ```shell
    input: 
        python3 img2train.py /home/andy/Data/img
    output: 
        ./train.txt
        ./val.txt
    ```
- [img2train_with_check_img.py](./img2train_with_check_img.py) ： 检验图像并将图像分为训练和验证集，保存为train.txt和val.txt

- [pick_img_by_list.py](./pick_img_by_list.py) ： 根据txt中的图像列表将图像和标签提取出来
    ```shell
    input: 
        python3 pick_img_by_list.py /home/andy/data/val.txt /home/andy/data/labels /home/andy/data/img
    output: 
        ./pickedLabel
        ./pickedImg
    ```
- [create_VOC_txt.py](./create_VOC_txt.py) ： 创建VOC-like的txt文件，其中Main文件夹下的只有文件名，当前文件夹下的是完整的目录
    ```shell
    input: 
        python3 create_txt_list.py /home/andy/Data/img
    output: 
        ./VOC/ImageSets/Main/train.txt
        ./VOC/ImageSets/Main/val.txt
        ./train.txt
        ./val.txt
    ```
- [showprocessbar.py](./showprocessbar.py) ： 显示处理进度脚本
- [pick_xml_img_by_xml.py](./pick_xml_img_by_xml.py) ： 从同一个文件夹中挑选xml和image文件分别到相应文件夹中
    ```shell
    input: 
        python3 pick_xml_img_by_xml.py /home/andy/data/labels /home/andy/data/img 
    output:    
        ./pickedLabel
        ./pickedImg
    ```
- [pick_xml_img_by_img.py](./pick_xml_img_by_img.py) ： 根据图片文件夹将图片和标注文件挑选出来
    ```shell
    input: 
        python pick_all_xml_img.py /home/andy/data/labels /home/andy/data/img
    output:    
        ./pickedLabel
        ./pickedImg
    ```
- [pick_txt_img_by_label.py](./pick_txt_img_by_label.py) : 根据指定标签将txt和image文件挑出来
    ```shell
    input : 
        python3 pick_txt_img_by_label.py  /home/andy/data/label_dir/  /home/andy/data/img_dir/ 
    output : 
        ./pickedLabel
        ./pickedImg
    ```
- [txt2xml.py](./txt2xml.py) ： YOLO的txt标签转VOC的xml格式标签脚本
    ```shell
    input : 
        python3 txt2xml.py /home/andy/data/ann_dir /home/andy/data/img_dir
    output:
        ./xml
    ```
- [xml2txt.py](./xml2txt.py)　：　VOC数据集xml标签转YOLO需要的txt格式的标签脚本
    ```shell
    input : 
        python3 xml2txt.py /home/andy/data/xml  /home/andy/data/img
    output :
        ./txt
        ./train.txt
        ./val.txt
        ./trainAll.txt
    ```

- [pick_non_empty_txt.py](./pick_non_empty_txt.py) : 提取text文件夹中非空的text文件
    ```shell
    input : 
        python3 rm_empty_txt.py /home/andy/data/txt  /home/andy/data/img
    output :
        ./dst_txt
        ./dst_img
    ```
- [count_classes_by_txt.py](./count_classes_by_txt.py) : 通过txt标注文件统计每一类的数量
    ```shell
    input : 
        python3 count_classes.py  /home/andy/data/txt_dir/
    output :
        ./classes_label_txt.txt
        ./classes_index_txt.txt
    ```
- [calculate_boxes.py](./calculate_boxes.py) : 统计 `json` 文件中boundingbox数量；    
- Caffe数据预处理
  - [creat_caffe_filelist.sh](./caffe/creat_caffe_filelist.sh)
  - [creat_caffe_lmdb.sh](./caffe/creat_caffe_lmdb.sh)
  - [make_myself_mean.sh](./caffe/make_myself_mean.sh)
- YOLO数据预处理
  - [processData.ipynb](./darknet/processData.ipynb)

- TensorRT
  - [Tensorflow to UFF](tensorrt/tf_to_uff.py)
  - [UFF to Engine](tensorrt/uff_to_engine.py)