# [DIBCO: Document Image Binarization Competition using BCDU-Net to achieve best performance](https://vc.ee.duth.gr/dibco2019/)

This GitHub page contains my implementation for DIBCO challenges in Document Image Binarization. The implemented code uses the BCDU-Net model for learning the binarization process on the DIBCO series. The evaluation results show the BCDU-net chan achieves the best performance on DIBCO challenges. If this code helps with your research please consider citing the following paper:
</br>
> [R. Azad](https://scholar.google.com/citations?hl=en&user=Qb5ildMAAAAJ&view_op=list_works&sortby=pubdate), et. all, "Bi-Directional ConvLSTM U-Net with Densely Connected Convolutions ", ICCV, 2019, download [link](http://openaccess.thecvf.com/content_ICCVW_2019/papers/VRMI/Azad_Bi-Directional_ConvLSTM_U-Net_with_Densley_Connected_Convolutions_ICCVW_2019_paper.pdf).

## Updates
- December 3, 2019: First release (Complete implementation for [DIBCO Series](https://vc.ee.duth.gr/dibco2019/), years 2009 to 2017 datasets added.). Other datasets can be added easily.

## Prerequisties and Run
This code has been implemented in python language using Keras library with TensorFlow backend and tested in ubuntu OS, though should be compatible with the related environment. following Environment and Library needed to run the code:

- Python 3
- Keras - tensorflow backend


## Run Demo
For training deep model for each DIBCO year, follow the bellow steps:

#### DIBCO Series
1- Download the DIBCO datasets from [this](https://drive.google.com/open?id=11hu7gZF641eETGHi0Yq8DCLPrJ-aekRh) link and extract it. We included DIBCO datasets from 2009 to 2017. It is easy to add DIBCO 2018, 2019 or other datasets, just need to revise the utils code. </br>
2- Run `Prepare_DIBCO.py` for data preparation and dividing data to train and test sets. Please note that this code will consider whole the samples of one particular year as a test set and the rest of the years for the training set. It is the common data division which uses in the DIBCO challenge. </br>
3- Run `Train_DIBCO.py` for training BCDU-Net model using trainng and validation (20% of the training samples) sets. The model will be training for 100 epochs and it will save the best weights for the validation set. </br>
4- For performance calculation and producing binarization result, run `Evaluate.py`. It will represent performance measures and will save related figures and results in `output` folder.</br>
#### Notice
We train the model using patches that we extract from the training set. Also for test image binarization, we apply patch-based overlaping binarization. If you want to train and evaluate the model of any particular year just determine the test year (parameter `Test_year = 2016`) when runing `Prepare_DIBCO.py` and `Evaluate.py`.</br>


## Quick Overview

### Structure of the Bidirection Convolutional LSTM that used in BCDU-Net network
![Diagram of the proposed method](https://github.com/rezazad68/LSTM-U-net/blob/master/output_images/convlstm.png)

## Results
For evaluating the performance of the BCDU-Net model on the DIBCO series, we followed the setting used in [`SAE`](https://www.sciencedirect.com/science/article/abs/pii/S0031320318303091). In [1] the authors provided the experimental results on only DIBCO series 2014 and 2016. To do so, they have considered the whole samples of one particular year (for example 2014 or 2016) as a test set and rest of the samples from other years as a train set. We used the same setting for reporting our results. In bellow, the results of the proposed approach illustrated in terms of F-measure.
</br>
 

Methods | DIBCO 2014 |DIBCO 2016
------------ | -------------|----|
[Otsu](https://ieeexplore.ieee.org/document/4310076)	 | 91.56	| 73.79
[Niblack](https://dl.acm.org/citation.cfm?id=4901)	 | 22.26	| 16.7
[Sauvola](https://www.sciencedirect.com/science/article/abs/pii/S0031320399000552)	 | 77.08	| 82.00
[Wolf et al.](https://ieeexplore.ieee.org/document/1048482)	 | 90.47	| 81.76
[Gatos et al.](https://www.sciencedirect.com/science/article/abs/pii/S0031320305003821)	 | 91.97	| 74.97
[Sauvola MS](https://link.springer.com/article/10.1007/s10032-013-0209-0)	 | 87.86	| 65.04
[Su et al.](https://ieeexplore.ieee.org/document/6373726)	 | 95.14	| 90.27
[Howe](https://link.springer.com/article/10.1007/s10032-012-0192-x)	 | 90.00	| 80.64
[Kliger and Tal](https://users.iit.demokritos.gr/~bgat/ICFHR_2016_DIBCO.pdf)	 | 95.00	| 90.48
[CNN](https://link.springer.com/chapter/10.1007/978-3-319-19222-2_10)	 | 81.23	| 54.58
[SAE](https://www.sciencedirect.com/science/article/abs/pii/S0031320318303091)	 | 89.12	| 85.27
[R. Azad BCDU-Net](https://github.com/rezazad68/LSTM-U-net/edit/master/README.md)	 | **97.88**	|**98.96**


#### Document Image Binarization Results on DIBCO Series

![Documnet Image Binarization result 1](https://github.com/rezazad68/BCDUnet_DIBCO/blob/master/images/1.png)
![Documnet Image Binarization result 2](https://github.com/rezazad68/BCDUnet_DIBCO/blob/master/images/2.png)
![Documnet Image Binarization result 3](https://github.com/rezazad68/BCDUnet_DIBCO/blob/master/images/3.png)
![Documnet Image Binarization result 4](https://github.com/rezazad68/BCDUnet_DIBCO/blob/master/images/4.png)


### Model weights
You can download the learned weights for DIBCO series, which trained on DIBCO 2009-2017 (except 2016) samples. Please note that the trained model can be used for other years too.

Test year |Learned weights
------------ | -------------
DIBCO 2016 | [Model Weights](https://drive.google.com/open?id=1aBjF7YLtI26wOm8Uj8XNk1WQsAx1Asuf)



### Query
All implementation done by Reza Azad. For any query please contact us for more information.

```python
rezazad68@gmail.com

```
