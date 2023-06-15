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
> + T5(Text To Text Transfer Transformer)

### Your Data
### Data Pre-Process
### Task Specify
## Pre-Training
### Model Structure
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
