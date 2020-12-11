# TDI CAPSTONE PROJECT 

Automating Road maintenance using Google Street View Images to Detect Potholes

By Hommood Alrowais

## Project Description:
The City of Toronto is responsible for the operation and maintenance of 5600 kilometers of public roads, trails, and sidewalks. The City of Toronto's Transportation Services each summer sends 16 technical trainees to manually analyze the quality of sidewalks. This operation is done by foot, and notes are taken by pen and paper. This only covers a small area of the city each year. In addition, due to the current pandemic, there were fewer trainees due to hiring freezes. I proposed automating the process of data collection and analysis to allow the trainees to cover more area with fewer staff hours. These repairs are necessary as Toronto is obliged to be in compliance of the Accessibility for Ontarians with Disabilities Act (AODA) to allow fair, safe, and equitable access of the public realm to those with disabilities independently.

As a proof of concept of automated infrastructure maintenance, and an attempt at a minimum viable product, I shifted my automated data collection to the 40 kilometers of cycling tracks that were installed this past summer. Due to the rapid implementation of the project, the road quality is poor for cycling and is riddled with potholes. Since 2005, Google has collected images of the streets all across the globe, including Toronto. These Google Street View images can be analyzed using machine learning algorithms to detect potholes and allow the city to respond in a timely fashion.

The goal of this prototype to persuade the City Council to fund higher quality detection mechanisms and more frequent data collection. These detection mechanisms can include 3D spatial images using LIDAR cameras installed on bicycles. These can be used to properly train and properly label images of potholes for image detection and classification machine learning algorithms. Prior usefulness has been proven in Iowa's Department of Natural Resources Data bike [url]. The bikes used cameras and accelerometers to detect the quality of trails around Iowa. I believe that with higher quality LIDAR data we can achieve more fidelity in detection, and will need less human involvement in the loop. 

The project would collect Google Street View images from the desired neighborhood. The collected images would be analyzed using a pothole detection algorithm. The results would be analyzed and validated by comparing the results to a database of citizen-reported potholes in the same neighborhood. 

The project was developed in Python using Jupyter Notebooks and PyCharm IDE.

## Methodology and Tools Used
### Data Ingestion:
Image collection: Images were downloaded using Google Street View API. The image collected were 640x640 pixels. Care was taken to ensure proper alignment with street direction, camera angles, and depth of view. 

Validation Data: The location, reporting date, and status of potholes is collected using Open Data Toronto's API. The API had been suspended in March of 2020. I worked on a subset of data previously collected. 

Labeled data: Training, validation, and testing images were collected from the internet. Images were manually labeled using LabelImg tool. The annotation and image were converted into an XML document in the Pascal VOC format. The generated files were converted to CSV files. For TensorFlow-friendly ingestion, the files were converted TFrecord files. To augment the data, pre-labeled pothole images were used from Roboflow and downloaded in TFRecord format.

### Machine Learning Model:
In order to detect potholes in images, we will use transfer learning to attempt to achieve high-quality results with less training time. The model uses TensorFlow 2 and Keras as a framework. The chosen model from the Object Detection API model zoo was the SSD MobileNet V2. The model has fast inference time of ~20 ms.

The model's learning rate and batch size were optimized. The chosen parameters were a batch size of 1 and a learning rate of 0.00133. This allowed the model to run on the local computer. 

## Preliminary Results:
### Visualiztion:
After training, the generated Total graph is below. 

As we can see, the validation total loss is higher than the training total loss. Based on these results we can tell that the model is overfitting.

Here is the generated inference for a model vs. the expected output. 


### Conclusions:
Image collection and machine learning have been completed. 

Unfortunately, the mAP (mean Average Precision) was calculated for the detection box to be. 

This attempt at using Google Street View as a quick-and-dirty method for data collection proved to be unsuccessful. This motivates using more accurate ML models but most importantly using higher quality data collection methods using LIDAR cameras with better labeling techniques.
