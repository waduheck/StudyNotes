BERT是用了Transformer的encoder侧的网络，encoder中的Self-attention机制在编码一个token的时候同时利用了其上下文的token，其中‘同时利用上下文’即为双向的体现，而并非想Bi-LSTM那样把句子倒序输入一遍。
https://www.jiqizhixin.com/articles/2019-11-05-2
https://paddlepedia.readthedocs.io/en/latest/tutorials/pretrain_model/bert.html

但是作者认为其并未充分利用句子的语言结构。利用语言模型在一系列的词语和句子找到最佳排列是NLP任务的本质，例如机器翻译，基于此，作者提出了一种新型的上下文表示模型，StructBERT。StrucBERT分别利用在句子中和句子间增加结构信息，词序(word-level ordering)和句序(sentence-level ordering)来增强模型的预训练，这样在预训练上可以明确捕获语言方面的内容，可以在上下文表示中对句子和单词之间的依存关系进行编码表示，增强了模型的通用性和适用性。