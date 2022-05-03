# Invoice_OCR_Detection
In is project I solve the problem of extracting data out of Images, this Project focus on Invoices Data Extracting which detects Invoice Images Data and Extracting records like Invoice Date and Items Description based on tesseract OCR Engine.

### Table of Contents:

#### 1- Importing Libraries
#### 2- Loading Invoices Images
#### 3- Method #1 Extracting data using Data Frames
#### 4- Method #2 Extracting Data through Image to Strings output
#### 5- String Output Preprocessing
#### 6- Printing Extracted Values



### Importing Libraries
```
from PIL import Image
import os
import pandas as pd
import numpy as np
import re,string,unicodedata
```
```
#Tesseract Library
import pytesseract
from pytesseract import Output

#Warnings
import warnings
warnings.filterwarnings("ignore")
```
```
#Garbage Collection
import gc

#Gensim Library for Text Processing
import gensim.parsing.preprocessing as gsp
from gensim import utils
```

#### Loading Invoices

![ex1](https://user-images.githubusercontent.com/24530726/166585913-7b0b6a6d-acf7-40bb-8eb3-16b86e08ee22.jpg)




#### Method #1 Extracting data using Data Frames


```
pytesseract.image_to_data("../input/invoice-ocr-data/invoice_2.jpg",output_type = Output.DATAFRAME)
```

#### Extracted Data

![pytessract_toDF](https://user-images.githubusercontent.com/24530726/166586644-76e03350-6643-4f22-bd75-8e9d0aba49ae.png)



#### Method #2 Extracting Data through Image to Strings output

```
pytesseract.image_to_string(Image.open(filepath), timeout=5)
```

#### String Output Preprocessing

```
# Create list of pre-processing func (gensim)
processes = [
               gsp.strip_tags, 
               gsp.strip_multiple_whitespaces,
               gsp.remove_stopwords, 
            ]
```

![preprocessing_output](https://user-images.githubusercontent.com/24530726/166587449-37481b53-18f4-4618-a1e6-156d815bff8f.png)


#### Extracted Data


![String_Output](https://user-images.githubusercontent.com/24530726/166588116-1ca9f699-ff61-4fa7-a6fb-080db5d53455.png)






