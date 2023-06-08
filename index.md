# M$^3$IT: Multi-Modal Multilingual Instruction Tuning Dataset

📃[[Paper]](https://arxiv.org/abs/2306.04387)  💾[[Dataset]](https://huggingface.co/datasets/MMInstruction/M3IT) 🎇[[Demo(Coming Soon)]]()

## TL;DR

We introduce the Multi-Modal, Multilingual Instruction Tuning (M3IT) dataset,  comprises **40** carefully curated datasets, including **2.4 million** instances and **400** manually written task instructions, reformatted into a vision-to-text structure. 

Key tasks are translated into **80** languages with an advanced translation system

We train a VLM model on our M3IT dataset, showcasing its potential to answer complex questions, generalize to unseen video tasks, and comprehend unseen instructions in Chinese. 

## Task Coverage

Our dataset covers 40 diverse Vision-to-Text Task, featuring Chinese and Video tasks as well:

![Task Converage](/imgs/task_coverage.png)



## Dataset Instance

Our data instance looks like:

![Data Instance](/imgs/data_instance.png)

and you easily load the dataset and start training with your own model:

```python
from datasets import load_dataset
from io import BytesIO
from base64 import b64decode
from PIL import Image


ds_name = "viquae"  # change the dataset name here
dataset = load_dataset("MMInstruction/M3IT", "viquae")

for train_instance in dataset['train']:
    instruction = train_instance["instruction"]  # str
    inputs = train_instance["inputs"]  # str
    outputs = train_instance["outputs"]  # str
    image_base64_str_list = train_instance["image_base64_str"]  # str (base64)
    image_0 = Image.open(BytesIO(b64decode(image_base64_str_list[0])))
```



## Statistics

Statistics of our instructions:

![Instruction Statistics](/imgs/instruction_stat.png)



Statistics of our dataset grouped by task:

![Task Statistics](/imgs/task_stat.png)

## Model Evaluation

GPT-4 evalaution on $300$ instances from OK-VQA, A-OKVQA and ViQuAE.

![GPT-4 Evaluation](/imgs/gpt4_eval.png)

Our model outperforms MiniGPT4 and InstructBLIP in most cases!

![Case Study](/imgs/case_study.png)









