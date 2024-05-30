# MER_24

# MER 2024 竞赛概况

# 人员分配

Lead Researcher：李佳
## Track1 MER-SEMI
成员：程浩（队长）、张龙、何艺超、韩宇、陈银、李佳

Github项目地址：https://github.com/MM-2024/MER_24

# 时间节点和注意事项
to-be-fill

# 结果提交
to-be-fill

# 论文提交

# 任务总体推进情况
## 数据预处理
## baseline
## 特征工程
> 提取什么样的特征
## 端到端的多模态模型
# 任务及数据集介绍
## 任务
## 数据集
> 1.Train&Val provides 5,030 samples labeled in 6 candidate categories (worried, happy, neutral, angry, surprise, andsad).
> 2.Clean test samples for Track1 and noisy test samples for Track2 are merged into unlabeled data, but we do not provide the name of test samples.Please try to develop a system that can perform well on clean and noisy samples. Each team should submit the most likely discrete label among the 6 candidate labels (worried, happy, neutral, angry, surprise, andsad).
> 3.For Track3, we encourage participants to generate any number of labels in any category, aiming to describe the character's emotional state as accurately as possible.
> 4.For all tracks, participants should predict results for all 115,595 unlabeled data.
![image](https://github.com/MM-2024/MER_24/assets/90198143/cef589a1-3ddb-42ee-85a7-2b4abcdf1af7)

总共包含5030个有标注的样本和115595个未标注的样本。所有数据都作为视频文件提供（包含音频），而对于5030个标注样本来说，总共有4种标注：
  1.转录文本
  2.情感标签和效价（valence）标签
  3.情感相关的描述
  4.开放式标签
**数据集来源**：
国产影视剧
剧集分类待探究，如果都是言情肥皂剧的话可能与转录文本最相关。

**数据集结构**:

**数据集注释特点**:


# 目前技术方案和验证结论
三个初步的想法（待验证）:
  1.特征工程，对每个模态的特征提取器选取最好的
  2.多模态模型：先端到端自监督的训练110k条数据，然后在5k条上finetune
  3.除了以上的多模态模型之外，其他半监督的方法（待调研）
# 参考资料、开源项目及工具
相关论文阅读之后总结一下放在这里
按不同类型的论文分开
# 任务安排及达成情况
## 2024-5-27周（第一周）
### 任务安排：
#### 调研任务：
1.梳理此文档
2.阅读相关文献
3.初步调研
#### 技术任务：
  数据预处理:
- [ ] 取帧+crop人脸
- [ ] 提取音频（采样率12000）
- [ ] 转录文本（采用openai whisper）
	复现baseline
