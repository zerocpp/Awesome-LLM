(杨万里 et al., 中科院计算所, ACL 2024 Findings)

![NICE学术分享33期](../attachments/NICE_Model_Editing_ywl.pdf)

# Note
**模型编辑的蝴蝶效应**

模型编辑采用ROME方法和MEMIT方法
用PPL（Perplexity，困惑度）来反映模型状态
单次编辑就足以导致模型崩溃，连续编辑更甚

**ROME（Rank-One Model Editing）**
ROME 是一种基于低秩更新的方法，用于高效编辑大语言模型（LLMs）的特定知识。主要特点包括：
1. **核心思想**：
• 利用神经网络权重的低秩性质，通过对模型中关键层的权重进行**秩为 1 的更新**来实现知识的定向编辑。
• 不需要对整个模型重新训练，而是针对某些层的权重矩阵进行增量式修改。
2. **操作过程**：
• **定位关键层**：通过激活分析确定与目标知识相关的关键层（通常是中间层）。
• **编辑目标**：使用具体的输入输出对（如输入某一事实，输出正确答案）作为编辑目标。
• **低秩更新**：通过计算特定的梯度，构造一个低秩调整矩阵以更新模型权重。
3. **优势**：
• 高效性：修改局部层权重，无需大规模模型调优。
• 可解释性：通过低秩更新，可以清楚地理解模型被修改的位置及影响。
• 精确性：修改对目标知识高效，且对非目标知识的影响最小。
4. **应用场景**：
• 动态修正模型知识，例如纠正错误或过时的知识。
• 可扩展至多个任务，例如实体知识更新或特定任务的微调。

**MEMIT（Mass-Editing Memory in Transformer）**
MEMIT 是一种专为 Transformer 架构设计的**批量知识编辑**方法，针对需要同时编辑多个知识点的问题提出了一种高效解决方案。
1. **核心思想**：
• 基于类似 ROME 的方法，但扩展为支持**批量并行编辑**，实现对多个目标知识的同步更新。
• 通过同时对模型中多层、多位置的权重进行更新来实现批量编辑。
2. **操作过程**：
• **识别编辑位置**：针对每个目标知识点，确定在模型中需要调整的层和位置。
• **联合优化**：利用多个输入输出对，通过联合优化构造一个更新矩阵，使模型能够同时学习多个新知识点。
• **批量更新**：将更新应用到多个关键层，确保批量知识点同时被修改。
3. **优势**：
• **高效批量更新**：支持同时修改数百甚至上千个知识点，适合大规模模型维护。
• **稳定性**：通过联合优化，最大程度降低知识冲突及对未修改知识的影响。
• **扩展性**：可用于扩充模型知识库，或快速适配新任务。
4. **技术挑战及解决**：
• **冲突管理**：对多个知识点的修改可能引发冲突，MEMIT 使用多目标优化技术降低冲突影响。
• **可扩展性**：通过针对 Transformer 层的特定设计，保证方法能够适应大模型的复杂性。
**比较与适用场景**
**特性** **ROME** **MEMIT**
编辑规模 单个知识点 多个知识点同时编辑
更新复杂度 单一低秩更新 批量联合优化
修改目标 精确地定向修改一条知识 同时编辑多个相关或不相关的知识
对未修改知识的影响 最小化干扰 管控批量冲突，影响略大
适用场景 单点修复（如纠正单个事实错误） 大规模知识库更新或维护

这两种方法适合不同的模型编辑需求。ROME 更适用于精确地纠正模型知识，而 MEMIT 更适合批量更新场景，例如快速适配模型到新的领域或更新多个过时的事实知识。

# Citation
```
@inproceedings{yang-etal-2024-butterfly,
    title = "The Butterfly Effect of Model Editing: Few Edits Can Trigger Large Language Models Collapse",
    author = "Yang, Wanli  and
      Sun, Fei  and
      Ma, Xinyu  and
      Liu, Xun  and
      Yin, Dawei  and
      Cheng, Xueqi",
    editor = "Ku, Lun-Wei  and
      Martins, Andre  and
      Srikumar, Vivek",
    booktitle = "Findings of the Association for Computational Linguistics: ACL 2024",
    month = aug,
    year = "2024",
    address = "Bangkok, Thailand",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.findings-acl.322",
    doi = "10.18653/v1/2024.findings-acl.322",
    pages = "5419--5437",
    abstract = "Although model editing has shown promise in revising knowledge in Large Language Models (LLMs), its impact on the inherent capabilities of LLMs is often overlooked. In this work, we reveal a critical phenomenon: even a single edit can trigger model collapse, manifesting as significant performance degradation in various benchmark tasks. However, benchmarking LLMs after each edit, while necessary to prevent such collapses, is impractically time-consuming and resource-intensive. To mitigate this, we propose using perplexity as a surrogate metric, validated by extensive experiments demonstrating changes in an edited model{'}s perplexity are strongly correlated with its downstream task performances. We further conduct an in-depth study on sequential editing, a practical setting for real-world scenarios, across various editing methods and LLMs, focusing on hard cases from our previous single edit studies. The results indicate that nearly all examined editing methods result in model collapse after only few edits. To facilitate further research, we have utilized GPT-3.5 to develop a new dataset, HardEdit, based on those hard cases. This dataset aims to establish the foundation for pioneering research in reliable model editing and the mechanisms underlying editing-induced model collapse. We hope this work can draw the community{'}s attention to the potential risks inherent in model editing practices.",
}
```