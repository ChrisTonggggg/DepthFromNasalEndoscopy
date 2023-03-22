# DepthFromNasalEndoscopy

This package contains 1)training datasets and 2)testing datasets of the method described in the following work:
	

	title = {Real-to-Virtual Domain Transfer-based Depth Estimation for Real-time 3D Annotation 
	in Transnasal Surgery: A Study of Annotation Accuracy and Stability (https://doi.org/10.1007/s11548-021-02346-9)},

	author = {Hon-Sing Tong · Yui-Lun Ng ·Zhiyu Liu · Justin D. L. Ho ·
	Po-Ling Chan · Jason Y. K. Chan · Ka-Wai Kwok}

	keywords = {Augmented Reality · Surgical Annotation · 
	Monocular Depth Estimation · Domain Transfer Learning · Transnasal Surgery}


This dataset is prepared for our IPCAI2021 submission with the abovementioned title. 
The data is NOT a final version and may be updated.
Please find the information of the current version of this package below.
________________________________________________________________________________________________________
1.1) Training datasets for depth estimation 
     [DepthFromNasalEndoscopy/Training/DepthTraining_1]

- Two datasets [dataset_1;dataset_2] with corresponding depth labels are included.
- [dataset_1/capture_RGB] consists of ~3,600 frames (size = 1718x1080) of synthetic endoscopic images.
- [dataset_1/real_train] consists of ~3,600 frames (size = 1718x1080) of depth maps that are correspondents of frames in [dataset_1/capture_RGB].
- [dataset_2/capture_RGB] consists of ~18,000 (size = 640x480) frames of synthetic endoscopic images.
- [dataset_2/capture_depth] consists of ~18,000 (size = 640x480) frames of depth maps that are correspondents of frames in [dataset_2/capture_RGB].

- [dataset_1;dataset_2] can be used for training a supervised depth estimation network.
- The depth estimation network we used was DepthDepth [1]. Though these data are also applicable to other methods. 
- All images were generated in Unity3D with a virtual camera. 
- Images were taken while the camera was being moved along a manually defined track inside a nasal airway model. 
- Depth at each pixel was stored as a normalized float number in the range [0,1], which corresponds to [0,25] mm.

[1] Alhashim, I. and P. Wonka, High quality monocular depth estimation via transfer learning. arXiv preprint arXiv:1812.11941, 2018.

________________________________________________________________________________________________________
1.2) Training datasets for style transfer 
     [DepthFromNasalEndoscopy/Training/StyleTransferTraining_1]

- Two datasets [dataset_1;dataset_2] containing source domain(real) and target domain(virtual) are provided.
- [dataset_1/capture_RGB] consists of ~3,600 frames (size = 1718x1080) that depict the target domain(virtual).
- [dataset_1/real_train] consists of ~3,000 frames (size = 1718x1080) that depict the source domain(real).
- [dataset_2/capture_RGB] consists of ~18,000 (size = 640x480) that depict the target domain(virtual).
- [dataset_2/real_train] consists of ~4,300 (size = 1718x1080) that depict the source domain(real).

- [dataset_1;dataset_2] can be used for training a domain adaptation network.
- The network we used was cycleGAN [2]. Though these data are also applicable to other similar methods. 
- Virtual images were generated in Unity3D with a virtual camera. 
- Images were taken while the camera was being moved along a manually defined track inside a nasal airway model. 
- Real images were captured using an Olympus rhinolaryngoscope (ENF-VH) inside a nasal airway phantom.
- Images of the two domains in a dataset are not paired correspondents as cycleGAN is an unsupervised method.

[2] Zhu, J.-Y., et al. Unpaired image-to-image translation using cycle-consistent adversarial networks. in Proceedings of the IEEE international conference on computer vision. 2017.
________________________________________________________________________________________________________
2) Testing datasets 
   [DepthFromNasalEndoscopy/Testing]

- This dataset contains real endoscopic images taken inside a nasal airway phantom and the corresponding ground truth depth.
- [real_forTest] consists of ~2,400 frames (size = 288x256) of real endoscopic images.
- [GT_forTest] consists of ~2,400 frames (size = 1718x1080) of ground truth depth maps that are correspondents of frames in [real_forTest].

- Size of images in [real_forTest] were resized to 288x256 so as to match the input size of cycleGAN.
- Images in [real_forTest] can be processed by i) a trained domain adaptation network, and then ii) a trained supervised depth estimation network to give depth prediction.
- Predicted depth maps can then be compared with [GT_forTest] for evaluating prediction accuracy. 
________________________________________________________________________________________________________


Should you have any question, please feel free to contact me at u3527192@connect.hku.hk
Repository created by Hon-Sing Tong
Date created: 18/01/2021

