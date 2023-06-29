# Supplementary-Result
In response to the reviewer's comments, we devoted significant effort to supplementing our experimental results within a constrained timeframe.   Specifically, this involved integrating three widely adopted interpolation techniques and conducting a comparison of model running times.
## Comparative Counterparts
The imputation methods described in the paper are as follows:
- Mean imputation: replacing missing values with the mean of the samples.
- Median imputation: replacing missing values with the median of the samples.
- k-Nearest Neighbors (KNN) imputation: for each data sample, we use k nearest neighbors with Euclidean distance to find similar vectors across different timestamps and estimate missing values using the weighted average of its neighbors.
- MRNN: using a multi-directional recurrent neural network to insert missing values in the data stream and estimate them across the data stream.
- BRITS: this method uses a bidirectional LSTM with history regression and feature regression to estimate missing values.
- Transformer: using the Transformer’s encoder for missing value estimation.
- MTSIT: using learnable position encoding and the Transformer’s encoder for missing value estimation.
- SAITS: using two diagonal-masked multihead attention modules for joint reconstruction.

We have add three new interpolation methods, which are described below:
- Zero-value imputation: This method involves filling the missing positions with zero values.
- Last observation carried forward (LOCF) imputation: In each sample, missing positions are filled with the last observed value, and if no prior observation exists, they are filled with zero values.
- Linear imputation: Given a set of known data points, this method constructs a straight line to estimate the values of unknown data points.

## Comparative of Imputation Performance
The specific experimental results are presented as follows. The findings indicate that traditional methods, including zero-value imputation, LOCF imputation, mean imputation, median imputation, and KNN imputation, exhibited significant biases and performed poorly. Unexpectedly , it was discovered that linear imputation demonstrated a clear advantage for datasets with a low missing rate, such as Beijing PM2.5 and Air Quality, due to the slow and infrequent variation of data, which exhibited smoother and certain continuity between data points. But, the effectiveness of linear imputation rapidly deteriorated for datasets with a high missing rate or non-smooth.

MRNN and BRITS both performed well on the Beijing PM2.5 and Air Quality datasets due to their lower missing rates and smoother. Furthermore, the BRITS method, which considers historical and feature regression, outperformed MRNN on all datasets. These results demonstrate that RNN-based methods not only perform well on smooth datasets but also exhibit better robustness than traditional methods on more complex datasets.          Thanks to the attention mechanism's global information retrieval capability, Transformer, MTSIT, and SAITS demonstrated advantages for non-smooth human behavior coordinate data and PhysioNet2012.

Our proposed method is built upon the fusion of self-attention and GRU, which capitalizes on the strengths of both methods. By fully exploiting the long-term and short-term temporal dependencies and the correlations between features, the methods outperforms other methods on most datasets.
### Comparison of imputation performance on MAE
| Methods | PhysioNet2012 | BeiJing PM2.5 | Air Quality | Localization 10% |
| :-----------: | :-----------: | :-----------: | :-----------: | :-----------: |
| Zero | 0.7113±0.005 | 0.896±0.006 | 0.7083±0.002 | 0.827±0.007 | 
| Last | 0.4464±0.003 | 0.2265±0.003 | 0.2076±0.002 | 0.8516±0.001 | 
| Linear | 0.4223±0.009 | **0.1403±0.001** | 0.1386±0.002 | 1.2809±0.03 | 
| Mean | 0.4624±0.003 | 0.5217±0.003 | 0.3654±0.001 | 0.5990±0.007| 
| Median | 0.4493±0.003 |  0.5108±0.004|  0.3585±0.001|  0.5777±0.007| 
| KNN | 0.5142±0.002 |  0.4756±0.002|  0.3259±0.002|  0.5408±0.008| 
| MRNN | 0.5551±0.007 |  0.3295±0.005|  0.2914±0.002|  0.8104±0.007| 
| BRITS | 0.2654±0.028 |  0.1813±0.003|  0.1443±0.001|  0.3769±0.006| 
| Transformer | 0.2079±0.002|  0.2100±0.005|  0.1567±0.001|  0.1790±0.007| 
| MTSIT | 0.3814±0.005 |  0.2476±0.006 |  0.2119±0.002|  0.2608±0.004| 
| SAITS | 0.2061±0.002 |  0.1928±0.003 |  0.1409±0.003|  0.1814±0.009| 
| Ours | **0.2021±0.002** |  0.1783±0.003 |  **0.1227±0.001**|  **0.1628±0.008**| 

### Comparison of imputation performance on MRE
| Methods | PhysioNet2012 | BeiJing PM2.5 | Air Quality | Localization 10% |
| :-----------: | :-----------: | :-----------: | :-----------: | :-----------: |
| Zero | 1.000±0.000 | 1.000±0.000 | 1.000±0.000 | 1.000±0.000 | 
| Last | 0.6276±0.003 | 0.2528±0.004 | 0.2931±0.003 | 1.0298±0.009 | 
| Linear | 0.5937±0.011 | **0.1566±0.002** | 0.1956±0.002 | 1.5491±0.044 | 
| Mean |  0.6501±0.002 | 0.5822±0.005 | 0.5159±0.002 | 0.7243±0.008 |
| Median | 0.6317±0.002 | 0.5701±0.007 | 0.5061±0.002 | 0.6986±0.008 |
| KNN | 0.7229±0.003 | 0.5307±0.002 | 0.4601±0.003 | 0.6539±0.007 |
| MRNN | 0.7804±0.006 | 0.3678±0.005 | 0.4114±0.003 | 0.9800±0.003 |
| BRITS | 0.3730±0.037 | 0.2023±0.003 | 0.2038±0.001 | 0.4558±0.004 |
| Transformer | 0.2923±0.003 | 0.2344±0.005 | 0.2213±0.002 | 0.2164±0.008 |
| MTSIT | 0.5363±0.009 | 0.2764±0.007 | 0.2992±0.003 | 0.3154±0.003 |
| SAITS | 0.2898±0.002 | 0.2152±0.003 | 0.1989±0.004 | 0.2193±0.010 |
| Ours | **0.2842±0.003** | 0.1990±0.003 | **0.1733±0.002** | **0.1968±0.009** |

### Comparison of imputation performance on RMSE
| Methods | PhysioNet2012 | BeiJing PM2.5 | Air Quality | Localization 10% |
| :-----------: | :-----------: | :-----------: | :-----------: | :-----------: |
| Zero | 0.9854±0.007 | 1.2352±0.008 | 1.0273±0.036 | 1.0071±0.011 | 
| Last | 0.7917±0.021 | 0.4525±0.012 | 0.5373±0.069 | 1.1507±0.015 | 
| Linear | 1.3021±0.527 | **0.3042±0.019** | 0.4793±0.08 | 2.6193±0.113 | 
| Mean | 0.7714±0.070 | 0.7644±0.007 | 0.6668±0.054 | 0.7853±0.011 |
| Median | 0.7367±0.016 | 0.8390±0.007 | 0.6973±0.053 | 0.8270±0.011 |
| KNN | 0.7995±0.017 | 0.7252±0.008 | 0.6126±0.060 | 0.7245±0.013 |
| MRNN | 0.8148±0.011 | 0.5544±0.016 | 0.5368±0.061 | 1.0029±0.011 |
| BRITS | 4.2431±7.298 | 0.3243±0.013 | 0.3579±0.053 | 0.5631±0.010 |
| Transformer | 0.4891±0.048 | 0.3655±0.016 | 0.3772±0.064 | 0.3478±0.014 |
| MTSIT | 0.6815±0.016 | 0.4197±0.014 | 0.4841±0.067 | 0.4531±0.008 |
| SAITS | 0.4653±0.030 | 0.3371±0.013 | 0.3537±0.061 | 0.3601±0.011 |
| Ours | **0.4632±0.031** | 0.3112±0.015 | **0.3267±0.060** | **0.3329±0.016** |

## Comparison Experiment of Model Execution Time
We conducted a statistical analysis of the execution time on the test set of the PhysioNet dataset, which comprised 2398 samples. The execution time and the average time per sample is presented in the table below. As our proposed method integrates bidirectional GRU and multiple self-attention mechanisms, it features a deeper network structure and greater complexity. Therefore, compared to methods based solely on self-attention, our method requires more time for execution. However, it is faster than BRITS, which is based on bidirectional RNN. Regarding the performance of imputation, our proposed methods outperforms other methods on most datasets. In future research, we plan to further enhance the model's efficiency and effectiveness.
| Methods | Test Time Consumed ( s ) | Average Time per Sample ( ms ) |
| :-----------: | :-----------: | :-----------: |
| MRNN |	1.7110 |	0.714 |
| BRITS |	4.5710 |	1.906 |
| Transformer |	**1.0244** |	**0.427** |
| MTSIT |	2.4820 |	1.035 |
| SAITS |	1.2186 |	0.508 |
| Ours |	3.7422 |	1.561 |

