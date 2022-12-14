<h2>EfficientNet-Malignant-Lymphoma (Updated: 2022/09/14)</h2>
<a href="#1">1 EfficientNetV2 Malignant Lymphoma Classification </a><br>
<a href="#1.1">1.1 Clone repository</a><br>
<a href="#1.2">1.2 Prepare Malignant Lymphoma dataset</a><br>
<a href="#1.3">1.3 Install Python packages</a><br>
<a href="#2">2 Python classes for Malignant Lymphoma Classification</a><br>
<a href="#3">3 Pretrained model</a><br>
<a href="#4">4 Train</a><br>
<a href="#4.1">4.1 Train script</a><br>
<a href="#4.2">4.2 Training result</a><br>
<a href="#5">5 Inference</a><br>
<a href="#5.1">5.1 Inference script</a><br>
<a href="#5.2">5.2 Sample test images</a><br>
<a href="#5.3">5.3 Inference result</a><br>
<a href="#6">6 Evaluation</a><br>
<a href="#6.1">6.1 Evaluation script</a><br>
<a href="#6.2">6.2 Evaluation result</a><br>

<h2>
<a id="1">1 EfficientNetV2 Malignant Lymphoma Classification</a>
</h2>

 This is an experimental EfficientNetV2 Malignant Lymphoma Classification project based on <b>efficientnetv2</b> in <a href="https://github.com/google/automl">Brain AutoML</a>.
<br>
The original  Malignant Lymphoma dataset has been taken from the following website:<br>

<a href="https://www.kaggle.com/datasets/andrewmvd/malignant-lymphoma-classification">Malignant Lymphoma Classification</a>

<br> 
Three types of malignant lymphoma are represented in the set:
<br>
CLL (chronic lymphocytic leukemia);<br>
FL (follicular lymphoma);<br>
MCL (mantle cell lymphoma).<br>

<pre>
Original Article
Orlov, Nikita & Chen, Wayne & Eckley, David & Macura, Tomasz & Shamir, Lior & Jaffe, Elaine & Goldberg, Ilya. (2010). Automatic Classification of Lymphoma Images With Transform-Based Global Features. IEEE transactions on information technology in biomedicine : a publication of the IEEE Engineering in Medicine and Biology Society. 14. 1003-13. 10.1109/TITB.2010.2050695.

BibTeX
@article{article,
author = {Orlov, Nikita and Chen, Wayne and Eckley, David and Macura, Tomasz and Shamir, Lior and Jaffe, Elaine and Goldberg, Ilya},
year = {2010},
month = {07},
pages = {1003-13},
title = {Automatic Classification of Lymphoma Images With Transform-Based Global Features},
volume = {14},
journal = {IEEE transactions on information technology in biomedicine : a publication of the IEEE Engineering in Medicine and Biology Society},
doi = {10.1109/TITB.2010.2050695}
}
License
License was not specified at the source
</pre>
<br>
<br>We use python 3.8 and tensorflow 2.8.0 environment on Windows 11.<br>
<br>

<h3>
<a id="1.1">1.1 Clone repository</a>
</h3>
 Please run the following command in your working directory:<br>
<pre>
git clone https://github.com/atlan-antillia/EfficientNet-Malignant-Lymphoma.git
</pre>
You will have the following directory tree:<br>
<pre>
.
??????asset
??????efficientnetv2-m
??????projects
    ??????Malignant-Lymphoma
        ??????eval
        ??????evaluation
        ??????inference
        ??????Malignant_Lymphoma_Images
        ???  ??????test
        ???  ???  ??????CLL
        ???  ???  ??????FL
        ???  ???  ??????MCL
        ???  ??????train
        ???      ??????CLL
        ???      ??????FL
        ???      ??????MCL
        ??????models
        ??????test
</pre>
<h3>
<a id="1.2">1.2 Prepare Malignant Lymphoma dataset</a>
</h3>

Please download the dataset <b>Malignant Lymphoma dataset</b> from the following web site:
<br>
<a href="https://www.kaggle.com/datasets/andrewmvd/malignant-lymphoma-classification">Malignant Lymphoma Classification</a>

<br>

As a working master dataset, we have created <b>Malignant_Lymphoma-jpg-master_840x840</b> dataset from the original <b>Malignant Lymphoma</b> above
 by using python script <a href="./projects/Malignant-Lymphoma/convert.py"> convert.py </a>.<br>
<pre>
Malignant_Lymphoma-jpg-master_840x840
  ??????CLL
  ??????FLL
  ??????MCL
</pre>
Futhermore, we have created <b>Malignant_Lymphoma_Images</b> dataset by splitting the master dataset to
 train and test sets by using a script <a href="./projects/Malignant-Lymphoma/split_master.py">split_master.py</a>.
<br>
<pre>
Malignant_Lymphoma_Images
  ??????test
  ???  ??????CLL
  ???  ??????FL
  ???  ??????MCL
  ??????train
      ??????CLL
      ??????FL
      ??????MCL</pre>
<br>
<br>
The number of images in classes of train and test sets:<br>
<img src="./projects/Malignant-Lymphoma/_Malignant_Lymphoma_Images_.png" width="740" height="auto"> 
<br>
<br>
Sample images of Malignant-Lymphoma/train/CLL:<br>
<img src="./asset/Malignant-Lymphoma_train_CLL.png" width="840" height="auto">
<br>
<br>
Sample images of Malignant-Lymphoma/train/FL:<br>
<img src="./asset/Malignant-Lymphoma_train_FL.png" width="840" height="auto">
<br>
<br>
Sample images of Malignant-Lymphoma/train/MCL:<br>
<img src="./asset/Malignant-Lymphoma_train_MCL.png" width="840" height="auto">
<br>

<h3>
<a id="#1.3">1.3 Install Python packages</a>
</h3>
Please run the following commnad to install Python packages for this project.<br>
<pre>
pip install -r requirements.txt
</pre>
<br>

<h2>
<a id="2">2 Python classes for Malignant Lymphoma Classification</a>
</h2>
We have defined the following python classes to implement our Malignant Lymphoma Classification.<br>
<li>
<a href="./ClassificationReportWriter.py">ClassificationReportWriter</a>
</li>
<li>
<a href="./ConfusionMatrix.py">ConfusionMatrix</a>
</li>
<li>
<a href="./CustomDataset.py">CustomDataset</a>
</li>
<li>
<a href="./EpochChangeCallback.py">EpochChangeCallback</a>
</li>
<li>
<a href="./EfficientNetV2Evaluator.py">EfficientNetV2Evaluator</a>
</li>
<li>
<a href="./EfficientNetV2Inferencer.py">EfficientNetV2Inferencer</a>
</li>
<li>
<a href="./EfficientNetV2ModelTrainer.py">EfficientNetV2ModelTrainer</a>
</li>
<li>
<a href="./FineTuningModel.py">FineTuningModel</a>
</li>

<li>
<a href="./TestDataset.py">TestDataset</a>
</li>

<h2>
<a id="3">3 Pretrained model</a>
</h2>
 We have used pretrained <b>efficientnetv2-m</b> to train Malignant Lymphoma FineTuning Model.
Please download the pretrained checkpoint file from <a href="https://storage.googleapis.com/cloud-tpu-checkpoints/efficientnet/v2/efficientnetv2-m.tgz">efficientnetv2-m.tgz</a>, expand it, and place the model under our top repository.

<pre>
.
??????asset
??????efficientnetv2-m
??????projects
    ??????Malignant-Lymphoma
  ...
</pre>

<h2>
<a id="4">4 Train</a>

</h2>
<h3>
<a id="4.1">4.1 Train script</a>
</h3>
Please run the following bat file to train our Lung Colon efficientnetv2 model by using
<b>Malignant_Lymphoma_Images/train</b>.
<pre>
./1_train.bat
</pre>
<pre>
rem 1_train.bat
python ../../EfficientNetV2ModelTrainer.py ^
  --model_dir=./models ^
  --eval_dir=./eval ^
  --model_name=efficientnetv2-m  ^
  --data_generator_config=./data_generator.config ^
  --ckpt_dir=../../efficientnetv2-m/model ^
  --optimizer=rmsprop ^
  --image_size=384 ^
  --eval_image_size=480 ^
  --data_dir=./Malignant_Lymphoma_Images/train ^
  --data_augmentation=True ^
  --valid_data_augmentation=True ^
  --fine_tuning=True ^
  --monitor=val_loss ^
  --learning_rate=0.0001 ^
  --trainable_layers_ratio=0.4 ^
  --dropout_rate=0.4 ^
  --num_epochs=50 ^
  --batch_size=4 ^
  --patience=10 ^
  --debug=True  
</pre>
, where data_generator.config is the following:<br>
<pre>
; data_generation.config

[training]
validation_split   = 0.2
featurewise_center = True
samplewise_center  = False
featurewise_std_normalization=True
samplewise_std_normalization =False
zca_whitening                =False
rotation_range     = 180
horizontal_flip    = True
vertical_flip      = True 
width_shift_range  = 0.2
height_shift_range = 0.2
shear_range        = 0.01
zoom_range         = [0.1, 2.0]
data_format        = "channels_last"

[validation]8
validation_split   = 0.2
featurewise_center = True
samplewise_center  = False
featurewise_std_normalization=True
samplewise_std_normalization =False
zca_whitening                =False
rotation_range     = 180
horizontal_flip    = True
vertical_flip      = True
width_shift_range  = 0.2
height_shift_range = 0.2
shear_range        = 0.01
zoom_range         = [0.1, 2.0]
data_format        = "channels_last"
</pre>

<h3>
<a id="4.2">4.2 Training result</a>
</h3>

This will generate a <b>best_model.h5</b> in the models folder specified by --model_dir parameter.<br>
Furthermore, it will generate a <a href="./projects/Malignant-Lymphoma/eval/train_accuracies.csv">train_accuracies</a>
and <a href="./projects/Malignant-Lymphoma/eval/train_losses.csv">train_losses</a> files
<br>
Training console output:<br>
<img src="./asset/Malignant-Lymphoma_train_at_epoch_24_0913.png" width="740" height="auto"><br>
<br>
Train_accuracies:<br>
<img src="./projects/Malignant-Lymphoma/eval/train_accuracies.png" width="640" height="auto"><br>

<br>
Train_losses:<br>
<img src="./projects/Malignant-Lymphoma/eval/train_losses.png" width="640" height="auto"><br>

<br>
<h2>
<a id="5">5 Inference</a>
</h2>
<h3>
<a id="5.1">5.1 Inference script</a>
</h3>
Please run the following bat file to infer the breast cancer in test images by the model generated by the above train command.<br>
<pre>
./2_inference.bat
</pre>
<pre>
rem 2_inference.bat
python ../../EfficientNetV2Inferencer.py ^
  --model_name=efficientnetv2-m  ^
  --model_dir=./models ^
  --fine_tuning=True ^
  --trainable_layers_ratio=0.4 ^
  --dropout_rate=0.4 ^
  --image_path=./test/*.jpg ^
  --eval_image_size=480 ^
  --label_map=./label_map.txt ^
  --mixed_precision=True ^
  --infer_dir=./inference ^
  --debug=False 
</pre>
<br>
label_map.txt:
<pre>
CLL
FL
MCL
</pre>
<br>
<h3>
<a id="5.2">5.2 Sample test images</a>
</h3>

Sample test images generated by <a href="./projects/Malignant-Lymphoma/create_test_dataset.py">create_test_dataset.py</a> 
from <a href="./projects/Malignant-Lymphoma/Malignant_Lymphoma_Images/test">Malignant_Lymphoma_Images/test</a>.
<br>
<img src="./asset/Malignant-Lymphoma_test.png" width="840" height="auto"><br>

<h3>
<a id="5.3">5.3 Inference result</a>
</h3>
This inference command will generate <a href="./projects/Lung-Colon-Cancer/inference/inference.csv">inference result file</a>.
<br>
<br>
Inference console output:<br>
<img src="./asset/Malignant-Lymphoma_infer_at_epoch_24_0913.png" width="740" height="auto"><br>
<br>

Inference result (inference.csv):<br>
<img src="./asset/Malignant-Lymphoma_inference_at_epoch_24_0913.png" width="740" height="auto"><br>
<br>
<h2>
<a id="6">6 Evaluation</a>
</h2>
<h3>
<a id="6.1">6.1 Evaluation script</a>
</h3>
Please run the following bat file to evaluate <a href="./projects/Malignant-Lymphoma/Malignant_Lymphoma_Images/test">
Malignant_Lymphoma_Images/test</a> by the trained model.<br>
<pre>
./3_evaluate.bat
</pre>
<pre>
rem 3_evaluate.bat
python ../../EfficientNetV2Evaluator.py ^
  --model_name=efficientnetv2-m  ^
  --model_dir=./models ^
  --data_dir=./Malignant_Lymphoma_Images/test ^
  --evaluation_dir=./evaluation ^
  --fine_tuning=True ^
  --trainable_layers_ratio=0.4 ^
  --dropout_rate=0.4 ^
  --eval_image_size=480 ^
  --mixed_precision=True ^
  --debug=False 
</pre>
<br>

<h3>
<a id="6.2">6.2 Evaluation result</a>
</h3>

This evaluation command will generate <a href="./projects/Malignant-Lymphoma/evaluation/classification_report.csv">a classification report</a>
 and <a href="./projects/Malignant-Lymphoma/evaluation/confusion_matrix.png">a confusion_matrix</a>.
<br>
<br>
Evaluation console output:<br>
<img src="./asset/Malignant-Lymphoma_evaluate_at_epoch_24_0913.png" width="740" height="auto"><br>
<br>

<br>
Classification report:<br>
<img src="./asset/Malignant-Lymphoma_classificaiton_report_at_epoch_24_0913.png" width="740" height="auto"><br>
<br>
Confusion matrix:<br>
<img src="./projects/Malignant-Lymphoma/evaluation/confusion_matrix.png" width="740" height="auto"><br>


<br>
<h3>
References
</h3>
<b>1. Malignant Lymphoma Classification</b>
<pre>
https://www.kaggle.com/datasets/andrewmvd/malignant-lymphoma-classification
</pre>
<b>2. Malignant lymphoma classification<br>
Elaine Jaffe (National Cancer Institute) and Nikita Orlov (National Institute on Aging)
</b>
<pre>
https://academictorrents.com/details/3cde17e7e4d9886513630c1005ba20b8d37c333a
</pre>

