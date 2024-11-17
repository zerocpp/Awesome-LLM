(杨万里 et al., 中科院计算所, EMNLP 2024 Findings)
# Note
## two factors behind ROME's collapse
- inconsistent implementation of key vectors
- anomalous distribution of first token representations
## Why does the **first token** have a different representation?
- 可能是自回归模型的自交互导致的
- Position Embedding可能会导致崩溃，但不是决定性影响
# Citation
```
@inproceedings{yang-etal-2024-fall,
    title = "The Fall of {ROME}: Understanding the Collapse of {LLM}s in Model Editing",
    author = "Yang, Wanli  and
      Sun, Fei  and
      Tan, Jiajun  and
      Ma, Xinyu  and
      Su, Du  and
      Yin, Dawei  and
      Shen, Huawei",
    editor = "Al-Onaizan, Yaser  and
      Bansal, Mohit  and
      Chen, Yun-Nung",
    booktitle = "Findings of the Association for Computational Linguistics: EMNLP 2024",
    month = nov,
    year = "2024",
    address = "Miami, Florida, USA",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.findings-emnlp.236",
    pages = "4079--4087",
    abstract = "Despite significant progress in model editing methods, their application in real-world scenarios remains challenging as they often cause large language models (LLMs) to collapse. Among them, ROME is particularly concerning, as it could disrupt LLMs with only a single edit. In this paper, we study the root causes of such collapse. Through extensive analysis, we identify two primary factors that contribute to the collapse: i) inconsistent handling of prefixed and unprefixed keys in the parameter update equation may result in very small denominators, causing excessively large parameter updates; ii) the subject of collapse cases is usually the first token, whose unprefixed key distribution significantly differs from the prefixed key distribution in autoregressive transformers, causing the aforementioned issue to materialize. To validate our findings, we propose a simple yet effective approach: uniformly using prefixed keys during editing phase and adding prefixes during testing phase to ensure the consistency between training and testing. The experimental results show that the proposed solution can prevent model collapse while maintaining the effectiveness of the edits.",
}
```
