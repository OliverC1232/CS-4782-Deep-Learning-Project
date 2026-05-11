# CS-4782-Deep-Learning-Project

Project Team: Oliver Cheung, Kevin Biliguun, Vijay Krishnamoorthy, Alif Abdullah
Please see our final report (located in `/report`) for further detail.

### 1. Introduction
In this GitHub Repository, we present our implementation of the paper "Investigating the Limitations of Transformers with Simple Arithmetic Tasks". The main finding of this paper is how altering the surface representation of digits overcomes some of the limitations of Transformers and leads to significantly higher accuracy on arithmetic tasks.



### 2. Chosen Result
We chose to replicate the main result of the paper (see Figure 1 displayed below). 10-based and 10E-based representations performed the best, whilst the decimal representation had the worst accuracy. The legend in Figure 1 gives examples for what these representations look like.

<img width="1073" height="435" alt="image" src="https://github.com/user-attachments/assets/d7c692ab-5b20-48e7-8b90-9494834dd327" />


### 3. Github Contents


### 4. Re-implementation Details



### 5. Reproduction Steps


### 6. Results/Insights


### 7. Conclusion
Our re-implementation confirms the paper's findings about which representations have the best performance. 
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
