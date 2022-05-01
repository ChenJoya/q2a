# Question-to-Actions for AssistQ

This repo provides a baseline model for our proposed task: AssistQ: Affordance-centric Question-driven Task Completion for Egocentric Assistant. 

[[Page]](https://showlab.github.io/assistq/)  [[Paper]](https://arxiv.org/abs/2203.04203)   [[LOVEU@CVPR'22 Challenge]](https://sites.google.com/view/loveucvpr22/track-3?authuser=0)

Click to know the task:

[![Click to see the demo](https://img.youtube.com/vi/3v8ceel9Mos/0.jpg)](https://www.youtube.com/watch?v=3v8ceel9Mos)

Model Architecture (see paper for details):

![arch](https://user-images.githubusercontent.com/20626415/162197041-f1b06325-098c-448a-9b65-d746d8bfe08d.png)


## Install
(1) PyTorch. See https://pytorch.org/ for instruction. For example,
```
conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
```
(2) PyTorch Lightning. See https://www.pytorchlightning.ai/ for instruction. For example,
```
pip install pytorch-lightning
```

## Data

Download training set by filling in the [[AssistQ Downloading Agreement]](https://forms.gle/h9A8GxHksWJfPByf7).

The testing set will be released on May 01, 2022 (11:59PM Pacific Time).

## Encoding

See [encoder.md](https://github.com/showlab/Q2A/blob/master/encoder/README.md).

## Training & Evaluation

Select the config file and simply train, e.g.,

```
CUDA_VISIBLE_DEVICES=0 python train.py --cfg configs/loveu_q2a_traintest_fps1+maskx2_vit_b16+bert_b.yaml
```

The evaluation will be performed after each epoch. You can use Tensorboard, or just terminal outputs to record evaluation results.

## Performance

### LOVEU@CVPR2022 Challenge: 80 videos' QA samples for training, 20 videos' QA samples for testing

|  Model   | Recall@1 &#8593 | Recall@3 &#8593 | MR (Mean Rank) &#8595 | MRR (Mean Reciprocal Rank) &#8593 |
|  ----  |  ----  |  ----  |  ----  |  ----  |
| Q2A ([configs/loveu_q2a_traintest_fps1+maskx2_vit_b16+bert_b.yaml](configs/loveu_q2a_traintest_fps1+maskx2_vit_b16+bert_b.yaml)) | 21.8 | 62.3 | 3.6 | 2.7 |

### 8:2 QA samples splitting for training and validation/testing, respectively

(1) Validation: current step can use the ground-truth answers in previous steps

|  Model   | Recall@1 &#8593 | Recall@3 &#8593 | MR (Mean Rank) &#8595 | MRR (Mean Reciprocal Rank) &#8593 |
|  ----  |  ----  |  ----  |  ----  |  ----  |
| Q2A ([configs/assistq_q2a_trainval_fps1+maskx2_vit_b16+bert_b.yaml](configs/assistq_q2a_trainval_fps1+maskx2_vit_b16+bert_b.yaml)) | 29.0 | 55.9 | 3.6 | 3.1 |

(2) Testing: 

|  Model   | Recall@1 &#8593 | Recall@3 &#8593 | MR (Mean Rank) &#8595 | MRR (Mean Reciprocal Rank) &#8593 |
|  ----  |  ----  |  ----  |  ----  |  ----  |
| Q2A ([configs/assistq_q2a_traintest_fps1+maskx2_vit_b16+bert_b.yaml](configs/assistq_q2a_traintest_fps1+maskx2_vit_b16+bert_b.yaml)) | 28.7 | 55.5 | 3.7 | 3.1 |

## Contact

Feel free to contact us if you have any problems: joyachen97@gmail.com, or leave an issue in this repo.
