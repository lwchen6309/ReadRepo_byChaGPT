# ReadRepo_byChaGPT
A tutorial aims to guide the researcher who's not familiar with deep learning to read through th a deep learning repository by using ChatGPT, especially to traverse the core function of repo to align with the scientific paper accordingly.

We start from [Segment Anything](https://github.com/facebookresearch/segment-anything) SAM repo.

![repo_tutor](https://user-images.githubusercontent.com/42672685/235139891-3e697565-bf5f-4464-909a-d18cfbf12378.jpg)

The general structure of girhub repo is below:
- `setup.py` indicates that this repo can installed by command 
```pip install -e .```
- `scripts` consists of the demo script of the repo.
- `segment_anything` (sometimes also named as `src`) contains the core code of the repo.

Let's start from the demo script, which is scripts/amg.py as indicated in SAM repo: 
```
python scripts/amg.py --checkpoint <path/to/checkpoint> --model-type <model_type> --input <image_or_folder> --output <path/to/output>
```

Simply, paste all the code of `scripts/amg.py` into ChatGPT with :

```
Please explain the code structure:
{paste the code of amg.py here}
```
Recieving the results from GPT:
```
...
The script imports the following modules:

- cv2 (OpenCV) for image processing and manipulation.
- segment_anything which contains the SamAutomaticMaskGenerator class and the sam_model_registry for model loading and mask generation.
- argparse for command-line argument parsing.
- json for writing COCO-style RLE masks to a JSON file.
- os for creating directories, joining paths, and checking if paths exist.
- typing for type annotations.
- The script defines a function write_masks_to_folder() that takes a list of masks and writes them as PNG images to a specified directory. The function also generates metadata for each mask and writes it to a CSV file in the same directory.

Another function get_amg_kwargs() takes the parsed command-line arguments and returns a dictionary of arguments for the SamAutomaticMaskGenerator class.
...
```
As indicated, `SamAutomaticMaskGenerator` is the core function implement SAM to be traversed. 
We now check the top of `scripts/amg.py` to traverse where its imported.
```
import cv2  # type: ignore

from segment_anything import SamAutomaticMaskGenerator, sam_model_registry
...
```
and find that it's imported from segment_anything, which is a dir and a module defined by the `__init__.py` under `segment_anything`, whose code is shown below. 
```
# Copyright (c) Meta Platforms, Inc. and affiliates.
# All rights reserved.

# This source code is licensed under the license found in the
# LICENSE file in the root directory of this source tree.

from .build_sam import (
    build_sam,
    build_sam_vit_h,
    build_sam_vit_l,
    build_sam_vit_b,
    sam_model_registry,
)
from .predictor import SamPredictor
from .automatic_mask_generator import SamAutomaticMaskGenerator
```
Now, we can see from this line 
```
from .automatic_mask_generator import SamAutomaticMaskGenerator
```
that the SAM is implemented at `automatic_mask_generator.py` under `segment_anything`. Namely, `segment_anything/automatic_mask_generator.py`

