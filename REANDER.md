# MTCNN  BASEDE ON TENSORFLOW
人脸检测MTCNN算法，采用tensorflow框架编写，含测试和训练，支持摄像头。代码来源：[forked from LeslieZhoa/tensorflow-MTCNN ](https://github.com/LeslieZhoa/tensorflow-MTCNN)
##  测试环境
window10<br>
vscode<br>
python3.6.5<br>
tensorflow1.8.0<br>
opencv3.4.3<br>
import tqdm为了显示进度条<br>
## 模型理解
[MTCNN](https://kpzhang93.github.io/MTCNN_face_detection_alignment/index.html)是目前比较流行的人脸检测方法，通过人脸检测可以进行更精准的人脸识别。模型主要通过PNet，RNet，ONet三个网络级联，一步一步精调来对人脸进行更准确的检测.
### 代码介绍
data下放置训练所用的原始数据和划分数据，生成的tfrecord等<br><br>
detection下的fcn_detector.py主要用于PNet的单张图片识别，detector.py用于RNet和ONet的一张图片通过PNet截取的多个人脸框的批次识别，MtcnnDetector.py为识别人脸和生成RNet，ONet输入数据<br><br>
graph里放置的是训练过程中生成的graph文件<br><br>
output里放置识别图像或视频完成后存储放置的路径<br><br>
picture里是要测试的图像放置路径<br><br>
preprocess里是预处理数据程序，BBox_utils.py和utils.py，loader.py是一些辅助程序，gen_12net_data.py是生成PNet的pos，neg,part的程序，gen_landmark_aug.py是生成landmark数据的程序，gen_imglist_pnet.py是pnet的四种数据组合一起，gen_hard_example.py是生成rnet,onet的三种数据程序，gen_tfrecords.py是生成tfrecord文件的程序<br><br>
train中的config是一些参数设定，model.py是模型,train.py是训练，train_model.py针对不同网络训练<br><br>
test.py是测试代码<br>
## 测试:<br>
主要在训练好的模型上直接训练，将欲测试的图片放到picture目录下。然后再vscode控制台上运行下面代码:<br>
python test.py<br>
## 注意事项：
 如果import opencv 时出现问题，需要 pip install 与python相应版本的opencv.
 测试的图片尺寸大小最好200x180以上，小的尺寸可以cv2.resize调整.
 
