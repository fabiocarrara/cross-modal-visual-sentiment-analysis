# The Emotions of the Crowd: Learning Image Sentiment from Tweets via Cross-modal Distillation
[![arXiv](https://img.shields.io/badge/arXiv-2304.14942-b31b1b.svg)](https://arxiv.org/abs/2304.14942)

![Method Overview](https://fabiocarrara.github.io/cross-modal-visual-sentiment-analysis/static/images/overview.png)

## Introduction
This work introduced a cross-modal learning method to train visual models for **Sentiment Analysis in the Twitter domain**.

It was used to fine-tune the Vision-Transformer (ViT) model pre-trained on Imagenet-21k, which was able to achieve incredible results on external benchmarks which were manually annotated, even ***beating the current State Of The Art!***

We crawled ∼3.7 pictures from social media from 1 April to 30 June to use them in our **cross-modal** approach. In particular, a cross-modal teacher-student learning technique was used to avoid human annotators, thus minimizing the efforts required and allowing for the creation of vast training sets.

The latter can help future research to train robust visual models, as the number of parameters of current SOTA is **exponentially growing along with their need of data** to avoid overfitting problems.

## Build Instructions
### Clone codebase
    $ git config --global http.postBuffer 1048576000
    $ git clone --recursive https://github.com/fabiocarrara/cross-modal-visual-sentiment-analysis/tree/master
### Install dependencies 
    $ chmod +x install_dependencies.sh
    $ ./install_dependencies.sh

## How to use the scripts for benchmark evaluation
### Test a model with a benchmark, get the accuracy and save the prediction
    $ python3 scripts/test_benchmark.py -m <model_name> -b <benchmark_name>
    
    $ options for <model_name>: [boosted_model, ViT_L16, ViT_L32, ViT_B16, ViT_B32, merged_T4SA, bal_flat_T4SA2.0, bal_T4SA2.0, unb_T4SA2.0, B-T4SA_1.0_upd_filt, B-T4SA_1.0_upd, B-T4SA_1.0]
    $ options for <benchmark_name>: [5agree, 4agree, 3agree, FI_complete, emotion_ROI_test, twitter_testing_2] 

### Execute a five fold cross validation on a benchmark, get the mean accuracy, the standard deviation and save the predictions (by default use the boosted_model)
    $ python3 scripts/5_fold_cross.py -b <benchmark_name>

### Fine tune FI on the five split, get the mean accuracy, the standard deviation and save the predictions (by default use the boosted_model)
    $ python3 scripts/fine_tune_FI.py
    
## Trained Models

<table style="text-align: center;">
  <tr>
    <th colspan="2"></th>
    <th colspan="3">Confidence Filter Threshold</th>
    <th colspan="1"></th>
    <th colspan="3">Accuracy on Twitter Dataset (TD)</th>
  </tr>
  <tr>
    <th>Label</th>
    <th>Dataset</th>
    <th>Pos</th>
    <th>Neu</th>
    <th>Neg</th>
    <th>Student Arch</th>
    <th>5 agree</th>
    <th>$\ge$ 4 agree</th>
    <th>$\ge$ 3 agree</th>
  </tr>
  <tr>
    <td><a href="https://github.com/fabiocarrara/cross-modal-visual-sentiment-analysis/releases/download/v0.1.0/B-T4SA_1.0_upd.h5">Model 3.1</a></td>
    <td>A</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>B/32</td>
    <td>82.2</td>
    <td>78.0</td>
    <td>75.5</td>
  </tr>
  <tr>
    <td><a href="https://github.com/fabiocarrara/cross-modal-visual-sentiment-analysis/releases/download/v0.1.0/B-T4SA_1.0_upd_filt.h5">Model 3.2</a></td>
    <td>A</td>
    <td>0.70</td>
    <td>0.70</td>
    <td>0.70</td>
    <td>B/32</td>
    <td>84.7</td>
    <td>79.7</td>
    <td>76.6</td>
  </tr>
  <tr>
    <td><a href="https://github.com/fabiocarrara/cross-modal-visual-sentiment-analysis/releases/download/v0.1.0/bal_flat_T4SA2.0.h5">Model 3.3</a></td>
    <td>B</td>
    <td>0.70</td>
    <td>0.70</td>
    <td>0.70</td>
    <td>B/32</td>
    <td>82.3</td>
    <td>78.7</td>
    <td>75.3</td>
  </tr>
  <tr>
    <td><a href="https://github.com/fabiocarrara/cross-modal-visual-sentiment-analysis/releases/download/v0.1.0/bal_T4SA2.0.h5">Model 3.4</a></td>
    <td>B</td>
    <td>0.90</td>
    <td>0.90</td>
    <td>0.70</td>
    <td>B/32</td>
    <td>84.4</td>
    <td>80.3</td>
    <td>77.1</td>
  </tr>
  <tr>
    <td><a href="https://github.com/fabiocarrara/cross-modal-visual-sentiment-analysis/releases/download/v0.1.0/ViT_B32.h5">Model 3.5</a></td>
    <td>A+B</td>
    <td>0.90</td>
    <td>0.90</td>
    <td>0.70</td>
    <td>B/32</td>
    <td>86.5</td>
    <td>82.6</td>
    <td>78.9</td>
  </tr>
  <tr>
    <td><a href="https://github.com/fabiocarrara/cross-modal-visual-sentiment-analysis/releases/download/v0.1.0/ViT_L32.h5">Model 3.6</a></td>
    <td>A+B</td>
    <td>0.90</td>
    <td>0.90</td>
    <td>0.70</td>
    <td>L/32</td>
    <td>85.0</td>
    <td>82.4</td>
    <td>79.4</td>
  </tr>
  <tr>
    <td><a href="https://github.com/fabiocarrara/cross-modal-visual-sentiment-analysis/releases/download/v0.1.0/ViT_B16.h5">Model 3.7</a></td>
    <td>A+B</td>
    <td>0.90</td>
    <td>0.90</td>
    <td>0.70</td>
    <td>B/16</td>
    <td>87.0</td>
    <td>83.1</td>
    <td>79.4</td>
  </tr>
  <tr>
    <td><a href="https://github.com/fabiocarrara/cross-modal-visual-sentiment-analysis/releases/download/v0.1.0/ViT_L16.h5">Model 3.8</a></td>
    <td>A+B</td>
    <td>0.90</td>
    <td>0.90</td>
    <td>0.70</td>
    <td>L/16</td>
    <td>87.8</td>
    <td>84.8</td>
    <td>81.9</td>
  </tr>
</table>

## Data
COMING SOON

## BibTeX
```bibtex
@article{serra2023emotions,
    author    = {Serra, Alessio and Carrara, Fabio and Tesconi, Maurizio and Falchi, Fabrizio},
    title     = {The Emotions of the Crowd: Learning Image Sentiment from Tweets via Cross-modal Distillation},
    journal   = {ECAI},
    year      = {2023},
}
```
