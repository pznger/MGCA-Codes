# MGCA: Multi-Granularity Candidate-Aware User Modeling for Personalized News Recommendation

> ⚠️ **Notice**: The complete code has not been released yet. We will gradually update the code and related documentation. Stay tuned!

## 📄 Paper Information

**Personalized News Recommendation with Multi-granularity Candidate-aware User Modeling**

- **Authors**: Qiang Li, Xinze Lin, Shenghao Lv, Faliang Huang, Xiangju Li
- **arXiv**: [2504.14130](https://arxiv.org/abs/2504.14130)
- **Subjects**: Information Retrieval (cs.IR), Artificial Intelligence (cs.AI)

## 📝 Abstract

Matching candidate news with user interests is crucial for personalized news recommendations. Most existing methods can represent a user's reading interests through a single profile based on clicked news, which may not fully capture the diversity of user interests. Although some approaches incorporate candidate news or topic information, they remain insufficient because they neglect the **multi-granularity relatedness** between candidate news and user interests.

To address this, this study proposed a **Multi-Granularity Candidate-Aware (MGCA) user modeling framework** that integrated user interest features across various levels of granularity. It consists of two main components:

1. **Candidate News Encoding**
   - News textual information extractor
   - Knowledge-enhanced entity information extractor

2. **User Modeling**
   - Word-level candidate-aware mechanism
   - Entity-level candidate-aware mechanism
   - News-level candidate-aware mechanism

Extensive experiments on a real-world dataset demonstrated that the proposed model could significantly outperform baseline models.

## 🏗️ Model Architecture

```
MGCA Framework
├── Candidate News Encoder
│   ├── Text Information Extractor (Multi-head Self-Attention)
│   └── Knowledge-enhanced Entity Information Extractor
│
└── User Modeling
    ├── News-level Candidate-aware Attention
    ├── Word-level Candidate-aware Attention (Fastformer)
    └── Entity-level Candidate-aware Co-Attention (Graph Co-Attention Network)
```

## 📁 Code Structure

```
MGCA-Codes/
├── Models.py           # Model definitions (Attention, Fastformer, MGCA, etc.)
├── Hypers.py           # Hyperparameter configurations
├── Preprocessing.py    # Data preprocessing module
├── Utils.py            # Utility functions (metrics: AUC, MRR, nDCG, etc.)
├── Generator.py        # Data generators (Keras Sequence)
├── main.ipynb          # Main entry point
├── MINDsmall/          # MIND dataset directory
│   ├── train/          # Training set
│   └── dev/            # Validation set
├── glove.840B.300d/    # GloVe pre-trained word embeddings
└── KGData/             # Knowledge graph data
    ├── entity_embedding.npy
    ├── entity2id.txt
    └── KGGraph.json
```

## 🔧 Requirements

### Main Dependencies

| Package      | Version                |
| ------------ | ---------------------- |
| Python       | 3.6+                   |
| TensorFlow   | 1.x (1.14 recommended) |
| Keras        | 2.2.x                  |
| NumPy        | 1.16+                  |
| scikit-learn | 0.20+                  |
| NLTK         | 3.4+                   |

### Installation

```bash
pip install tensorflow==1.14.0
pip install keras==2.2.5
pip install numpy
pip install scikit-learn
pip install nltk
```

### NLTK Data Download

```python
import nltk
nltk.download('punkt')
```

## 📊 Dataset

This project uses the small version of [MIND (Microsoft News Dataset)](https://msnews.github.io/) - MINDsmall.

### Dataset Download

1. Download MINDsmall dataset from [MIND official website](https://msnews.github.io/)
2. Download [GloVe](https://nlp.stanford.edu/projects/glove/) pre-trained word embeddings (glove.840B.300d)
3. Prepare knowledge graph data (entity embeddings and KG structure)

### Data Format

- `behaviors.tsv`: User behavior data (impression logs)
- `news.tsv`: News article data
- `entity_embedding.vec`: Entity embedding vectors

## 🚀 Quick Start

1. **Configure Data Paths**

   Set the correct data paths in `main.ipynb`:

   ```python
   data_root_path = 'MINDsmall\\'
   embedding_path = 'glove.840B.300d\\'
   KG_root_path = 'KGData\\'
   ```

2. **Run Training**

   Open and run the `main.ipynb` notebook

3. **Evaluate Model**

   The model will automatically evaluate on the validation set with the following metrics:

   - AUC (Area Under Curve)
   - MRR (Mean Reciprocal Rank)
   - nDCG@5
   - nDCG@10

## ⚙️ Hyperparameters

Main hyperparameters are defined in `Hypers.py`:

| Parameter      | Value | Description                         |
| -------------- | ----- | ----------------------------------- |
| MAX_TITLE      | 30    | Maximum number of words in title    |
| MAX_CONTENT    | 50    | Maximum number of words in content  |
| MAX_ENTITY     | 5     | Maximum number of entities per news |
| MAX_CLICK      | 50    | Maximum user click history length   |
| npratio        | 4     | Negative sampling ratio             |
| max_entity_num | 10    | Maximum number of entities in KG    |

## 📈 Experimental Results

Please refer to our paper for detailed experimental results on the MINDsmall dataset.

## 📖 Citation

If you use this code in your research, please cite our paper:

```bibtex
@article{li2025personalized,
  title={Personalized News Recommendation with Multi-granularity Candidate-aware User Modeling},
  author={Li, Qiang and Lin, Xinze and Lv, Shenghao and Huang, Faliang and Li, Xiangju},
  journal={arXiv preprint arXiv:2504.14130},
  year={2025}
}
```

## 📧 Contact

If you have any questions, please feel free to:

- Open a GitHub Issue
- Contact the corresponding author via email (see paper for details)

## 📜 License

This project is for academic research purposes only.

