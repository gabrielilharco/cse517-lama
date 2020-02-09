# LAMA: LAnguage Model Analysis

This repository is forked from https://github.com/facebookresearch/LAMA

LAMA is a probe for analyzing the factual and commonsense knowledge contained in pretrained language models. <br>
#### The dataset for the LAMA probe is available at https://dl.fbaipublicfiles.com/LAMA/data.zip <br>
LAMA contains a set of connectors to pretrained language models. <br>
LAMA exposes a transparent and unique interface to use:

- Transformer-XL (Dai et al., 2019)
- BERT (Devlin et al., 2018)
- ELMo (Peters et al., 2018)
- GPT (Radford et al., 2018)
- RoBERTa (Liu et al., 2019)

Actually, LAMA is also a beautiful animal.

## The LAMA probe

To reproduce the results:

### 1. Create conda environment and install requirements

(optional) It might be a good idea to use a separate conda environment. It can be created by running:
```
conda create -n lama37 -y python=3.7 && conda activate lama37
pip install -r requirements.txt
```

### 2. Download the data

```bash
wget https://dl.fbaipublicfiles.com/LAMA/data.zip
unzip data.zip
rm data.zip
```

### 3. Download the models

#### DISCLAIMER: ~55 GB on disk

Install spacy model
```bash
python3 -m spacy download en
```

Download the models
```bash
chmod +x download_models.sh
./download_models.sh
```

The script will create and populate a _pre-trained_language_models_ folder.
If you are interested in a particular model please edit the script.


### 4. Run the experiments

```bash
python scripts/run_experiments.py
```

results will be logged in _output/_ and  _last_results.csv_.

## Other versions of LAMA

### LAMA-UHN

This repository also provides a script (`scripts/create_lama_uhn.py`) to create the data used in (Poerner et al., 2019).

### Negated-LAMA
This repository also gives the option to evalute how pretrained language models handle negated probes (Kassner et al., 2019), set the flag `use_negated_probes` in `scripts/run_experiments.py`. Also, you should use this version of the LAMA probe https://dl.fbaipublicfiles.com/LAMA/negated_data.tar.gz

## Other References

- __(Kassner et al., 2019)__ Nora Kassner, Hinrich Schütze. _Negated LAMA: Birds cannot fly_. arXiv preprint arXiv:1911.03343, 2019.

- __(Poerner et al., 2019)__ Nina Poerner, Ulli Waltinger, and Hinrich Schütze. _BERT is Not a Knowledge Base (Yet): Factual Knowledge vs. Name-Based Reasoning in Unsupervised QA_. arXiv preprint arXiv:1911.03681, 2019.

- __(Dai et al., 2019)__ Zihang Dai, Zhilin Yang, Yiming Yang, Jaime G. Carbonell, Quoc V. Le, and Ruslan Salakhutdi. _Transformer-xl: Attentive language models beyond a fixed-length context_. CoRR, abs/1901.02860.

- __(Peters et al., 2018)__ Matthew E. Peters, Mark Neumann, Mohit Iyyer, Matt Gardner, Christopher Clark, Kenton Lee, and Luke Zettlemoyer. 2018. _Deep contextualized word representations_. NAACL-HLT 2018

- __(Devlin et al., 2018)__ Jacob Devlin, Ming-Wei Chang, Kenton Lee, and Kristina Toutanova. 2018. _BERT: pre-training of deep bidirectional transformers for language understanding_. CoRR, abs/1810.04805.

- __(Radford et al., 2018)__ Alec Radford, Karthik Narasimhan, Tim Salimans, and Ilya Sutskever. 2018. _Improving language understanding by generative pre-training_.

- __(Liu et al., 2019)__ Yinhan Liu, Myle Ott, Naman Goyal, Jingfei Du, Mandar Joshi, Danqi Chen, Omer Levy, Mike Lewis, Luke Zettlemoyer, Veselin Stoyanov. 2019. _RoBERTa: A Robustly Optimized BERT Pretraining Approach_. arXiv preprint arXiv:1907.11692.



## Reference:

The LAMA probe is described in the following paper:

```bibtex
@inproceedings{petroni2019language,
  title={Language Models as Knowledge Bases?},
  author={F. Petroni, T. Rockt{\"{a}}schel, A. H. Miller, P. Lewis, A. Bakhtin, Y. Wu and S. Riedel},
  booktitle={In: Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing (EMNLP), 2019},
  year={2019}
}
```

## Licence

LAMA is licensed under the CC-BY-NC 4.0 license. The text of the license can be found [here](LICENSE).
