# Multilabel Tag Prediction on StackOverflow Questions

![Alt text](images/stackoverflow.png)

## Introduction
The current case-study revolves around tag prediction of Stack Overflow questions. We utilise [StackSample Kaggle dataset](https://www.kaggle.com/datasets/stackoverflow/stacksample), which represents approximately 10% of Stack Overflow Q&A corpus. More specifically we only utilise the following files:
1. Questions.csv
    * A unique identifier of the user that created each question
    * A unique identifier of the question itself
    * Creation and closing datetimes corresponding to each question
    * The cumulative reaction score of each question (zero, positive or negative)
    * The title and main body of each question.
3. Tags.csv
    * A unique identifier for each question.
    * One or more associated tags.



## EDA 
Due to time and resources limitations, from the beginning of this project, we knew that we must retain a proper subset of the original dataset. After merging two csv files, we aimed to identify insights for Tags via plots and statistics, thus leading us to the result to experiment in keeping only top N tags. After some trial and errors, we decided it (for future ease) to experiment in keeping with the top M tag combinations. Note that we decided to opt only the Questions with positive cummulative score, as we believe this kind of questions, most of the times provide valuable insights and solutions, therefore more quality data.


The biggest time allocation of this project was for sure EDA, and one of its subgoals, which is preprocessing. We gave a strong focus with many manual examples exploration, in order to reassure pipeline's stability. We treated specially words like the name of a Tag, because they give a strong weight to prediction. In addition, most of the tags are programming languages, packages, versions, systems and other and due to this fact we were very cautius with punctuation (C#,C++,.NET).

After a single run of EDA notebook [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/spyros-briakos/Multilabel_StackOverflow_Tag_Prediction/blob/main/notebooks/EDA.ipynb), having opted M value, it is produced a preprocessed.csv, which contains data with top M tag combinations, ready to manipulate afterwards on model notebooks. In that way, code is more generic and we have the ability to store different subsets of original dataset, as we prefer.











## Baseline Model

With similar thought process Baseline_Model notebook [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/spyros-briakos/Multilabel_StackOverflow_Tag_Prediction/blob/main/notebooks/Baseline_Model.ipynb) is 

> [!TIP]
> Helpful advice for doing things better or more easily.


## LLM Model
dsadsadsada





















## Experiment Table

<table>

  <tr>
    <td colspan="3" align="center">EDA</td>
    <td colspan="4" align="center">Linear SVC</td>
    <td colspan="4" align="center">BERT</td>
  </tr>
  
  <tr>
    <td align="center">Questions</td>
    <td align="center">Tag Combinations</td>
    <td align="center">Unique Tags</td>
    <td align="center">Hamming Loss</td>
    <td align="center">Micro-F1</td>
    <td align="center">Macro-F1</td>
    <td align="center">Time (mins)</td>
    <td align="center">Hamming Loss</td>
    <td align="center">Micro-F1</td>
    <td align="center">Macro-F1</td>
    <td align="center">Epoch GPU (mins)</td>
  </tr>
  <tr>
    <td align="center">33.374</td>
    <td align="center">20</td>
    <td align="center">16</td>
    <td align="center">0.03</td>
    <td align="center">0.83</td>
    <td align="center">0.81</td>
    <td align="center">3</td>
    <td align="center">0.02</td>
    <td align="center">0.86</td>
    <td align="center">0.84</td>
    <td align="center">11</td>
  </tr>
  <tr>
    <td align="center">42.369</td>
    <td align="center">35</td>
    <td align="center">28</td>
    <td align="center">0.02</td>
    <td align="center">0.8</td>
    <td align="center">0.79</td>
    <td align="center">6</td>
    <td colspan="4" align="center">N/A</td>
  </tr>
  <tr>
    <td align="center">48.505</td>
  <td align="center">50</td>
  <td align="center">38</td>
  <td align="center">0.01</td>
  <td align="center">0.79</td>
  <td align="center">0.77</td>
  <td align="center">8</td>
  <td align="center">0.01</td>
  <td align="center">0.84</td>
  <td align="center">0.78</td>
  <td align="center">16</td>
  </tr>
<tr>
  <td align="center">62.118</td>
  <td align="center">100</td>
  <td align="center">74</td>
  <td align="center">0.01</td>
  <td align="center">0.78</td>
  <td align="center">0.7</td>
  <td align="center">17</td>
  <td align="center">0.02</td>
  <td align="center">0.68</td>
  <td align="center">0.28</td>
  <td align="center">21</td>
</tr>

<tr>
  <td align="center">70.474</td>
  <td align="center">150</td>
  <td align="center">104</td>
  <td align="center">0.01</td>
  <td align="center">0.76</td>
  <td align="center">0.68</td>
  <td align="center">24</td>
  <td colspan="4" align="center">N/A</td>
</tr>
  <tr>
    <td align="center">76.766</td>
    <td align="center">200</td>
    <td align="center">133</td>
    <td colspan="8" align="center">MEMORY RAM CRASH</td>
  </tr>
</table>


Unfortunately on the experiment procedure, we face RAM issues with 200 Top Tag Combinations, therefore we must limit in smaller subsets of original dataset.

Baseline model is **Linear Support Vector Machines** and except of its pretty descent performance, we have to mention that was very time efficient, managing to train in just a few seconds.

For a more sophisticated model we opted from HuggingFace library BERTforSequenceClassification architecture with **BERT 'bert-base-uncased'** model. Our choice is justified by the fact that we have a multilabel classification problem and also BERT is very popular for text classification. 

