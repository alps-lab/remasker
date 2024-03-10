# ReMasker

This is the implementation for the ICLR'24 paper: [ReMasker: Imputing Tabular Data with Masked Autoencoding](https://openreview.net/forum?id=KI9NqjLVDT)


## Installation
1. Require environment of `python>=3.9`

2. pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu116

3. pip install timm

4. pip install hyperimpute

## Configuration
Modify the corresponding configuration in the config file or command-line arguments.

Example:
> Path of datasets: `--path` (`./`)

## Basic Command
You can run this basic command to get the imputation results of ReMasker on iris dataset:

`python plugin_mae.py --dataset iris`

## Toy Example Usage
```python
import numpy as np
import pandas as pd
from utils import get_args_parser
from remasker_impute import ReMasker

X_raw = np.arange(50).reshape(10, 5) * 1.0
X = pd.DataFrame(X_raw, columns=['0', '1', '2', '3', '4'])
X.iat[3,0] = np.nan

imputer = ReMasker()

imputed = imputer.fit_transform(X)
print(imputed[3,0])
```

## Citation

If you use the code, please cite our paper: 

```
@inproceedings{
    du2024remasker,
    title={ReMasker: Imputing Tabular Data with Masked Autoencoding},
    author={Tianyu Du and Luca Melis and Ting Wang},
    booktitle={The Twelfth International Conference on Learning Representations},
    year={2024},
    url={https://openreview.net/forum?id=KI9NqjLVDT}
}
```