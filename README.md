# CS 4782 Deep Learning Project
### Based on the paper: Investigating the Limitations of Transformers with Simple Arithmetic Tasks
### Project Team: Oliver Cheung, Kevin Biliguun, Vijay Krishnamoorthy, Alif Abdullah  
Please see our final report (located in `/report`) for further detail.

### 1. Introduction
In this GitHub Repository, we present our implementation of the paper "Investigating the Limitations of Transformers with Simple Arithmetic Tasks". The main finding of this paper is how altering the surface representation of digits overcomes some of the limitations of Transformers and leads to significantly higher accuracy on arithmetic tasks.


### 2. Chosen Result
We chose to replicate the main result of the paper (see Figure 1 displayed below). 10-based and 10E-based representations performed the best, whilst the decimal representation had the worst accuracy. The legend in Figure 1 gives examples for what these representations look like.

<img width="1073" height="435" alt="image" src="https://github.com/user-attachments/assets/d7c692ab-5b20-48e7-8b90-9494834dd327" />


### 3. Github Contents
1. [Instructions for dataset generation](https://github.com/OliverC1232/CS-4782-Deep-Learning-Project/blob/main/data/README.md#data)
2. [The datasets we generated and used for the project (as csv files)](https://github.com/OliverC1232/CS-4782-Deep-Learning-Project/tree/main/data)
3. [Our code for re-implementation](https://github.com/OliverC1232/CS-4782-Deep-Learning-Project/blob/main/code/CS4782FinalProject.ipynb)
4. [Our results for both the main chosen results and extensions](https://github.com/OliverC1232/CS-4782-Deep-Learning-Project/tree/main/results)
5. [Final Report](https://github.com/OliverC1232/CS-4782-Deep-Learning-Project/blob/main/report/Investigating_Limitations_of_Transformers_with_Simple_Arithmetic_Tasks_2page_report.pdf)
6. [Copy of the poster we presented in class](https://github.com/OliverC1232/CS-4782-Deep-Learning-Project/blob/main/poster/CS4782%20Poster%20-%20Final%20Version.pdf)


### 4. Re-implementation Details
First, we generate our own datasets consisting of 22,000 arithmetic tasks. We then fine-tune on a pretrained T5-base model (220 million parameters). We train on 20 epochs - this is lower than suggested in the paper due to Google Colab's compute usage limitations. We evaluate the representations on the accuracy achieved on the unseen test dataset (e.g. 0.8 means the model got 80% of the arithmetic tasks in the test set correct).


### 5. Reproduction Steps
Our repo can be easily implemented by running the `.ipynb` Python notebook found in the `/code` folder. You can either use the datasets we provide or generate your own dataset of arithmetic tasks. Information for dataset generation, including parameter choice, can be found in the [data README](https://github.com/OliverC1232/CS-4782-Deep-Learning-Project/blob/main/data/README.md).
Best results are obtained by running on Google Colab with the A100 GPU - be sure to mount your Google Drive (using the code provided) to store the dataset that the notebook generates. Our code will install/import the following libraries: `os`, `numpy`, `random`, `num2words`, `pandas`, `datasets`, `transformers`, `re`, `torch`, `tqdm`, `csv`.

### 6. Main Results & Insights
Our results for the addition task (Figure 2) show similar trents to the paper's findings. 10-based and 10E-based representations were most robust, consistently achieving around 80% accuracy across all 3 digit lengths we tested on. Decimal was the worst-performing representation by far, and drops off to around 0.02 accuracy for 15 digits. Underscore and Words performed well for 5 and 10 digits but accuracy declined sharply at 15 digits - this is also similar to the paper's results. 

<img width="809" height="592" alt="image" src="https://github.com/user-attachments/assets/2069e76d-8bc3-4ced-9720-c645091c92e6" />  


<br/>
      
The paper did not provide detailed results for the subtraction task, so we implemented this and provide results below (Figure 3). Again, results are comparable to both our implementation of the addition task and the original results from the paper.

<img width="753" height="556" alt="image" src="https://github.com/user-attachments/assets/65a3d950-5568-46cb-8401-d5e9850a2ae1" />



### 7. Conclusion & Extensions
Our re-implementation confirms the paper's findings that 10E-based and 10-based representations are superior, achieving much higher accuracy than decimal (which has near-zero accuracy for larger numbers of digits).  
We also explored extensions that weren't covered in the main section of the paper. We tested multiplication, but achieved lower accuracy, which suggests that the paper's methods do not generalize well to more complex operations. We found that extrapolation was possible, but high accuracy was achieved only with the 10E-Based representation. Finally, we combined features of multiple representations, and found this to achieve similar levels of accuracy to the representations mentioned in the paper.

### 8. References

Original Paper: “Investigating the Limitations of Transformers with Simple Arithmetic Tasks” Rodrigo Nogueira, Zhiying Jiang & Jimmy Lin 
April 12, 2021 
https://arxiv.org/pdf/2102.13019

T5 Model: ‘Exploring the limits of transfer learning with a unified text-to-text transformer’ 
Colin Raffel, Noam Shazeer, Adam Roberts, Katherine Lee, Sharan Narang, Michael Matena, Yanqi Zhou, Wei Li, Peter J. Liu 
Journal of Machine Learning Research, 2020
https://arxiv.org/pdf/1910.10683

### 9. Acknowledgements
This repository was submitted for a course at Cornell University, namely CS4782 - Deep Learning, taught by Professors Kilian Weinberger and Wei-Chiu Ma. We thank them and the TAs for their teaching and guidance through the Spring '26 semester. The poster was presented to and graded by course staff and fellow students.
