**大语言模型(large language model, LLM)** 的**本质**是一个能做**文字接龙** i.e. **下一词元预测(next-token prediction)** 的**黑箱(black box)**
**提示词工程(prompt engineering)**:
	There is no need to be polite to LLMs so there is no need to use phrases like "please", "thank you", "if you don't mind", or "I would like to".
	Use affirmative directives like "do" rather than negative languages like "don't".
	把前提给模型(model)讲清楚
	提供给模型(model)一些它不知道的知识
	**上下文学习(in-context learning, ICL)**: 提供给模型(model)一些范例
		**零样本学习(zero-shot learning)**
		**单样本学习(one-shot learning)**
		**少样本学习(few-shot learning)**
	**思维链(chain-of-thought, CoT)**: 让模型(model)思考 "Let's think step by step."
	**情绪勒索(emotional blackmail)**:
		"This is very important to my career."
		"I'm going to tip $20 for a better solution."
		"You will be penalized if..."
	"Ensure that your answer is unbiased and avoids relying on stereotypes."
	将复杂的问题拆解为几个简单的步骤
	让模型(model)解释它的答案: “先给我解释推理过程，再给我答案”
	让模型(model)检查它的答案: “你的答案是否准确？逻辑上是否站得住脚？是否全面？是否遗漏了任何要点？”
	Q: 对于同一个问题，模型(model)每次生成的答案都不同怎么办？
	A: **自洽性(self-consistency)**: 调用模型(model)多次，生成多个答案，以出现次数最多的那个答案为最终答案
	**思维树(tree of thoughts, ToT)**、**思维算法(algorithm of thoughts, AoT)**、**思维图(graph of thoughts, GoT)**...
![[三个提升AI流利度的方法.png]]

**大语言模型(large language model, LLM)训练(training)**/**学习(learning)** 的三个阶段:
	**第一阶段**——**预训练(pre-training)**: **初始参数(initial parameters)** -**大量网络数据**-> **基础模型(foundation model, FM)**/**Base模型(Base model)** e.g. Qwen3-30B-A3B-Base，模型(model)从**大量网络数据**中学习**语言知识(linguistic knowledge)** 和**世界知识(world knowledge)**
		n.b. **从零训练(training from scratch)**(×)，**预训练(pre-training)**(√)
		**数据清洗(data cleaning)**: **内容过滤(content filtering)**: **过滤有害数据** e.g. 色情、血腥、暴力 -> **文本提取(text extraction)** e.g. 去除的HTML标签(tag)、保留项目符号(bullet point) -> **质量过滤(quality filtering)**: **过滤低质量数据** -> **数据去重(repetition removal & document deduplication)** -> **测试集过滤(test-set filtering)**: **确保测试(testing)的严谨性**
	n.b. **预训练(pre-training)** 是一种**自监督学习(self-supervised learning)**
	**第二阶段**和**第三阶段**——**后训练(post-training)** a.k.a. **对齐(alignment)**:
		**第二阶段**——**指令调优(instruction tuning, IT)**/**指令微调(instruction fine-tuning)**: **基础模型(foundation model, FM)**/**Base模型(Base model)** e.g. Qwen3-30B-A3B-Base -**少量人类标注数据**-> **Instruct模型(Instruct model)** e.g. Qwen3-30B-A3B-Instruct-2507，“莫问收获，但问耕耘”
			**路线一**: **微调(fine-tune)一堆专才模型(model)** e.g. BERT (Google, 2018)
			**路线二**: **微调(fine-tune)一个全才模型(model)** e.g. GPT (OpenAI, 2018)
				**挑战(challenge)**: **灾难性遗忘(catastrophic forgetting)**
			**适配器(adapter)**: **固定初始参数(initial parameter)** 并引入**少量可训练(trainable)新参数(parameter)** e.g. LoRA(low-rank adaptation, 低秩适配)
		n.b. **指令调优(instruction tuning, IT)**/**指令微调(instruction fine-tuning)** 是一种**监督学习(supervised learning)**
		**第三阶段——基于人类反馈的强化学习(reinforcement learning from human feedback, RLHF)**: **Instruct模型(Instruct model)** e.g. Qwen3-30B-A3B-Instruct-2507 -> 最终模型 e.g. Qwen3-30B-A3B，“莫问耕耘，但问收获”
			Q: 为什么需要基于人类反馈的强化学习(reinforcement learning from human feedback, RLHF)?
			A: 指令调优(instruction tuning, IT)/指令微调(instruction fine-tuning)所需的人类标注数据很难获得；对于某些问题，虽然人类(human)很难给出正确答案，但是很容易判断一个答案的好坏；指令调优(instruction tuning, IT)/指令微调(instruction fine-tuning)的每一步最优的策略不一定导出全局最优
			**回馈模型(reward model, RM)**: 用于模拟真实人类(actual human)喜好的“虚拟人类”
				**问题(question)** -**大语言模型(large language model, LLM)**-> **答案(answer)**
				**问题(question)** + **答案(answer)** -**回馈模型(reward model, RM)**-> **分数(score)**
				**safety** v.s. **helpfulness**
			**直接偏好优化(direct preference optimization, DPO)**、**KTO(Kahneman-Tversky optimization, KTO)**、**基于AI反馈的强化学习(reinforcement learning from AI feedback, RLAIF)**...
**测试(testing)**/**推理(inference)**

**工具调用(tool calling)**:
	**检索增强生成(retrieval augmented generation, RAG)**: 让模型(model)**调用搜索引擎(search engine)联网搜索** 或**查询数据库**
	**思维程序(program of thoughts, PoT)**: 让模型(model)**写代码** 并**执行代码**
	**图像生成(image generation)**: 让模型(language model, LM)**调用文生图模型(text-to-image model)**

**多智能体协作(multi-agent collaboration)**:
	用**合适的模型(model)** 做**合适的任务(task)**
	**多智能体辩论(multi-agent debate)**: 让模型(model)互相讨论
	Q: 讨论何时终止?
	A: 引入**裁判模型(referee model)**
	引入不同的**角色(role)**:
		不同的模型(model)本身就有不同的专长
		通过系统提示词(system prompt)设定模型(model)的角色(role) “你是一个猫娘。”
	让**裁判模型(referee model)** 给**其他模型(other models)** 的表现打分