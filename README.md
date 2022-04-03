# Papers for Event Extraction
Papers from top conferences and journals for event extraction in recent years.


# Table of Contents
<summary><b>Table of Contents</b></summary><blockquote><p align="justify">

- [Classification-based](#Classification-based)
- [Generation-based](#Generation-based)
- [QA-based](#QA-based)
- [Augmentation](#Augmentation)
</p></blockquote>




## Classification-based

**A Joint Neural Model for Information Extraction with Global Features.** 
_Ying Lin, Heng Ji, Fei Huang, Lingfei Wu_ [ACL2020](https://www.aclweb.org/anthology/2020.acl-main.713) 
> Keywords: End-to-End, graph, joint-optimization
> 
> Proposed unified ONEIE framework that performs entity, relation and event extraction. Extract globally optional result as a graph from an input sentence by incorporate *global features* and *beam decoder*.
> 
> global feature helps to capture cross-subtask interactions (between entities, relations and events) and cross-instance interactions (between multiple event and/or relation instances in the sentence)

**Biomedical Event Extraction with Hierarchical Knowledge Graphs**
_Kung-Hsiang Huang, Mu Yang, Nanyun Peng_ [EMNLP2020 Finding](https://www.aclweb.org/anthology/2020.findings-emnlp.114)
> Keywords: biomedical, used gold-entity, graph, joint-optimization, knowledge-based
> 
> Proposed Graph Edge-conditioned Attention Networks (**GEANet**) that incorporate **domain knowledge** to PLMs via hierarchical graph representation encoded by it, GEANet updates the token node embedding via corresponding sentence graph.
> 
> Challege: challenging to identify adjective triggers because it is less common and ofen cannot be linked with UMLS comcept; misleading triggers: triggers providing clues about incorrect event
> KG provides clues for identifying the trigger and corresponding arguments through reasoning path

**Cross-lingual Structure Transfer for Zero-resource Event Extraction**
_Di Lu1, Ananya Subburathinam, Heng Ji, Jonathan May, Shih-Fu Chang, Avirup Sil, and Clare Voss_ [LREC2020](https://aclanthology.org/2020.lrec-1.243)
> Keywords: cross-lingual, graph, zero-shot
> 
> Developed a share-and-transfer framework that can transfer graph structure across languages to tackle with cross-lingual event extraction. _sentence -> universal language graph (dependency tree and fully connected graph for edges) (cross-lingual word embedding for nodes) -> mapping latent word representation to event types and argument roles through FNN and Softmax_
> 
> Train event extractor on English and apply on other languages

**Joint Extraction of Events and Entities within a Document Context**
_Bishan Yang, Tom Mitchell_ [NAACL2016](http://aclweb.org/anthology/N16-1033)
> Keywords: feature engineering, joint-optimization
> 
> Proposed unified model to jointly extract both event and entities in document level; jointly inference three local models (_within-event structure (probabilistic model); event-event relation (pairwise model with hand-engineered features); entity extraction (CRF)_) to extract coherent event and entity
> 
> Error Analysis: missing triggers; missing arguments due to wrong entity type
> 
> Thought: restrict the entity type may help argument extraction; jointly optimize entity identification and classification with argument extraction and role labeling; some trigger words were never seen during training; complex languages are misleading, infuse background knowledg may be helpful

**Query and Extract: Refining Event Extraction as Type-oriented Binary Decoding**
_Sijia Wang, Mo Yu, Shiyu Chang, Lichao Sun, Lifu Huang_ [ACL2022](http://arxiv.org/abs/2110.07476)
> Keywords: embedding, attention mechanism
> 
> Proposed framework in query-and-extract paradigm that leverages semantics of event types (event type representation) and argument roles (argument role query) 
> 
> Trigger detection: word contextual embedding, in-context representation, event type aware contextual representation, POS tag encoding
> 
> Argument detection: trigger-aware entity embedding + argument embedding -> multiway attention -> argument role aware contextual representation, entity-aware contextual representation, relation amoung entities, relation among argument roles
> 
> Thought: make use of the event type representation (prototype triggers) for trigger detection


## Generation-based

**DEGREE: A Data-Efficient Generative Event Extraction Model**
_I-Hung Hsu, Kuan-Hao Huang, Elizabeth Boschee†, Scott Miller, Prem Natarajan, Kai-Wei Chang, Nanyun Peng_ [arxiv](http://arxiv.org/abs/2108.12724)
> Keyword: prompt, end-to-end
> 
> Proposed DEGREE that takes the original passage and a set of prompts (predefined based on event type) as input and generate template-based text so that the trigger word and arguments can be easily extracted/decoded from the output text. The template can probide ontology information of the event.
> 
> *need to know the event type first as the prompts are event based*
> 
> Advantage: models **label semantics** (event role description), **output dependencies** (extract trigger and argument as once) and **event structure** (expressive prior) 

**Document-Level Event Argument Extraction by Conditional Generation (BART-Gen)**
_Sha Li and Heng Ji and Jiawei Han_ [NAACL2021](http://arxiv.org/abs/2104.05919)
> Keywords: document-level, argument extraction, prompt/template, end-to-end
> 
> Proposed document-level event argument extraction model that generates output by fill in template (special token "tgr" to identify trigger in document, and "arg" as placeholders in template) with arguments, tackle with the coreference issue by prioritise longest name mention over nominal mentions and pronouns. Applied clarification statements to add entity type constraints on arguments based on their role. The triggers are extracted through sequence labeling.

**Generating Disentangled Arguments with Prompts: A Simple Event Extraction Framework that Works (GDAP)**
_Jinghui Si, Xutan Peng, Chen Li, Haotian Xu, Jianxin Li_ [ICASSP 2022](http://arxiv.org/abs/2110.04525)
> Keywords: prompt, negative sampling
> 
> GDAP architecture contains three models (ETD, TrgE, and ArgE). ETD learn to encode the raw sentence and decode its event types using **Parenthesis Representation** ((ET1)(ET2)...(ETi)...(ETx)). After event type been predicted, TrgE extract the trigger words by input in a prompt that is formed by event type and sentence in the format of "ET_i</s>Sent", output represented in the same way as ETD -> ((Trg1 )(Trg2 )⋯(Trgy )). With trigger words been extracted, the prompt for ArgE is created in the format of "ET_i</s>RTij</s>Sent", expected outputs is ((Trg1 )(Trg2 )⋯(Trgy ))
> 
> tire-based constraint decoding algorithm is applied to guarantee the token validness
> 
> introduced negative sampling mechanism to train TrgE and ArgE, which is to randomly select N event types that have not appeared in the Sent and expect the model to learn to only generate empty sequence
> 
> Thought: remove irrelevant sentences in the document imrpoves the extraction performance

**Multilingual Generative Language Models for Zero-Shot Cross-Lingual Event Argument Extraction (X-GEAR)**
_Kuan-Hao Huang∗† I-Hung Hsu∗‡ Premkumar Natarajan‡ Kai-Wei Chang† Nanyun Peng_ [ACL2022](http://arxiv.org/abs/2203.08308)
> Keywords: cross-lingual, prompt, giben-trigger
> 
> Proposed X-GEAR that takes the passage and prompt containing event trigger and language-agnostic template as input to generate output by fill in the template with event arguments. Language-agnostic template is created using special tokens to represent argument role type
> 
> Thought: not end-to-end event extraction

**Structured Prediction as Translation between Augmented Natural Languages (TANL)**
_Giovanni Paolini, Ben Athiwaratkun, Jason Krone, Jie Ma, Alessandro Achille, Rishita Anubhai, Cicero Nogueira dos Santos, Bing Xiang, Stefano Soatto_ [ICLR2021](http://arxiv.org/abs/2101.05779)
> Keywords: augmented language translation, unified model
> 
> Unified model that can work on entity and relation extraction, semantic role labeling, coreference resolution. Event extraction is done by first extract trigger, then extract arguments. The trigger word and event type will be added to the output sentence "... \[trigger_word | event_type\] ...". Same for argument but with trigger words mentioned "... \[entity | type | role_type = trigger \] ..."
> 
> Thought: coreference can be treated while extracting trigger and arguments

**Text2Event: Controllable Sequence-to-Structure Generation for End-to-end Event Extraction**
_Yaojie Lu, Hongyu Lin, Jin Xu, Xianpei Han, Jialong Tang, Annan Li, Le Sun, Meng Liao, Shaoyi Chen_ [ACL2021](http://arxiv.org/abs/2106.09232)
> Keywords: event schema, controlled generation, end-to-end, curriculum learning
> 
> TEXT2EVENT is a sequence-to-structure network that directly generate event schemas and text spans to form event records (in lineralized format) via constrained decoding (trie-based constrained decoding). Event schema knowledge is injected as prompt to the decoder fir valid event structure generation.

## QA-based

**Biomedical Event Extraction as Multi-turn Question Answering**
[paper](https://www.aclweb.org/anthology/2020.louhi-1.10)

**Event Extraction as Machine Reading Comprehension**
[paper](https://www.aclweb.org/anthology/2020.emnlp-main.128)

**Event Extraction as Multi-turn Question Answering**
[paper](https://www.aclweb.org/anthology/2020.findings-emnlp.73)

**Event Extraction by Answering (Almost) Natural Questions**
[paper](http://arxiv.org/abs/2004.13625)


## Augmentation

**Automatically Labeled Data Generation for Large Scale Event Extraction**
_Yubo Chen, Shulin Liu, Xiang Zhang, Kang Liu and Jun Zhao_ [ACL2017](http://aclweb.org/anthology/P17-1038)
> Keyword: classification-based EE approach; Soft Distance Supervision
> 
> Automatically generate EE data by jointly using world knowledge (Freebase) to prioritize arguments and select key or representatives and linguistic knowledge (FrameNet) to filter noisy triggers and expand more triggers; label event extraction data by detecting key arguments and trigger words for each event type and employ them to label events in the text.
> 
> Distant Supervision method assumes that if two entities have a relationship in a known knowledge base, then all sentences that mention these two entities will express that relationship in some way.






