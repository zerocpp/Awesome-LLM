(Dathathri et al., DeepMind, Nature 2024)
https://www.nature.com/articles/s41586-024-08025-4
[机器之心：Nature专业户DeepMind又登封面，开源水印技术SynthID-Text，Gemini已经用上了](https://mp.weixin.qq.com/s/_4gK9tUV6rHky_SGBTrp7w)
[s41586-024-08025-4.pdf](../attachments/s41586-024-08025-4.pdf)

# Abstract
这篇论文介绍了一种名为SynthID-Text的文本水印方案，旨在识别大型语言模型（LLM）生成的合成文本。该方案通过在文本生成的采样过程中引入细微的统计特征，从而实现对文本的标记，而无需影响LLM的训练过程。 SynthID-Text具有可扩展性，可用于大规模生产系统，并能有效地识别LLM输出的文本，同时保持文本质量。 论文还比较了SynthID-Text与现有其他水印方案的性能，并展示了其在检测精度和文本质量方面取得的优异表现。 此外，该研究还探讨了将SynthID-Text与LLM生产环境中的常见加速技术相结合的方法。

# Note


# Cite
```
@article{dathathri2024scalable,
  title={Scalable watermarking for identifying large language model outputs},
  author={Dathathri, Sumanth and See, Abigail and Ghaisas, Sumedh and Huang, Po-Sen and McAdam, Rob and Welbl, Johannes and Bachani, Vandana and Kaskasoli, Alex and Stanforth, Robert and Matejovicova, Tatiana and others},
  journal={Nature},
  volume={634},
  number={8035},
  pages={818--823},
  year={2024},
  publisher={Nature Publishing Group UK London}
}
```