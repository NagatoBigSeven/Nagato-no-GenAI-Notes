**Transformers**:
	**编码器(encoder)**:
		**第一步**——**分词(tokenization)**: **字符序列(character sequence)** -**分词器(tokenizer)** e.g. 字节对编码分词器(byte-pair encoding tokenizer, BPE tokenizer)-> **词元序列(token sequence)**
			**词元(token)**: **不包含分隔符(separator)** 的**字符序列(character sequence)**
			n.b. **分词器(tokenizer)无可训练参数(trainable parameter)**
		**第二步**——**嵌入(embedding)**: **词元序列(token sequence)** -**嵌入模型(embedding model)**-> **词元嵌入序列(token embedding sequence)**，理解**词元序列(token sequence)** 中的每个**词元(token)** 的**语义信息(semantic information)**
			n.b. **词元表(token table)** 中的每个**词元(token)** 均有且仅有一个**独特(distinct)** 的**可训练(trainable)** 的**嵌入(embedding)**，即一个**向量(vector)**。**语义(semantic)相近** 的**词元(token)** 的**嵌入(embedding)** 在**潜空间(latent space)** 中的**距离(distance)** 也**相近**
		**第三步**——**位置编码(positional encoding)**: **词元嵌入序列(token embedding sequence)** + **位置嵌入序列(positional embedding sequence)** -> **位置编码的词元嵌入序列(positionally encoded token embedding sequence)**，理解**词元序列(token sequence)** 中的每个**词元(token)** 的**位置信息(positional information)**
			n.b. **词元序列(token sequence)** 中的每个**位置(position)** 均有且仅有一个**独特(distinct)** 的**位置嵌入(positional embedding)**，即一个**向量(vector)**。**位置嵌入(positional embedding)** 既可以是**人造的(man-made)**，也可以是**可训练的(trainable)**
		**第四步**——n $\times$ **Transformer块(Transformer block)** a.k.a. **层(layer)**= **注意力层(attention layer)** + **前馈神经网络(feed-forward neural networks, FFNN)**:
			**注意力层(attention layer)**: **位置编码的词元嵌入序列(positionally encoded token embedding sequence)** -**多头注意力机制(multi-head attention mechanism)**-> 多个**上下文化的词元序列(contextualized token embedding sequence)**，理解**词元序列(token  sequence)** 中的每个**词元(token)** 的**上下文信息(contextual information)**
			**前馈神经网络(feed-forward neural networks, FFNN)**: 多个**上下文化的词元嵌入序列(contextualized token embedding sequence)**-**前馈神经网络(feed-forward neural networks, FFNN)**->，将**注意力层(attention layer)** 中**多头注意力机制(multi-head attention mechanism)** 产生的多个**上下文化的词元嵌入序列(contextualized token embedding sequence)** 整合为一个**上下文化的词元嵌入序列(contextualized token embedding sequence)**
		**第五步**——**输出层(output layer)** = **线性变换(linear transformation)** + **softmax**: 
	**解码器(decoder)**: 

