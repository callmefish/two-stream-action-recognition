# two-stream-action-recognition
A binary action recognition model for detecting "Slipping". The model based on two-stream CNN model and built by Pytorch.

# Note
The latest version of project has been moved to https://github.com/callmefish/CSCE636ActionRecognition .

# Demo video
https://www.youtube.com/watch?v=v4Yl3FdkZOA

# Environment
```
VM: Google cloud deeplearning-vm
Framework: PyTorch-1.4
Based on: Debian GNU/Linux 9.11 (stretch) (GNU/Linux 4.9.0-11-amd64 x86_64\n)
Programming Language: Python 3.7 from Anaconda.
Machine type: n1-highmem-4 (4 vCPUs, 26 GB memory)
GPUs: 1 x NVIDIA Tesla K80
```

# Prepare Steps

 1. Clone code from github:
 	```
 	git clone https://github.com/callmefish/two-stream-action-recognition.git
 	```
 2. Download dataset and unzip them, suggest use 475 dataset:\
	[rgb_497](https://storage.cloud.google.com/ucf101_for_rar/video_data_497.zip?authuser=1)(gs://ucf101_for_rar/video_data_497.zip): A dataset of RGB frames extracted from 497 action videos\
        [rgb_497_sim](https://storage.cloud.google.com/ucf101_for_rar/video_data_497_sim.zip?authuser=1)(gs://ucf101_for_rar/video_data_497_sim.zip): A dataset of RGB frames extracted from 497 action videos and after simplified\
  	[rgb_475](https://storage.cloud.google.com/ucf101_for_rar/video_data_475.zip?authuser=1)(gs://ucf101_for_rar/video_data_475.zip): A dataset of RGB frames extracted from 475 action videos\
	[opt_475](https://storage.cloud.google.com/ucf101_for_rar/opt_475.zip?authuser=1)(gs://ucf101_for_rar/opt_475.zip): A dataset of TVL1 optical flow frames extracted from 475 action videos.\
	[rgb_575](https://storage.cloud.google.com/ucf101_for_rar/video_data_575.zip?authuser=1) (gs://ucf101_for_rar/video_data_575.zip)(optional): A dataset of RGB frames extracted from 475 action videos.\
	[opt_575](https://storage.cloud.google.com/ucf101_for_rar/opt_575.zip?authuser=1) (gs://ucf101_for_rar/opt_575.zip) (optional): A dataset of TVL1 optical flow frames extracted from 475 action videos.
 3. Download model and unzip:\
	[best_model](https://storage.cloud.google.com/ucf101_for_rar/model_best.zip?authuser=1) (gs://ucf101_for_rar/model_best.zip): The spatial stream model trained from rgb_497 respectively.\
  [whole project](https://storage.cloud.google.com/ucf101_for_rar/636project.zip?authuser=1) (gs://ucf101_for_rar/636project.zip): The whole project which contains code and models.
 4. Change every `path` in the python script.
 5. Run the `create_txt.py` and `save_pickle.py` before every start.

# Train and test model

 1. Spatial stream model
 	```
 	python spatial_cnn.py
 	```
 2. Motion stream model
	```
	python motion_cnn.py
	```

# Test model only
 1. Spatial stream model
 	```
 	python spatial_cnn.py --resume PATH_TO_PRETRAINED_MODEL --evaluate
 	```
 2. Motion stream model
	```
	python motion_cnn.py --resume PATH_TO_PRETRAINED_MODEL --evaluate
	```

# Test video
Download the [sample_video](https://storage.cloud.google.com/ucf101_for_rar/sample_video.zip?authuser=1) (gs://ucf101_for_rar/sample_video.zip)  and change the `file path` in `whole_test.py` and `whole_test2.py` to test model.
 1. Only use spatial stream model to test video
 	```
 	python whole_test.py
 	```
 
 2. Use two stream model to test video
 	```
 	python whole_test2.py
 	```


