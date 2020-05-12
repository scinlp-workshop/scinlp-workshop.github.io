# SciNLP: Natural Language Processing and Data Mining for Scientific Text

The 1st SciNLP workshop will be at [AKBC 2020](https://www.akbc.ws/2020/)!  

SciNLP will be held **virtually** on **June 24th** from **8AM - 1PM (PST)**.

The primary goal of this half-day workshop is to bring together researchers from diverse fields
who are interested in extracting and representing knowledge from scientific text, and/or
applications or methods for improving access to and understanding of such knowledge. Such
research includes, but is not limited to:

* **Methods** in natural language processing and data mining for extracting and representing
knowledge from scientific text (e.g. information extraction, entity normalization, discourse
analysis, parsing, summarization, text generation, question answering, knowledge base
construction, weak/distant supervision, crowdsourcing),
* **Applications** of these methods to improving scientific knowledge discovery and/or
understanding (e.g. automated literature review, search and recommender systems,
techniques for data exploration and visualization),
* **Fairness** (e.g. augmented or assistive paper reading, concept simplification, scientific
education and literacy),
* **Science of science** studies (in particular, studies that shed light on phenomena that can
motivate future research in above-mentioned areas), and
* **Datasets**, **Resources** (e.g. treebanks, knowledge bases), and **Tools** (e.g. software
libraries, annotation interfaces) for conducting research in such areas.

We welcome research relevant to processing text in any domain of science (e.g. Biology,
Medicine, Computer Science, Physics, Economics, Sociology, etc.) that can come from a
variety of text sources (e.g. scholarly papers, surveys and technical reports, patents, tweets
by scholars, blogs/tutorials, etc.)

# Call for papers

We welcome submissions of **short abstracts (1 page)** related to the above research areas. Submissions may include previously published results, late-breaking results, work in progress, among other types of scholarly work.  Relevant submissions will be accepted for presentation in the **virtual poster session**.

To submit an abstract, please send an email to **scinlp@googlegroups.com** with the subject line "SCINLP submission: [TITLE]". Please include:
        
* One-page abstract in PDF format as an attachment.  Abstracts will be lightly reviewed to ensure that the topic is within the scope of the workshop.
* Indicate which of the authors will be presenting the work.  We require each accepted work to provide a **~3 minute video** recording of the presentation.  We will reach out with video uploading instructions *after* acceptance notification.  Video length requirements may change depending on the number of submissions.
* Indicate the scientific domain(s) and source(s) of scientific text relevant to the submission; for example, scientific domain could be “Genomics” while source of text could be “Peer-reviewed papers from PubMed”.

**Writing guidelines:**  These abstracts will be longer than the typical abstracts for a full research paper.  Figures and tables are allowed, but will count toward the length limit.  References will *not* count toward the length limit.  We allow abstracts that summarize a collection of works under a unified theme (e.g., a series of closely-related papers that build on each other or tackle a common problem).  For formatting examples, see the accepted abstracts from last year's [SLKB](https://sites.google.com/view/akbc-sci/home#h.p_gSgV1fypJAMf) workshop at AKBC 2019. 

All accepted abstracts (and their videos) will be made available online prior to the workshop and remain accessible afterwards.

If you have a disability and require accommodation in order to fully participate in the workshop, please let us know and we'll be in touch to discuss how we can best address your needs.

**Can't make it?** Check out these other upcoming workshops related to NLP and text mining over scientific text:

* [SDP](https://ornlcda.github.io/SDProc) at EMNLP 2020
* [BioNLP](https://aclweb.org/aclwiki/BioNLP_Workshop) at ACL 2020



# Tentative schedule

The tentative schedule is:

Total estimated 285 minutes (4.75 hrs).  All times are in PST:

* 8:00       - START
* 8:00-8:25  - Invited talk 1 (25 min)
* 8:25-8:50  - Invited talk 2 (25 min)
* 8:50-9:15  - Invited talk 3 (25 min)
* 9:15-9:40  - Invited talk 4 (25 min)
* 9:40-10:05  - Poster session (30 min)
* 10:10-10:35 - Invited talk 5 (25 min)
* 10:35-11:00 - Invited talk 6 (25 min)
* 11:00-11:25 - Invited talk 7 (25 min)
* 11:25-11:50 - Invited talk 8 (25 min)
* 11:50-12:15 - Invited talk 9 (25 min)
* 12:15-12:45 - Panel discussion (30 min)
* 12:45       - END

Each invited talk is roughly 25 min (which includes a few minutes of QA and buffer time for transitions).

# Panel discussion

In light of the activity from the computing community to help with the current virus epidemic, we felt it important to hold a panel discussion on the role of NLP and text mining over scientific text (in particular biomedical literature).  

* What are useful short/long-term endeavors?
* What are we doing that *isn't* helpful?  
* How can we best connect and collaborate with domain experts?
* What are challenges that prevent us from being helpful?

We've invited a few of our speakers who regularly collaborate with biomedical domain experts to share their thoughts and answer questions.

We will be curating questions from the audience beforehand (as well as live during the discussion).


# Invited talks

## [Asma Ben Abacha](https://lhncbc.nlm.nih.gov/personnel/asma-ben-abacha)

**Insights from the Organization of International Challenges on Artificial Intelligence in Medical Question Answering**

Artificial intelligence (AI) is playing an increasingly important role in our access to information. However, a one-fits-all approach is suboptimal, especially in the medical domain where health-related information is more sensitive due to its potential impact on public health, and where domain-specific aspects such as technical language and case or context-based interpretation have to be taken into account. Bridging the gap between several research areas such as AI, NLP, medical informatics, and computer vision is a promising way to achieve reliable and efficient access to medical information. In recent years, I organized several international challenges to promote research efforts in medical question answering. The organization of these competitions raised key questions in data design, evaluation metrics, and problem formulation. It also offered valuable insights on the critical subtasks that need to be solved, and on the most promising solutions in challenging
problems such as restricted training data and multidisciplinary tasks. In this talk, I will share all these insights and the promising perspectives in the addressed tasks, including textual question answering and visual question answering.

*Dr. Asma Ben Abacha is a staff scientist at the U.S. National Institutes of Health (NIH), National Library of Medicine (NLM), Lister Hill National Center for Biomedical Communications. Prior to joining the NLM in 2015, she was a researcher at the Luxembourg Institute of Science and Technology and lecturer at the University of Lorraine, France. Dr. Ben Abacha received a Ph.D. in computer science from Paris 11 University, France, a research master’s degree from Paris 13 University, and a software engineering degree from the National School of Computer Sciences (ENSI), Tunisia. She is currently working on medical question answering, visual question answering, and NLP-related projects in the medical domain.*

## [Doug Downey](https://users.cs.northwestern.edu/~ddowney)

**Mining the Citation Graph for Representation Learning and Concept Extraction**

The exploding pace of scientific publication has led to a pressing need for tools that automatically make sense of the scientific literature.  In this talk, I will describe two recent, simple methods for mining the citation graph to extract meaning from scientific documents.  First, representation learning forms the foundation of today’s natural language processing systems, and large pretrained language models (LMs) like BERT learn powerful representations for short texts like words and sentences.  But, naively applying the models to produce representations for entire scientific documents, which are necessary for many applications, is ineffective.  I will introduce SPECTER, a method for producing scientific document representations using a pretrained LM that is able to achieve state-of-the-art performance by fine-tuning the LM on the citation graph as a signal of document relatedness.  Second, I will describe a new concept extraction technique called ForeCite that uses the intuition that new concepts tend to be introduced or popularized by a single paper.  By mining this signal from the citation graph, ForeCite achieves much higher precision than previous techniques.

*Doug Downey is a research scientist at the Allen Institute for AI, where he works on the Semantic Scholar team, and also an associate professor of Computer Science at Northwestern University.  His research interests involve information extraction, natural language processing, and machine learning, with a particular focus on automatically extracting knowledge from large corpora to powering new search and browsing experiences.  He has won a best paper award at IJCAI, along with an NSF CAREER award, election to the DARPA Computer Science Study Group, and a Microsoft New Faculty Fellowship.*


## [David Jurgens](https://jurgens.people.si.umich.edu)

**Putting a Face on Science: Analyzing Author Mentions in Science Journalism Reveal Wide-Spread Ethnic Bias**

Media outlets play a key role in spreading scientific knowledge to the general public and raising the profile of researchers among their peers.  Yet, given social biases and attention constraints, not all scholars receive equal media coverage.  In this talk, I will describe a large-scale study across hundreds of thousands of news stories that uncovers systematic ethnic bias in which authors journalists mention by name when covering science.  Using NLP techniques to analyze these stories and controlling for confounds, I will show that this ethnic bias is consistent across multiple types of news media, with even larger disparities for long-form journalism focused on science. 

*David Jurgens is an Assistant Professor at the University of Michigan in the School of Information and by courtesy in the Department of Computer Science.  He received his PhD in Computer Science from UCLA. His research in computational social science combines new methods from natural language processing and data science to discover, explain, and predict human behavior in large social systems.*


## [Vivi Nastase](https://www.cl.uni-heidelberg.de/~nastase)

**Looking for the dark matter within knowledge graphs**

Knowledge graphs contain much useful information directly available, but also hidden information that could be leveraged in a variety of ways. Some of this dark matter includes negative instances, missing links, missing nodes and obfuscated patterns. Uncovering and using this hidden information can lead to bigger and more complete graphs, and also to a better understanding of the interaction between structured knowledge in knowledge graphs and unstructured knowledge in text collections. In this talk I will show our exploration of this dark matter in some of the most commonly used KGs -- Freebase, NELL and WordNet -- and discuss how the different nature of each of these graphs influenced our search and what we found.

*Vivi Nastase is a research associate in the Institute for Natural Language Processing at the University of Stuttgart. She obtained a PhD from the University of Ottawa, Canada on the topic of semantic relations. She works mainly on lexical semantics, semantic relations, knowledge acquisition and language evolution, and published about 100 articles on these topics, including a book on "Semantic Relations between Nominals" in the series Synthesis Lectures on Human Language Technologies.*

## [Hoifung Poon](https://www.microsoft.com/en-us/research/people/hoifung)

**Machine Reading for Precision Medicine**

The advent of big data promises to revolutionize medicine by making it more personalized and effective, but big data also presents a grand challenge of information overload. For example, tumor sequencing has become routine in cancer treatment, yet interpreting the genomic data requires painstakingly curating knowledge from a vast biomedical literature, which grows by thousands of papers every day. Electronic medical records contain valuable information to speed up clinical trial recruitment and drug development, but curating such real-world evidence from clinical notes can take hours for a single patient. Natural language processing (NLP) can play a key role in interpreting big data for precision medicine. In particular, machine reading can help unlock knowledge from text by substantially improving curation efficiency. However, standard supervised methods require labeled examples, which are expensive and time-consuming to produce at scale. In this talk, I'll present Project Hanover, where we overcome the annotation bottleneck by combining deep learning with probabilistic logic, and by exploiting self-supervision from readily available resources such as ontologies and databases. This enables us to extract knowledge from millions of publications, reason efficiently with the resulting knowledge graph by learning neural embeddings of biomedical entities and relations, and apply the extracted knowledge and learned embeddings to supporting precision oncology.

*Hoifung Poon is the Senior Director of Biomedical NLP at Microsoft Research and an affiliated professor at the University of Washington Medical School. He leads Project Hanover, with the overarching goal of structuring medical data for precision medicine. He has given tutorials on this topic at top conferences such as the Association for Computational Linguistics (ACL) and the Association for the Advancement of Artificial Intelligence (AAAI). His research spans a wide range of problems in machine learning and natural language processing (NLP), and his prior work has been recognized with Best Paper Awards from premier venues such as the North American Chapter of the Association for Computational Linguistics (NAACL), Empirical Methods in Natural Language Processing (EMNLP), and Uncertainty in AI (UAI). He received his PhD in Computer Science and Engineering from University of Washington, specializing in machine learning and NLP.*

## [Byron Wallace](http://www.byronwallace.com/)

**What does the evidence say? Models to help make sense of the biomedical literature**

How do we know if a particular medical intervention actually works better than the alternatives for a given condition and outcome? Ideally one would consult all available evidence from relevant trials that have been conducted to answer this question. Unfortunately, such results are primarily disseminated in natural language articles that describe the conduct and results of clinical trials. This imposes substantial burden on physicians and other domain experts trying to make sense of the evidence. In this talk I will discuss work on designing tasks, corpora, and models that aim to realize natural language technologies that can extract key attributes of clinical trials from articles describing them, and infer the reported findings regarding these. The hope is to use such methods to help domain experts (such as physicians) better access and make sense of unstructured biomedical evidence.

*Byron Wallace is an assistant professor in the Khoury College of Computer Sciences at Northeastern University. He holds a PhD in Computer Science from Tufts University, where he was advised by Carla Brodley. He has previously held faculty positions at the University of Texas at Austin and at Brown University. His research is in machine learning and natural language processing, with an emphasis on their application in health informatics.*


# Organizers

* Kyle Lo, AI2
* Iz Beltagy, AI2
* Arman Cohan, AI2
* Keith Hall, Google
* Yi Luan, Google
* Lucy Lu Wang, AI2
