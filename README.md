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
## Checking
## deployment
## Application
