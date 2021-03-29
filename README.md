# 2021-GAIIC-phase1-idea

# 2021全球人工智能技术创新大赛赛道一周周星分享

大家好，我是来自重庆邮电大学的lollipop97，很高兴获得了本周的周周星，以下是我在本次比赛中的总结，希望得到大家的指教。

## 模型部分
1.我主要采用的模型是seq2seq多标签分类模型，一般的深度模型都选择将多标签分类转化为了多个二分类问题，而seq2seq模型的优势是可以学习到标签之间的关联程度，来直接对多标签进行预测。

2.seq2seq的上分trick主要尝试了采用强制学习teacher forcing，把真实标签序列在上一个时间步的标签作为解码器在当前时间步的输入。

3.decoder的Attention采用luong_attention和bahdanau_attention，在这里的思路主要参考的[SGM](https://github.com/lancopku/SGM)这篇论文，里面还有一些其他的操作暂时还没有成功实现。

4.最终再和其他的传统深度学习模型，例如textRNN，HAN等模型融合达到了线上的分数。

## 上分的操作
- 送进去的标签按出现频率排序；
- 对decoder的输出进行变形，把常规的一维输出变为17维，然后对17维输出求均值
- 学习率减小
- batch_size减小

## 失败的尝试
- 加入w2v词向量
- 余弦退火
- 换为双向lstm
