# 原计划书

People with face acne problem may have concerns about how they look. When deciding on a skin care product, they may want to know how their acne problem can be improved after they use those products. However, there exists no such techniques for simulating the changes of acne on facial skin of different skin tones. In this project, we propose to explore advanced computer vision or deep learning techniques to build a novel system which can simulate skin acne changes.

## Description of the Project:
In this project, the student should explore possible approaches to build a system for the skin acne simulation. This system should first the segment facial acne. On each segmented acne, and the simulation operation is conducted. Therefore, the student need to learn to apply image segmentation method to segment the acne. Then, the student may explore image processing or deep learning methods to implement the simulation operations. Moreover, as people have different skin tones, from fair to dark, the variety of skin tones may affect the segmentation and simulation models. Hence, the student need to explore generalization methods to improve the segmentation and simulation methods’ performance against the diversity of skin tones.

To achieve the above objectives, the student needs to conduct literature study about image segmentation, image warping, image translation, and so on. Then, the student needs to do programming to implement and improve the simulation and segmentation methods, and conduct experiments for analysis.

What you will learn & do:
1. Algorithm implementation: the student needs to implement some image/video processing and computer vision techniques, such as acne detection, image warpping, etc.
2. Data understanding: the student needs to understand the face image data to design acne simulation operations
3. The required knowledge and skill for this project can be summarized as follows: (a) MatLab; (b) Python & Pytorch; (c) OpenCV; (d) deep learning and computer vision

# 主题
## 现状
色斑的生理学特征，成因和主要性状（简略）：由于其复杂的机理，导致定义和建模的困难；现有的算法难以准确而自然地编辑色斑的外观。（提出问题和 gap）

## 提出的方法
皮肤光学性质模型，次表面散射原理；借用图形学中一些近似算法，对色斑的外观进行建模，实现色斑和基底皮肤的分离，从而进行有真实感的修改

一个新颖的，能较好估计皮肤色素的相对浓度的框架被提出。通过这个框架，色斑和皮肤能较好地分离。又提出一个参数化的色斑模型，实现色斑的空间的分布的稳健拟合。

## 工程实现
我们使用 python + opencv 编写了一个处理后端，能自动分析和拟合 ROI 中色斑的浓度