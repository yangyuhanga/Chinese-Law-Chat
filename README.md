# Chinese-Law-Chat
以Llama为基底模型微调得到的中文法律大模型

# 简介
![微信图片_20240121000531](https://github.com/yangyuhanga/Chinese-Law-Chat/assets/131662288/3dfd1225-5497-4763-8a13-285c009b42e6)
  如图所示，我们基于huggingface提供的LLaMA-7B模型，并针对模型的中文理解能力及其在法律领域的应用效果进行了优化。
  
  鉴于原始LLaMA模型主要基于英文语料库进行预训练，其对中文文本的处理能力较弱。为了改善这一点，我们采用了结合LoRA技术的方法。通过将Chinese_llama_lora和Chinese_alpaca_lora与LLaMA模型进行权重融合，我们生成了Chinese LLaMA Alpaca（简称为7B-Full）模型。
  
  为增强模型在法律领域的应用效果，我们构建并引入了一个名为"legal_pre"的法律专业预训练语料库。该库包含了1万份涵盖多种法律文本的长文本，如地方性法律法规、检察法规和司法解释。为防止过拟合，我们还加入了通用领域的数据。通过对该语料库进行迭代预训练，模型的法律术语敏感性得到了提升，从而增强了对真实法律场景的理解能力。
  
  我们按三个阶段引入不同的数据集进行微调，每个阶段均根据数据特性进行了精心设计的微调过程。最终获得了我们的Chinese-Law-Chat模型

# 案例分析
在法律领域，一个关键的应用目标是将法律知识有效地应用于具体案例分析中。为此，我们选定了劳动法、消费者权益保护法和道路交通安全法这三个具体的法律子领域。在这些领域中，我们对比了7B-Full、7B-Chat和CLC-7B这三个模型的性能，重点评估了它们在案件分析中的回答准确性和逻辑合理性。

<img width="300" alt="image" src="https://github.com/yangyuhanga/Chinese-Law-Chat/assets/131662288/83147eea-1da3-4075-9224-01d548d3d6c0">

<img width="300" alt="image" src="https://github.com/yangyuhanga/Chinese-Law-Chat/assets/131662288/f8434811-5d67-4165-a0fc-cd65727d5aa3">

<img width="300" alt="image" src="https://github.com/yangyuhanga/Chinese-Law-Chat/assets/131662288/860e2863-2f2f-4c49-b3f5-5d51204b2975">

经全面评估，CLC-7B模型在法律案例分析方面表现卓越。它不仅准确引用并解释法律条款，还能将法条与案例情境有效结合，显示出对法律知识的深入理解和灵活应用。CLC-7B提供的建议既有充分法律依据，又与案例背景紧密相关，展现了其在法律领域的应用潜力。模型在案件分析中的逻辑严密性和合理性进一步证明了其作为法律语言模型的效用。这些成果为未来法律语言模型的发展提供了重要参考。

# 数据集
本研究构建了一个全面而深入的[法律领域数据集](https://pan.baidu.com/s/1ssEtjhXBnxPSnFOoKkx4Gg?pwd=9uxf)，采用了多元化的数据来源策略。我们收集了大量与法律相关的原始文本数据，涵盖了包括法律文书、案例数据库和法律文献在内的多种类型。这些数据不仅包括了法律条款、裁决文书、法庭辩论等专业内容，还包括了政府法规官方网站和法律法规解读平台上的权威数据。此外，为了捕捉法律领域的实际应用和公众视角，我们还收集了法律论坛、博客和问答平台上的用户讨论和问题。特别注意的是，我们覆盖了刑法、民事法、知识产权法等多个子领域，以及法规、法案、合同等不同类型的法律文本，确保数据集的全面性和多样性。

# 实验结果
我们使用c-eval对我们的模型进行测试，无论是知识定义问题还是案例分析问题，无论是零样本学习效果还是少样本学习效果，Chinese-Law-Chat模型相比于Chinese-LLaMA-Alpaca-7B和Llama-2-7b-chat都更加出色。

# 推理
参考[Chinese-LLaMA-Alpaca项目](https://github.com/ymcui/Chinese-LLaMA-Alpaca)相关脚本

# 使用
为方便复现实验和使用该模型，实验中使用到的LoRA权重，模型均进行公开：
| LoRA   | 链接   |
|-------|-------|
| chinese_alpaca_plus_lora_7b | [百度网盘](https://pan.baidu.com/s/1FuxaLDZ3K7Xmnie4hHKjBw?pwd=dps6) |
| chinese_alpaca_pro_lora_7b | [百度网盘](https://pan.baidu.com/s/1vgEL7RLpZMBrXa1VowAmbA?pwd=k3xc) |
| chinese_llama_plus_lora_7b | [百度网盘](https://pan.baidu.com/s/1OQ271ZylzoD1BIgkHEA5RQ?pwd=i6tv) |
| chinese_alpaca_2_lora_7b | [百度网盘](https://pan.baidu.com/s/13SDCCMLHOr27M1fNt0PLjQ?pwd=5a3x) |
| chinese_llama_2_lora_7b | [百度网盘](https://pan.baidu.com/s/15Ui4gjuRVSWFyyObv5HdVw?pwd=hfyy) |
| chinese_alpaca_plus_lora_13b | [百度网盘](https://pan.baidu.com/s/16R72rygdx4XrBQEeuYsWMQ?pwd=5w3z) |
| chinese_llama_plus_lora_13b | [百度网盘](https://pan.baidu.com/s/1bi0RjlhBEHE1aUJj4EaGew?pwd=anfa) |

| huggingface模型   | 链接   |
|-------|-------|
| 7B_hf | [百度网盘](https://pan.baidu.com/s/1GdScmUBAsT-XhvNt-0N_mg?pwd=nowg) |
| Llama-2-7b-chat-hf | [百度网盘](https://pan.baidu.com/s/1Z_0bzdyCOf83Pg9IDOLNeg?pwd=scio) |

| model   | 链接   |
|-------|-------|
| 7B_Full | [百度网盘](https://pan.baidu.com/s/1nIwvXW3FDj5fzZUJGjCPVQ?pwd=ib75) |
| Llama-7b-chat | [百度网盘](https://pan.baidu.com/s/16s9ZlugBwi86bFcgIBfJ_g?pwd=d3go) |
| 7B_Full_pretain | [百度网盘](https://pan.baidu.com/s/16TvHJw1P6A4ub4nRYVpqyw?pwd=dpxd) |
| Chinese-Law-Chat | [百度网盘](https://pan.baidu.com/s/1Ybei2_recVWfKXyp9lG-sA?pwd=w54x) |
