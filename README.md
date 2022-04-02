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
> Proposed unified ONEIE framework that performs entity, relation and event extraction. Extract globally optional result as a graph from an input sentence by incorporate *global features* and *beam decoder*.
> global feature helps to capture cross-subtask interactions (between entities, relations and events) and cross-instance interactions (between multiple event and/or relation instances in the sentence)

**Biomedical Event Extraction with Hierarchical Knowledge Graphs**
_Kung-Hsiang Huang, Mu Yang, Nanyun Peng_ [EMNLP2020 Finding](https://www.aclweb.org/anthology/2020.findings-emnlp.114)
> Keywords: biomedical, used gold-entity, graph, joint-optimization, knowledge-based
> Proposed Graph Edge-conditioned Attention Networks (**GEANet**) that incorporate **domain knowledge** to PLMs via hierarchical graph representation encoded by it, GEANet updates the token node embedding via corresponding sentence graph.
> Challege: challenging to identify adjective triggers because it is less common and ofen cannot be linked with UMLS comcept; misleading triggers: triggers providing clues about incorrect event
> KG provides clues for identifying the trigger and corresponding arguments through reasoning path

**Cross-lingual Structure Transfer for Zero-resource Event Extraction**
_Di Lu1, Ananya Subburathinam, Heng Ji, Jonathan May, Shih-Fu Chang, Avirup Sil, and Clare Voss_ [LREC2020](https://aclanthology.org/2020.lrec-1.243)
> Keywords: cross-lingual, graph, zero-shot
> Developed a share-and-transfer framework that can transfer graph structure across languages to tackle with cross-lingual event extraction. _sentence -> universal language graph (dependency tree and fully connected graph for edges) (cross-lingual word embedding for nodes) -> mapping latent word representation to event types and argument roles through FNN and Softmax_
> Train event extractor on English and apply on other languages

**Joint Extraction of Events and Entities within a Document Context**
_Bishan Yang, Tom Mitchell_ [NAACL2016](http://aclweb.org/anthology/N16-1033)
> Keywords: feature engineering, joint-optimization
> Proposed unified model to jointly extract both event and entities in document level; jointly inference three local models (_within-event structure (probabilistic model); event-event relation (pairwise model with hand-engineered features); entity extraction (CRF)_) to extract coherent event and entity
> Error Analysis: missing triggers; missing arguments due to wrong entity type
> Thought: restrict the entity type may help argument extraction; jointly optimize entity identification and classification with argument extraction and role labeling; some trigger words were never seen during training; complex languages are misleading, infuse background knowledg may be helpful

**Query and Extract: Refining Event Extraction as Type-oriented Binary Decoding**
_Sijia Wang, Mo Yu, Shiyu Chang, Lichao Sun, Lifu Huang_ [ACL2022](http://arxiv.org/abs/2110.07476)
> Keywords: embedding, attention mechanism
> Proposed framework in query-and-extract paradigm that leverages semantics of event types (event type representation) and argument roles (argument role query) 
> Trigger detection: word contextual embedding, in-context representation, event type aware contextual representation, POS tag encoding
> Argument detection: trigger-aware entity embedding + argument embedding -> multiway attention -> argument role aware contextual representation, entity-aware contextual representation, relation amoung entities, relation among argument roles
> Thought: make use of the event type representation (prototype triggers) for trigger detection


## Generation-based

**DEGREE: A Data-Efficient Generative Event Extraction Model**
[paper](http://arxiv.org/abs/2108.12724)

**Document-Level Event Argument Extraction by Conditional Generation**
[paper](http://arxiv.org/abs/2104.05919)

**Generating Disentangled Arguments with Prompts: A Simple Event Extraction Framework that Works**
[paper](http://arxiv.org/abs/2110.04525)

**Multilingual Generative Language Models for Zero-Shot Cross-Lingual Event Argument Extraction**
[paper](http://arxiv.org/abs/2203.08308)

**Structured Prediction as Translation between Augmented Natural Languages**
[paper](http://arxiv.org/abs/2101.05779)

**Text2Event: Controllable Sequence-to-Structure Generation for End-to-end Event Extraction**
[paper](http://arxiv.org/abs/2106.09232)


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
> Automatically generate EE data by jointly using world knowledge (Freebase) to prioritize arguments and select key or representatives and linguistic knowledge (FrameNet) to filter noisy triggers and expand more triggers; label event extraction data by detecting key arguments and trigger words for each event type and employ them to label events in the text.
> Distant Supervision method assumes that if two entities have a relationship in a known knowledge base, then all sentences that mention these two entities will express that relationship in some way.






