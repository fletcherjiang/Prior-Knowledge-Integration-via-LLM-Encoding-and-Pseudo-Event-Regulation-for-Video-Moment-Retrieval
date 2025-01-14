# Prior Knowledge Integration via LLM Encoding and Pseudo-Event Regulation for Video Moment Retrieval

[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/prior-knowledge-integration-via-llm-encoding/natural-language-moment-retrieval-on-tacos)](https://paperswithcode.com/sota/natural-language-moment-retrieval-on-tacos?p=prior-knowledge-integration-via-llm-encoding)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/prior-knowledge-integration-via-llm-encoding/highlight-detection-on-youtube-highlights)](https://paperswithcode.com/sota/highlight-detection-on-youtube-highlights?p=prior-knowledge-integration-via-llm-encoding)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/prior-knowledge-integration-via-llm-encoding/highlight-detection-on-qvhighlights)](https://paperswithcode.com/sota/highlight-detection-on-qvhighlights?p=prior-knowledge-integration-via-llm-encoding)


[Yiyang Jiang](https://yyjiang.com/), [Wengyu Zhang](https://wengyuzhang.com), [Xulu Zhang](https://scholar.google.com/citations?user=4UqJoGMAAAAJ), [Xiao-Yong Wei](https://www4.comp.polyu.edu.hk/~x1wei/), [Chang Wen Chen](https://web.comp.polyu.edu.hk/chencw/), and [Qing Li](https://www4.comp.polyu.edu.hk/~csqli/).
</div>

[![arXiv](https://badgen.net/badge/arXiv/2407.15051/red?cache=300)](https://arxiv.org/abs/2407.15051)
[![License](https://badgen.net/badge/License/BSD%203-Clause%20License?color=blue&cache=300)](https://github.com/fletcherjiang/LLMEPET/blob/main/LICENSE)


Official Pytorch Implementation of 'Prior Knowledge Integration via LLM Encoding and Pseudo-Event Regulation for Video Moment Retrieval'
<p align="center"><img width="850" src="images/model.png"></p>


[**Installation**](#installation) | [**Dataset**](#dataset) | [**Training**](#training) | [**Evaluation**](#evaluation) | [**Model Zoo**](#model)

## 📢 News
**[2024.7.21]** Our paper has been accepted by ACM Multimedia 2024 (Oral).

**[2024.7.10]** The code and dataset of related tasks has been released.

**[2024.5.10]** The repository is public.

**[2024.4.10]** The repository is created.



<a name="installation"></a>
## ⚙️ Installation
1. Clone the repository from GitHub.

```shell
git clone https://github.com/fletcherjiang/LLMEPET.git
cd LLMEPET
```

2. Create conda environment.

```shell
conda create -n LLMEPET python=3.8
conda activate LLMEPET
```

3. Download the packages
```shell
pip install -r requirements.txt
```
<a name="dataset"></a>

## 🗂️ Dataset
For all datasets, we provide extracted features, download them and place them into `features/`
- [QVHighlights](https://polyuit-my.sharepoint.com/:u:/g/personal/yiyajiang_polyu_edu_hk/EW28uy57KENIusLy8T_u5ZcB8Stq6sPhPv0zfbhorENrmA?e=K60DvU)
- [Charades-STA](https://polyuit-my.sharepoint.com/:u:/g/personal/yiyajiang_polyu_edu_hk/EaP3G8d6z4VGgZ4qHtjQ_tYBGI6t3-zQCHX48xTeUww9ig?e=L4z64w)
- [TACoS](https://polyuit-my.sharepoint.com/:u:/g/personal/yiyajiang_polyu_edu_hk/EfTC9kZXptlJqr0TxfbV10MBf3CDxT-mguIxiI7_1Tf4Pg?e=WDzwmp)
- [YouTube Highlights](https://polyuit-my.sharepoint.com/:u:/g/personal/yiyajiang_polyu_edu_hk/ERIChtcQPQREsJMCdOng8DcBMzL_uRtv-n822aC3FGgHFA?e=uoxVha)
- [TVSum](https://polyuit-my.sharepoint.com/:u:/g/personal/yiyajiang_polyu_edu_hk/EfEJugMe4jNOr6OjKYwRwskBpdP5Tu9XDu3-pL8jKS0MFQ?e=7w50ow)

### The prepared dataset should be in the following structure.
```
.
├── LLMEPET
│   ├── llm_epet
│   └── data
│   └── results
│   └── run_on_video
│   └── standalone_eval
│   └── utils
├── data
├── features
│   └── qvhighlight
│   └── charades
│   └── tacos
│   └── tvsum
│   └── youtube_uni
├── llama
│   └── consolidated.00.pth
│   └── tokenizer.model
│   └── params.json
├──README.md
└── ···
```
## 🪐 LLaMA Checkpoint
* You can download from [huggingface](https://huggingface.co/nyanko7/LLaMA-7B)
OR
* [LLaMA](https://polyuit-my.sharepoint.com/:f:/g/personal/yiyajiang_polyu_edu_hk/EmNCvzkVem1Ik5gntXQYJ8gB1dv6WusOjKpzZjWdTVIRMw?e=HsZDIh)


If you want to try LLaMA-2 or LLaMA-3, you could download the checkpoints from [LLaMA-2](https://huggingface.co/meta-llama/Llama-2-7b) or [LLaMA-3](https://huggingface.co/meta-llama/Meta-Llama-3-8B/tree/main/original). You should edit the (llm_epet/llama.py) by yourself.



<a name="training"></a>

## 🚀 Training

### QVHighlights Training
```
bash llm_epet/scripts/train.sh  
```


### Charades-STA
```
bash llm_epet/scripts/charades_sta/train.sh
```

### TACoS
```
bash llm_epet/scripts/tacos/train.sh  
```

### TVSum
```
bash llm_epet/scripts/tvsum/train_tvsum.sh  
```

### Youtube-hl
```
bash llm_epet/scripts/youtube_uni/train.sh  
```



<a name="evaluation"></a>

## ⭐ QVHighlights Evaluation and Submission
```
bash llm_epet/scripts/inference.sh results/{direc}/model_best.ckpt 'val'
bash llm_epet/scripts/inference.sh results/{direc}/model_best.ckpt 'test'
```
Pack the hl_{val,test}_submission.jsonl files and submit them to [CodaLab](https://codalab.lisn.upsaclay.fr/competitions/6937).

<a name="model"></a>

## 📦 Model Zoo
Dataset | Model file
 -- | -- 
QVHighlights (Slowfast + CLIP) | [checkpoints](https://polyuit-my.sharepoint.com/:f:/g/personal/yiyajiang_polyu_edu_hk/EgNbMi8eS1dCoRI7xo5Ivn0B0x0b8r0J2APzi8QkYjHfdw?e=ioqkQ5)
Charades (Slowfast + CLIP) | [checkpoints](https://polyuit-my.sharepoint.com/:f:/g/personal/yiyajiang_polyu_edu_hk/ElnP--2r1RNLqNjqQcUUUCsBRK2NN3CdMMBQae9yf_FrdQ?e=jZo1JO)
TACoS | [checkpoints](https://polyuit-my.sharepoint.com/:f:/g/personal/yiyajiang_polyu_edu_hk/EuxFRpahctJBv7NqdXCMPDYBF_jdCDPE7TnnA6z7xJzrkg?e=uo2zqr)
TVSum | [checkpoints](https://polyuit-my.sharepoint.com/:f:/g/personal/yiyajiang_polyu_edu_hk/ErIPP2K7r7RMmsj7gLbPMZoBv-IbPyiB2NwcvmYS3kYEfg?e=2asVNJ)
Youtube-HL | [checkpoints]()
 

## 📖 Citation
If you find the repository or the paper useful, please use the following entry for citation.
```
@inproceedings{
jiang2024prior,
title={Prior Knowledge Integration via {LLM} Encoding and Pseudo Event Regulation for Video Moment Retrieval},
author={Yiyang Jiang and Wengyu Zhang and Xulu Zhang and Xiaoyong Wei and Chang Wen Chen and Qing Li},
booktitle={ACM Multimedia 2024},
year={2024},
url={https://arxiv.org/abs/2407.15051}
}
```
