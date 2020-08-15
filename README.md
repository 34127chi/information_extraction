# information_extraction
信息抽取

## 基本知识：
- crf与hmm之间的关系：https://zhuanlan.zhihu.com/p/70067113 两者之间的不同（生成式、判别式）
- bilstm + crf中crf层的理解：https://zhuanlan.zhihu.com/p/44042528 如何学习句子中的约束关系、损失函数以及解码过程（维特比算法）
- 中文NER任务实验小结报告：https://zhuanlan.zhihu.com/p/103779616 从非bert类到bert类方法 代码地址：https://github.com/qiufengyuyi/sequence_tagging
  - 总结：1）一般是基于字的训练标注 如何加入词的信息 例如可以直接将词的embedding加在字的embedding上 还有就是像lattice lstm 2）mrc（机器阅读理解）框架下的实体识别 首先对每种标签构造query当作先验知识 最后以构造的query以及原始文本作为阅读理解任务

## 具体的应用/比赛：
- 2019语言与智能技术竞赛--信息抽取（三元组）
  - baseline方案：实体识别 =》 实体关系预测
  - 基于概率图方案：先预测subject 再同时预测object和predicate 具体参考：https://spaces.ac.cn/archives/6671
      - 总结：字词的混合embedding、半指针-半标注结构、conv1d结构（多通道传输）、远程监督

- 2020语言与智能技术竞赛--事件抽取（事件类型、事件角色、论元）
  - 官方baseline:Pipelined的方法 即基于序列标注方法先进行事件检测(ed) 然后进行论元的识别来完成事件抽取
  - 建模成普通的序列标注 具体参考：https://kexue.fm/archives/7321 
    - 注：建模方式优雅
  - 两段式 事件类型=》基于mrc的事件角色预测 具体参考：https://zhuanlan.zhihu.com/p/141237763 
    - 注：将标签作为作为外部信息加入以及基于mrc框架
  - 两段式 相对1） 第二阶段考虑只识别事件对应的论元


