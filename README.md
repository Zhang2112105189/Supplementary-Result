# Supplementary-Result
Supplementary-Result
## Comparison of imputation performance on MAE
| Methods | PhysioNet2012 | BeiJing PM2.5 | Air Quality | Localization 10% |
| :-----------: | :-----------: | :-----------: | :-----------: | :-----------: |
| Zero | 0.7113±0.005 | 0.896±0.006 | 0.7083±0.002 | 0.827±0.007 | 
| Last | 0.4464±0.003 | 0.2265±0.003 | 0.2076±0.002 | 0.8516±0.001 | 
| Mean | 0.4624±0.003 | 0.5217±0.003 | 0.3654±0.001 | 0.5990±0.007| 
| Median | 0.4493±0.003 |  0.5108±0.004|  0.3585±0.001|  0.5777±0.007| 
| KNN | 0.5142±0.002 |  0.4756±0.002|  0.3259±0.002|  0.5408±0.008| 
| MRNN | 0.5551±0.007 |  0.3295±0.005|  0.2914±0.002|  0.8104±0.007| 
| BRITS | 0.2654±0.028 |  0.1813±0.003|  0.1443±0.001|  0.3769±0.006| 
| Transformer | 0.2079±0.002|  0.2100±0.005|  0.1567±0.001|  0.1790±0.007| 
| MTSIT | 0.3814±0.005 |  0.2476±0.006 |  0.2119±0.002|  0.2608±0.004| 
| SAITS | 0.2061±0.002 |  0.1928±0.003 |  0.1409±0.003|  0.1814±0.009| 
| Ours | **0.2021±0.002** |  **0.1783±0.003** |  **0.1227±0.001**|  **0.1628±0.008**| 

## Comparison of imputation performance on MRE
| Methods | PhysioNet2012 | BeiJing PM2.5 | Air Quality | Localization 10% |
| :-----------: | :-----------: | :-----------: | :-----------: | :-----------: |
| Zero | 1.000±0.000 | 1.000±0.000 | 1.000±0.000 | 1.000±0.000 | 
| Last | 0.6276±0.003 | 0.2528±0.004 | 0.2931±0.003 | 1.0298±0.009 | 
| Mean |  0.6501±0.002 | 0.5822±0.005 | 0.5159±0.002 | 0.7243±0.008 |
| Median | 0.6317±0.002 | 0.5701±0.007 | 0.5061±0.002 | 0.6986±0.008 |
| KNN | 0.7229±0.003 | 0.5307±0.002 | 0.4601±0.003 | 0.6539±0.007 |
| MRNN | 0.7804±0.006 | 0.3678±0.005 | 0.4114±0.003 | 0.9800±0.003 |
| BRITS | 0.3730±0.037 | 0.2023±0.003 | 0.2038±0.001 | 0.4558±0.004 |
| Transformer | 0.2923±0.003 | 0.2344±0.005 | 0.2213±0.002 | 0.2164±0.008 |
| MTSIT | 0.5363±0.009 | 0.2764±0.007 | 0.2992±0.003 | 0.3154±0.003 |
| SAITS | 0.2898±0.002 | 0.2152±0.003 | 0.1989±0.004 | 0.2193±0.010 |
| Ours | **0.2842±0.003** | **0.1990±0.003** | **0.1733±0.002** | **0.1968±0.009** |

## Comparison of imputation performance on RMSE
| Methods | PhysioNet2012 | BeiJing PM2.5 | Air Quality | Localization 10% |
| :-----------: | :-----------: | :-----------: | :-----------: | :-----------: |
| Zero | 0.9854±0.007 | 1.2352±0.008 | 1.0273±0.036 | 1.0071±0.011 | 
| Last | 0.7917±0.021 | 0.4525±0.012 | 0.5373±0.069 | 1.1507±0.015 | 
| Mean | 0.7714±0.070 | 0.7644±0.007 | 0.6668±0.054 | 0.7853±0.011 |
| Median | 0.7367±0.016 | 0.8390±0.007 | 0.6973±0.053 | 0.8270±0.011 |
| KNN | 0.7995±0.017 | 0.7252±0.008 | 0.6126±0.060 | 0.7245±0.013 |
| MRNN | 0.8148±0.011 | 0.5544±0.016 | 0.5368±0.061 | 1.0029±0.011 |
| BRITS | 4.2431±7.298 | 0.3243±0.013 | 0.3579±0.053 | 0.5631±0.010 |
| Transformer | 0.4891±0.048 | 0.3655±0.016 | 0.3772±0.064 | 0.3478±0.014 |
| MTSIT | 0.6815±0.016 | 0.4197±0.014 | 0.4841±0.067 | 0.4531±0.008 |
| SAITS | 0.4653±0.030 | 0.3371±0.013 | 0.3537±0.061 | 0.3601±0.011 |
| Ours | **0.4632±0.031** | **0.3112±0.015** | **0.3267±0.060** | **0.3329±0.016** |
