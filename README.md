# NER-pytorch
公开一个NER的pytorch模型实现, 有需要自取, Bi-LSMT-CRF

### Bi-lstm-crf baseline in pytorch
这个模型用来做命名实体识别

torch tutorial 给了bi-lstm-crf做ner的例子,不过是基于cpu运行的
> https://pytorch.org/tutorials/beginner/nlp/advanced_tutorial.html

### gpu修改
这里在tutorial的基础上,将代码改成了gpu运行,并采用[boson数据集进行验证](https://bosonnlp.com/dev/resource)

[修改过程部分参考这个文档](https://blog.csdn.net/qq_28444159/article/details/78781201)

然后自己还改了很多东西  

比如对于继承了`nn.model`的模型,直接在`train.py`对model用上`.to(device)`就行

### 平台
- Ubuntu 16.04
- 1080ti
- python3.7

### requirements
- python3.7
- pytorch='1.0.1.post2'
- numpy='1.16.2'

### usage
- 运行`data/data_util.py`工具,处理出pickle数据并保存
- 读取pickle为numpy,转换为tensor,然后带入官方的tutorial,注意已经改成gpu了
- 训练接口是`pytorch/train.py`

### 训练时间
我觉得比单纯cpu就快了一点点...没有特别大改进..猜想是因为lstm跟rnn一样也是一个序列化模型,跑并行效果并不明显

### 结构
```
 pytorch/
   BiLSTM_CRF.py 模型
   train.py boson数据集
   raw_train.py tutorial的测试例子
 data/
   data_util.py 
```


### tensorflow版本
晚点会补上,并加上与其他几个模型的F-score对比

### 参考
> [写的很好的原始中文pytorch版本](https://github.com/buppt/ChineseNER)  
> [python改为3的tensorflow版本](https://github.com/WenRichard/NER-TF/tree/master/NER-Chinese-BiLSTM%2BCRF)  
> [RNN做NER, in tf](https://github.com/zjy-ucas/ChineseNER)  
> [bert-bilstm-crf-ner in tf](https://github.com/macanv/BERT-BiLSTM-CRF-NER)
