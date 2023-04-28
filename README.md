# ReadRepo_byChaGPT
A tutorial aims to guide the researcher who's not familiar with deep learning to read through th a deep learning repository by using ChatGPT.

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
Simply, paste all the code of ```scripts/amg.py``` into ChatGPT with :
```

```
