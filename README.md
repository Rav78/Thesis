# DoRA: Domain-Based Self-Supervised Learning Framework for Low-Resource Real Estate Appraisal (CIKM 2023)
Official code of the paper **DoRA: Domain-Based Self-Supervised Learning Framework for Low-Resource Real Estate Appraisal**. Paper link: http://arxiv.org/abs/2309.00855.

## Overview
DoRA is pre-trained with an intra-sample geographic prediction as the pretext task based on the metadata of the real estate for equipping the real estate representations with prior domain knowledge. And, inter-sample contrastive learning is employed to generalize the representations to be robust for limited transactions of downstream tasks.

## Model Framework
<img src="./img/model_framework.jpg" width="500">

## Model Training
```
python DoRA.py {building_type} {num_shot}
```
{building_type} = ```'building', 'apartment', 'house'``` <br>
{num_shot} = ```1, 5, ...```

## Details of the Features
### Real Estate Features
|               Feature                | Feature Type (#class) |                                         Example                                          |
|:------------------------------------:|:---------------------:|:----------------------------------------------------------------------------------------:|
|              City Name               |     Category (21)     |                                       Taipei city                                        |
|              Town Name               |    Category (350)     |                                     Ren’ai township                                      |
|             Parking spot             |     Category (2)      |                    True/False (If the house includes a parking spot.)                    |
|                Studio                |        Binary         |         True/False (If the area of the estate is smaller than 8 square meters.)          |
|        Details building type         |     Category (5)      |        Residential building (11 floors and above), Mansion (10 floors and below)         |
|             Main Purpose             |    Category (1622)    |                            Electromechanical equipment space                             |
|          Building materials          |    Category (220)     |                                       Rebar, Wood                                        |
|       Management organization        |        Binary         |                                        True/False                                        |
|        Type of parking space         |     Category (3)      |                        Flat parking spot, Automated parking spot                         |
|               Elevator               |        Binary         |                                        True/False                                        |
|          First-floor index           |        Binary         |                 True/False (If the house is located on the first floor.)                 |
|              Shop index              |        Binary         |                        True/False (If the house is for shop use.)                        |
|             Housing type             |     Category (3)      |                                Building, Apartment, House                                |
|             Village name             |    Category (4650)    |                                    Zhongshan village                                     |
|               Land use               |     Category (19)     |                       Residential zone, Forestry land, Mining land                       |
|         Land Use Designation         |     Category (16)     |                       Type A building land, Class B building site                        |
|          Land transfer area          |       Numerical       |                                            30                                            |
|        Building transfer area        |       Numerical       |                                            50                                            |
|          Number of bedrooms          |       Numerical       |                                            2                                             |
|        Number of living rooms        |       Numerical       |                                            1                                             |
|          Number of bathroom          |       Numerical       |                                            3                                             |
|        Number of total rooms         |       Numerical       |                                            5                                             |
|             Parking area             |       Numerical       |                                            5                                             |
|          Main building area          |       Numerical       |                                           100                                            |
|       Ancillary building area        |       Numerical       |                                            10                                            |
|             Balcony area             |       Numerical       |                                            5                                             |
|              House age               |       Numerical       |                                         10 years                                         |
|      Number of land transaction      |       Numerical       |                                            1                                             |
|    Number of building transaction    |       Numerical       |                                            1                                             |
| Number of parking space transactions |       Numerical       |                                            2                                             |
|  Building area without parking area  |       Numerical       |                                            45                                            |
|          Single floor area           |       Numerical       |                                            20                                            |
|        Floor area ratio (FAR)        |       Numerical       | 10 (Derived by dividing the total area of the building by the total area of the parcel.) |
|             Estate floor             |       Numerical       |                                            5                                             |
|             Total floor              |       Numerical       |                                            10                                            |
|               Latitude               |       Numerical       |           Horizontal lines that measure distance north or south of the equator           |
|              Longitude               |       Numerical       |     Vertical lines that measure east or west of the meridian in Greenwich, England.      |
|       Building coverage ratio        |       Numerical       |                                            9                                             |
|           Park count flat            |       Numerical       |                                            0                                             |

### PoI Features
Generally, real estate with many YIMBY facilities often has a higher price since it implies the quality of living and the degree of transportation convenience. On the contrary, real estate with many NIMBY facilities may be likely to have a lower price since it indicates there may be some pollutant issues that cause a negative impact on living 
|   Feature   | Feature Type (#class) | Example |
|:-----------:|:---------------------:|:-------:|
|  YIMBY_10   |       Numerical       |    2    |
|  YIMBY_50   |       Numerical       |    3    |
|  YIMBY_100  |       Numerical       |    3    |
|  YIMBY_250  |       Numerical       |    6    |
|  YIMBY_500  |       Numerical       |    7    |
| YIMBY_1000  |       Numerical       |   13    |
| YIMBY_5000  |       Numerical       |   28    |
| YIMBY_10000 |       Numerical       |   52    |
|  NIMBY_10   |       Numerical       |    0    |
|  NIMBY_50   |       Numerical       |    0    |
|  NIMBY_100  |       Numerical       |    0    |
|  NIMBY_250  |       Numerical       |    1    |
|  NIMBY_500  |       Numerical       |    1    |
| NIMBY_1000  |       Numerical       |    2    |
| NIMBY_5000  |       Numerical       |    3    |
| NIMBY_10000 |       Numerical       |    6    |

### Economic and Geographical Features
|               Feature                | Feature Type (#class) |            Example             |
|:------------------------------------:|:---------------------:|:------------------------------:|
|          Land area per town          |       Numerical       |     23.13 (km<sup>2</sup>)     |
|     Population density per town      |       Numerical       | 23835 (#people/km<sup>2</sup>) |
|    House price index per quarter     |       Numerical       |              110               |
|    Unemployment rate per quarter     |       Numerical       |               5%               |
|   Economic growth rate per quarter   |       Numerical       |               3%               |
|       Lending rate per quarter       |       Numerical       |              1.9%              |
|  Land transaction count per quarter  |       Numerical       |             163796             |
| Average land price index per quarter |       Numerical       |              101               |
|    Steel price index per quarter     |       Numerical       |              1071              |
