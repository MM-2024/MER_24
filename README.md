# MER_24

# MER 2024 竞赛概况

# 人员分配


## MER-SEMI
Lead Researcher：李佳\
成员：程浩（队长）、张龙、何艺超、韩宇、任宏哲、陈银

Github项目地址：https://github.com/MM-2024/MER_24 \
offical web：https://zeroqiaoba.github.io/MER2024-website/

虽然是semi为题，但是半监督和无监督方法均是可以的



# 时间节点和注意事项
*注意！！！后期结果提交在官网，论文提交地址不在官网

*注意！！！官方只要求我们提供离散分类标签的结果

*注意！！！准确率被看成是认可的模型评价标准，但是最终排名的依据按照WAF为准

![image](https://github.com/MM-2024/MER_24/assets/156440850/484f0f28-ab9e-42ae-960f-f39f22be93a3)



解读：weighted-f1考虑了不同类别的重要性，也就是把每个类别的样本数量作为权重，计算加权f1。


2024.4.30:[基线论文](https://arxiv.org/abs/2404.17113)、[代码](https://github.com/zeroQiaoba/MERTools/tree/master/MER2024)发布

2024/6/30-2024/7/10：结果提交时间，结果在官网提交，目前link is coming soon

![image](https://github.com/MM-2024/MER_24/assets/156440850/4230d6ff-ae65-4623-83f2-d0547296ab78)

2024/6/30-2024/7/20：论文提交时间，论文官网给出了提交地址：https://cmt3.research.microsoft.com/MRAC2024

![image](https://github.com/MM-2024/MER_24/assets/156440850/26015b02-d4a9-4ec2-9ce8-9a8cdd969df0)

*注意：论文以pdf格式提交，官方给了latex模板，模板下载链接：https://2024.acmmm.org/files/ACM-MM24-paper-templates.zip，打开后有如下文件

![image](https://github.com/MM-2024/MER_24/assets/156440850/47d5032f-342d-41b6-a7bf-06ca97600425)

*注意：论文篇幅有限制，4页正文+1页参考文献  or  8页正文+2页参考文献

2024/8/5：论文接收通告

2024/8/18：终稿提交截止日期

2024/10/28：MRAC workshop



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
1. 转录文本
2. 情感标签和效价（valence）标签
3. 情感相关的描述
4. 开放式标签

**数据集来源**：\
国产影视剧\
剧集分类待探究，如果都是言情肥皂剧的话可能与转录文本最相关。\
![image](https://github.com/MM-2024/MER_24/assets/90198143/258313e4-9333-409f-8688-ca52d3d96a6a)
实际上今年的数据集和去年的相差不大。

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

offical baseline paper给出了几个参赛的指导意见：

1.在所有模态中，声学编码器的单模态效果最好，说明MER2024中的样本主要依靠声学模态来表达情感

2.域兼容性对视觉编码器非常重要，鼓励参赛者训练情感领域的预训练模型

3.文本模态和语音模态的性能和语言种类息息相关，选取和数据集同种语言的预训练模型效果可能会好些

4.通过注意力机制融合不同模态效果可能会好一些

5.原文中的table6给出了很多不同语言下的单模态预训练模型，可以参考


### 转录任务
任务称作：**Automatic Speech Recognition**
https://paperswithcode.com/task/automatic-speech-recognition &
https://paperswithcode.com/task/automatic-speech-recognition-2

评价指标： WERs (word error rates) or CER (character error rates) 对于中文来说，通常的CER都会比WER的表现好上非常多，甚至可能会出现CER 10，WER 80的情况[cite](https://paperswithcode.com/sota/speech-recognition-on-common-voice-chinese-2)

数据集：Common Voice 15, Fleurs datasets, AISHELL-1(普通话语音识别数据集)

参考：https://github.com/modelscope/FunASR/blob/main/README_zh.md (一个集合多个ASR工具的包）

对于AISHELL-1数据集, Qwen-audio模型表现最好, [参考](https://paperswithcode.com/sota/speech-recognition-on-aishell-1)

可用模型：paraformer-zh, Qwen-audio


# 任务安排及达成情况
## 2024-5-27周（第一周）
### 任务安排：
#### 调研任务：
1.梳理此文档\
2.阅读相关文献\
3.初步调研
#### 技术任务：
  数据预处理:
- [X] 取帧+crop人脸
- [X] 提取音频（采样率12000）
- [X] 转录文本
- [X] 复现baseline

***注意：标记数据中有3个、未标记数据中有34个视频，MTCNN无法提取人脸，导致所属的/data/public_datasets/MER_2024/mer2024-dataset-process/croped_face/labeled_croped/sample_00000074 文件夹为空，可能会导致错误***

## 2024-6-3周（第二周）
### 任务安排：
- [ ] 特征融合方法（张）
- [ ] 转录质量研究（何、韩）
- [ ] T、V 的特征工程（程）

### 发现的问题汇总：
1.数据转录的质量问题：
- [X] 是否解决？
A：据不完全调研，Qwen-Audio已经是中文ASR任务最好的模型了。这种质量的话也没办法。。。（考虑抛弃文本模型）

（1）转录成功，但汉语以英语呈现：例如：【id：00090351】现在已经这样了，我不能什么都不做---->But it's already like this, I can't do anything right now.

（2）转录失败，并以英语呈现：例如：【id：00038386】那我还得谢谢你啊---->I got it!

（3）转录结果为空，例如：【id：00013481】李严将军之下----><|zh-CN|> 或者直接没有 或者其他乱码

（4）转录成功，原视频为英语，但转录后的英语没有分词，例如：【id：00101684】instead it's about sloppiness and hearts which feel no responsibility for themselves.---->insteadit'saboutsloppinessandheartswhichfeelnoresponsibilityforthemselves.

（5）视频时间问题，发现有到33分钟的视频，实际播放长度越2-3秒，例如：【id：00047271】

![image](https://github.com/MM-2024/MER_24/assets/156440850/7929b87d-bc97-4ebd-a604-4445e913f6af)

*合并的数据没有问题，cuda_0下转录的数据为57795条（实际57794），cuda_1下转录的数据为57795条（实际57794），三个转录的文件中都有一个提示性的文件头，即["filename","transcription"]，所以合并的文件为115589条（实际115588），不过官方提供的unlabel数据为115595，说明有几条数据没有成功转录

*数据转录的质量验证逻辑：经过调研，数据集大部分为中文语音，于是初步找出转录后不为中文的数据条例并统计，发现有6000多条数据转录效果堪忧（已经将其文件名保存为npy文件，并发送至讨论小组，方便后期处理），进一步通过人为随机检查视频对照，发现转录结果的确出现问题，但是视频本身的口音问题也比较严重，这可能是转录失败的关键。

![image](https://github.com/MM-2024/MER_24/assets/156440850/8c98c635-db36-4719-8e25-fe05685c2416)

![image](https://github.com/MM-2024/MER_24/assets/156440850/791d9600-0fe7-4373-89f2-d58261695616)


# 可行思路和验证结论：

（按时间排序，留下姓名）
程浩Q：


程浩Q：（24-6-5）

- [ ] 为什么去年不用clip-large做baseline？
- [ ] 为什么文本部分不用clip-large？
- [ ] 如果把videomae large在这个数据集上预训练一下，那会有什么样的效果？因为这个是作者没有做到的。
- [ ] 特征融合上面，这个作者仅仅考虑了attention机制，那么有没有更复杂的机制？
- [ ] 看一下baseline怎么用whisper提取音频特征的，我准备用qwenaudio提取音频特征. 但是whisper的要比hubert的低十几个点. 不知道有没有必要
- [ ] 非常有可能hubert已经把音频这东西刷满了, 那我们就不需要管音频部分怎么怎么样了, 我们只需要聚焦于另外两个模态了。**但是WavLM-Plus 这个模型仍然值得尝试**

> 似乎利用baseline在用clip-large的时候，并没有考虑时序关系 https://chatgpt.com/share/6b3d1d3b-c1f9-425a-be91-70286586dfc5

> 看到去年的冠军也就比baseline好了3个点, 那我们做什么才能比去年的冠军还好呢?
> 1. 多模态大模型的运用
> 2. 融合机制
> 3. 伪标签(去年冠亚的共性), 可能也是一种好的半监督方法
