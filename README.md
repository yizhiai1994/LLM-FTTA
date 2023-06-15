# LLM-FTTA (under construction)
Large Language Model —— From Training To Application

Everything I know about LLM in NLP.


## Timeline
## Data Process
### Public Data
#### C4(Colossal Clean Crawled Corpus)
Detail Page: 

> + https://www.tensorflow.org/datasets/catalog/c4

Source Paper:

> + Raffel C, Shazeer N, Roberts A, et al. Exploring the limits of transfer learning with a unified text-to-text transformer[J]. The Journal of Machine Learning Research, 2020, 21(1): 5485-5551.
> + https://www.jmlr.org/papers/volume21/20-074/20-074.pdf

Download Method
<pre><code>pip install tfds-nightly[c4]
echo 'tfds-nightly[c4]' > /tmp/beam_requirements.txt
python -m tensorflow_datasets.scripts.download_and_prepare \
  --datasets=c4/en \
  --data_dir=gs://$MY_BUCKET/tensorflow_datasets \
  --beam_pipeline_options="project=$MY_PROJECT,job_name=c4,staging_location=gs://$MY_BUCKET/binaries,temp_location=gs://$MY_BUCKET/temp,runner=DataflowRunner,requirements_file=/tmp/beam_requirements.txt,experiments=shuffle_mode=service,region=$MY_REGION"
</code></pre>
Language Options: 
> + c4/en.noclean
> + c4/en
> + c4/en.noclean
> + c4/realnewslike
> + c4/webtextlike
> + c4/multilingual 

Related Models:
> + T5 (Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer)

### Your Data
### Data Pre-Process
### Task Specify
## Pre-Training
### Model Structure
### Training Objective
#### MLM (Mask Language Model)
Detail[1]:
> +  Simply mask some percentage of the input tokens at random, and then predict those masked tokens.
Example[1]:
> + Orginal: my dog is hairy
> + Input: my dog is [MASK]
> + Output: hairy
>> + Tips: In the paper "BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding", the authors said "80% of the time: Replace the word with the [MASK] token" and "10% of the time: Replace the word with a
random word" and "10% of the time: Keep the word unchanged"
Related Models:
> + GPT-3 (GPT-3: Language Models are Few-Shot Learners)
> + BERT (BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding)
> + RoBERTa (RoBERTa: A Robustly Optimized BERT Pretraining Approach)
> + ALBERT (ALBERT: A Lite BERT for Self-supervised Learning of Language Representations)
#### NSP (Next Sentence Prediction)
Detail[1]:
> + Choosing the sentences A and B for each pretraining example, 50% of the time B is the actual next sentence that follows A (labeled as IsNext), and 50% of the time it is a random sentence from the corpus (labeled as NotNext).
Example[1]:
> + Input1: [CLS] the man went to [MASK] store [SEP] he bought a gallon [MASK] milk [SEP]
> + Output1: IsNext
> + Input2: [CLS] the man [MASK] to the store [SEP] penguin [MASK] are flight ##less birds [SEP]
> + Output2: NotNext
Related Models:
> + BERT (BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding)
> + UniLM (Unified Language Model Pre-training for Natural Language Understanding and Generation)
#### Text-to-Text
Related Models:
> + T5 (Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer)
### Parameters Selection
### Optimizer
### Training Pipline
### Training Skills
### Acceleration Techniques
## Fine-Tuning
### Test Tasks
> + Sentence acceptability judgment 
>> + CoLA (Warstadt et al., 2018)
> + Sentiment analysis 
>> + SST-2 (Socher et al., 2013)
> + Paraphrasing/sentence similarity 
>> + MRPC (Dolan and Brockett, 2005)
>> + STS-B (Ceret al., 2017)
>> + QQP (Iyer et al., 2017)
> + Natural language inference 
>> + MNLI (Williams et al., 2017)
>> + QNLI (Rajpurkar et al., 2016)
>> + RTE (Dagan et al., 2005)
>> + CB (De Marneff et al., 2019)
> + Coreference resolution 
>> + WNLI and WSC (Levesque et al., 2012)
> + Sentence completion 
>> + COPA (Roemmele et al., 2011)
> + Word sense disambiguation 
>> + WIC (Pilehvar and Camacho-Collados, 2018)
> + Question answering 
>> + MultiRC (Khashabi et al., 2018)
>> + ReCoRD (Zhang et al., 2018)
>> + BoolQ (Clark et al., 2019))
## Checking
## deployment
## Application
## Reference
[1] Devlin J, Chang M W, Lee K, et al. Bert: Pre-training of deep bidirectional transformers for language understanding[J]. arXiv preprint arXiv:1810.04805, 2018.
