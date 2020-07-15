# SciNLP 2020 Invited Speaker Q&A

This is a transcript of questions and answers for our invited speakers.  We recorded conversations on both Rocket Chat and Zoom.  We've edited typed questions/answers that contained typos or grammatical errors, but tried to remain faithful to the original content.  We've also transcribed answers to questions that were given live during the presentation (so there might be some mistakes).  Please let us know if anything in here is incorrect!

In speaker order:
* [Ryan McDonald](#ryan-mcdonald)
* [Vivi Nastase](#vivi-nastase)
* [David Jurgens](#david-jurgens)
* [Robert Stojnic](#robert-stojnic)
* [Iris Shen](#iris-shen)
* [Doug Downey](#doug-downey)
* [Hoifung Poon](#hoifung-poon)
* [Asma Ben Abacha](#asma-ben-abacha)
* [Byron Wallace](#byron-wallace)
* [Panel with Asma, Hoifung, and Byron](#panel)

# Ryan McDonald

### Zoom chat

Q1: "Do you generate questions at different passage granularities? I imagine the types of questions generated at a document level would be quite different from something generated at a sentence level for example."

A1 (live): Right now, we basically divide documents into sections.  And we generate questions at the whole-section level - so abstract, intro, etc..  And we generate questions at the sentence-level, as well.  Since it's a lot of questions, we've experimented with using IDF weights to pick which sentences are more content-full.  So far, we've found that much of that hasn't really affected the quality of the neural model.

Q2: "Could you comment further on entity linking and discovery, and its impact on QA in Scientific Literature?"

A2 (live): I'll comment on what we've experimented with.  When you ask questions like 'What regulates the Warburg effect?', which is our prototypical question since it has a lot of nice properties: (1) you have to understand the predicate-argument structure to make sure you get the right answer (2) more interestingly, there are a lot of things that regulate it.  What we've found is that, in order to show users useful results, a very effective solution is to look for answers - parts of the document that answer the question - link that to ontologies, and then cluster by those linkages - doing a hard cluster (i.e., everything linking to the same node in the ontology is in the same cluster) - and show results that way (by entities as opposed to a list of documents).  In qualitative feedback, we've been told that's a very useful thing to do, but I don't have any quantiative UX studies on that front.


### Rocket chat

Q1: “Could to talk a bit more about the effect of the datasets and why there was a large performance difference on the TREC-COVID data vs BioASQ?”

A1: “NDCG@10 for the two datasets is comparable. However, the questions in TREC-COVID are a bit more general, so there is a larger number of relevant documents on average.”


Q2: “I would like to know a bit more about the performance differences across bioASQ and TREC-covid, the neural methods perform significantly better on TREC.”

A2: “We think that the neural models also perform better (or at least on par) for BioASQ as well, but the data is skewed to questions that can be answered with term matches. However, there are many cases where BM25 is clearly better, which is why we moved to the hybrid model.”
 
Q3:  “Is Google working on products with biomed QA or is this isolated research?”

A3:  “We are working on better discovery from scientific literature. Biomed is an obvious place to start given the size of the problem as well as the investment the community has made in resources.”

 
Q4: "Are the codes/publication of your work available publicly?"

A4: “We don't have a GitHub, but all the resources we use are basically public, including our question generator and the data plus all the eval data. The nearest neighbour backend is not open sourced, but Facebook’s Faiss library would work.  Stay tuned to up-coming papers.”
 
Q5: “Will this be new functionality in Google Scholar?”

A5: “Too early to say. Those decisions are above my pay-grade 🙂”

### Unanswered

Zoom: "Is there a reason that you focused on biomedical literature, vs. for instance physics or chemistry?"



# Vivi Nastase

### Zoom chat

Q1: "Curious whether there would be special considerations in other domains?"

A1 (live): We haven't on any domain-specific knowledge graph, but the code for any of these things is online.  So if anybody is interested in trying it out, then it's there.  We only thought about our own narrow interests - this ACL graph that we're trying to build - but we haven't gotten there. I think we should try it out. 

### Rocket chat

Q1: “Did you say that you tried to use the ACL Anthology for your experiments at some point but had problems?”

A1: “We are still working on extracting specific information from the ACL collection -- connecting NLP problems with their solutions -- but, unsurprisingly, it's hard. So that part is still under construction.”

Q2 (follow-up; rephrased): “Have you used the ACL ARC v2 has OCRed and parsed versions of the anthology?”

A2: “We work with the OCR-ed, and even did some word segmentation correction there, but it's hard to extract a nice and clean path from the problem to the solution, which is what we are after. But we'll persist!”


# David Jurgens

### Zoom chat


Q1: "What are the topics that journalists cover without mentioning authors?"

A1 (live):  It's actually a lot.  A lot of it has to do with food and health.  So like "Chocolate cures cancer" and it's like "Researchers at blablabla have found that eating so much chocolate will improve something" but they don't actually cite the particular study.  I don't think we've seen / we didn't dig too much into the topics there.

Q2: "Have you considered communication barriers? (perhaps foreign authors tend to respond less to journalists)"

A2 (live):  Yeah, we tried to get at that whether the author's home institution is in the US or out of the US to control for this.  All of the authors are writing English-language papers, so it's not like they're not fluent in English to some degree. We didn't see any strong effect there either.  But yeah, maybe fluency is playing a role in this.

Q3: "Any thoughts on the origin of this bias? Is it the journalists ignore these minority authors or is it a discoverability issue (e.g. search engine bias)?"

A3 (live):  I don't think it's the journalists.  We didn't see anything systematic in terms of the journalist.  We also manually coded them for ethnicity for the most prolific journalists. We are controlling for the journal/venue itself, so it should at least normalize for discoverability across different venues.

**Comments from audience:**

Lucy: "Foreign institutions may not have press offices that are well connected to these news outlets though."

Yoav: "Authors who publish in English are most definitely not necessarily fluent in English!"

David's repsonse: "Fully agree Yoav and Lucy! I do think that lots of journalists initially communicate via email which might be easier for less fluent authors though (that said, controlling for this better is something we’re looking at)"

### Unanswered

Zoom: "Random effects for journalists?"

Zoom: "Are the news outlets primarily located in us/canada and northern european countrys?"



# Robert Stojnic

### Zoom chat

Q1: "Is "papers with code" in your view meant primarily for academic researchers or for industry researchers?"

Q2: "How do you link entities of tasks from each paper? (Is the information easy to download for the public? i.e. is it within one of the three available download links in the about section?)"

Q3: "Is the focus on equating tasks with scores on datasets good or bad for DL-science in the long run?"

Q4: "At any point do you envision your platform (since you have both code and the paper) where one might interactively play with the parameters and see results in relation to the rest of the results / papers you index.. sort of live experiments where possible?"

Q5: "Are components of this platform open, and can people adapt them for other collaborative efforts around paper extractions, maybe for results in other domains?"

Q6 (follow-up from another audience member): "+1 and also, is the data (papers + extracted results) available for e.g. creating a dataset for training supervised extraction?"

Q7: "The new accessibility standards for PDF require rather strict formatting of tables for the software for visually challenged users to read them.  Do you plan to use this formatting when available?"


**More comments from audience:**

Jodi: "Thanks for baking licensing in! :)"


# Iris Shen

### Zoom chat

Q1: "How does MAG discard (if it does!) articles of dubious standing (say pseudoscience or extremely controversial content) from its publication index?"

A1 (live): For low-quality content, we actually leverage some external/whole web information by calling the Bing API to see if the top results are really coming from more prestigious/reputable domains, and we'll do classification from there.

### Unanswered questions

Zoom: "With the increased availability of full-text open access articles, will it be possible for MAG to parse the entirety of the content in articles (not only abstracts)? Is it expected to reduce the number of orphan fields of study?"

Zoom: "What about a new concept clusters / trees?  As in, a group of new concepts can arise all at once.  How does the algorithm handle cases like this? Some may be leaf nodes of other new concepts..."

Zoom: "Is BERT-Large performing better than AllenAI models (SciBERT and siblings) for MAG?"



# Doug Downey

### Zoom chat

Q1: "Could you please explain more how the input of the pretrained transformer is represented ? every paper is represented as a sentence with |SEP| between the three papers?"

Q2: “Why does Pretrained Transformer perform poor given that Abstract, Title and Conclusion are information dense?”

A2 (live):  The story is really that document-level semantics is kind of a different end point than his within-document masked language model objective that the pretrained Transformer is trained on.  So it's not aimed at producing a single embedding that captures the semantics of the whole passage.  At least, not in the sense that we were consuming it in the paper-embeddings tasks.  I don't have a great reason for why it's true; I was a little surprised by how bad it was.  I'm still a little puzzled by that result, but it's really the difference between the document-level topic objective and the token-level masked language model objective that drives a lot of it.

Q3: "The scientific concepts extraction algorithm is very cool! How domain-independent do you think the heuristic is?  Will it work on Bio/Chem/Phys as well as on CS?"

A3 (live):  I would think/hope that it's fairly domain-independent since it's fairly simple (it just uses the citation structure).

Q3 (follow-up; clarification): "I guess the question is "is the citation structure in CS and other fields similar"

A3 (DanielKing continued answer live):  So we did a little bit with the PubMed corpus (and ran it on the CORD-19 corpus) and there are certainly some differences in the citation structure (CS has this tendency to name stuff that isn't necessarily present in their field), but the top concepts looked to be similar precision in Bio, which is the other domain.  Haven't tried other domains.  Definitely there are citation pattern differences across fields.



### Rocket chat



Q1 (repeat from Zoom): “Why does Pretrained Transformer perform poor given that Abstract, Title and Conclusion are information dense?”

A1 (chat): “You're right that the raw semantic content needed to represent the paper well is there (btw we use just title+abstract, not conclusion, but the point remains the same). The problem is that the embeddings output by the off-the-shelf transformer didn't tend to capture that document-level information well, in our experiments. Finetuning the transformer on the citation objective helps ensure that the document-level semantics ends up in the embeddings.”

Q2: “How would AI2's Longformer (https://github.com/allenai/longformer) fare on the tasks in the table in which SPECTER was compared to baselines?"

A2: “Good question, we are working on this now -- stay tuned 🙂. I think it would help, in particular Longformer would allow us to easily use the text of the paper references, which I expect will be very valuable for our tasks.”

**Comments from audience about Q1**

Lingfei: "My quick guess on Sidhu’s question: Unlike other domains, science is all about using the same terminology to talk about new ideas. Citation is expert-label data on the hidden association between ideas, which may or may not be easily recognized by machines."

**More comments from audience**

Samuel: "by Stigler's Law: typically everyone cites the *second* paper ;)"

Anita: "Acronym identification will be a core requirement for future summarization tools"

Marti: "I like the simplicity of the SPECTER approach; really neat!"



# Hoifung Poon

### Zoom chat

Q1: "KBs can also contradict one another (esp since some are more up to date). What's the effect of this when using them for distant supervision? Do you prioritize relationships that are more trustworthy?"

A1 (in-chat): "Excellent question! That's partially the motivation for deep probabilistic logic. We want to be able to express and reason such prior belief about the quality of prior knowledge. It's straightforward to do. We are also extending DPL with the capability to propose new self-supervision, which can be directly added to the model or vetted by experts (as in feature-based active learning). The initial results are very promising."

**More comments from audience**

Lucy: "exchange coffee for knowledge :D"

### Rocket chat

Q1: “Would it be conceivable to ask to article authors to provide curated propositions to help/benchmark the creation of KBs? Do standards exists for this?”

Q2 (related): “Authors are currently required to provide "keywords" when submitting articles. Would it make sense to start requiring "triplets" of connected concepts (or something of that kind?) What would be the most useful (but easy to produce) data format?”

A1-A2: “That's a standard question I have been asked for many years 🙂 Short answer is that it's easy to collect some high-level meta data, but hard to collect all valuable info. There are many relations of interest, some not even high on the mind of the authors, but useful for specific use cases. It's hard for authors to anticipate all of them, and it can quickly devolve into a super heavy curation burden. For comparison, Semantic Web started by trying to do something similar for the Web, but quickly retreated from the original goal as it was hardly attainable.”

Q3: “Is the new benchmark of NLP tasks on biomedical domain that you mentioned, released?”

A3: “Yes, we plan to release the benchmark and our Pubmed BERT model by early July. Stay tuned 🙂”
 
Q4: “You mentioned how the current sweet spot of NLP is to empower curators with super speed using NLP technologies to reduce their effort and the size of their search space. What are some of the most data resources that you think need to be curated in this space?”

A4: “The top two sources are Pubmed and EMRs, as mentioned in the talk. There are many impactful use cases. We are currently focusing on precision health, esp. oncology as the beachhead area, but many are also so tempting, like microbiome, immunology, etc.”
 
Q5 (follow-up):  “I'm specifically interested in the efforts you mentioned about feature-based active learning. How are you going about identifying relevant features? Is it simply creating a network that proposes labeling functions?”

A5: “We have a paper submission that explains all that. Hopefully it will be accepted 🙂 Briefly, we can introduce general self-supervision templates, and the problem becomes one of structure learning. In our preliminary experiments, we find that even simple templates go a long way in reducing manual effort in defining self-supervision (or labels).”
 
Q6: “Do you (or anyone interested) think the amount of human curation needed can be modeled?  When we are doing annotation work in our research, we found that the amount of human curation work goes far beyond our expectation, thus we have been thinking the way to foresee that, by modeling it, or modeling proxy/key factors for getting some insights.”

A6 (partially on Zoom): "Sure. There are a lot of opportunities to gradually shift more and more of human burden to machine reading. E.g., we start with (drug, gene, mutation) relation, and now are adding cancer type, evidence type, and other info human experts use for their curation."

A6 (partially on Rocket): “One thing we find helpful is to break down the annotation task into 80/20 stages. Often, finding the core facts is the most time-consuming part, which is what we start with, e.g., drug-gene-mutation for molecular tumor board. And then we keep identifying the next 80/20 opportunities for assisted curation.”

Q7: “What do you think of full-text vs. title & abstract? Will full-text mining availability always help? There are definitely more data in full-text but also probably more noise that may confuse the algorithm. Do you have an experience with that?”

A7: “Full text is basically mandatory. E.g., most mutation-level results are not present in abstracts. As a rule of thumb, the most details and nuanced info you are looking for, the more you need full text. Like you said, full text is much noisier, with more complex structures, which is why we are pushing on cross-sentence or document-level relation extraction.”
 
Q8: “It's nice to consolidate the labeling functions / sources of supervision via graphical models. Could you comment on the efficiency/scalability aspect of this approach?”

A8: “Yes. In deep probabilistic logic, we use graphical model for modeling self-supervision, which is in a reduced state space (latent labels), so even standard methods like belief propagation work reasonably well. The end-to-end training uses variational EM, which generally converges after 2-3 iterations.”


# Asma Ben Abacha

### Zoom chat

Q1: "Can you talk a bit more about consumer health QA and the goals of the NIH around this?  Whether there are public-facing goals?"

Q2: "What are some interesting distinctions between clinical and consumer domains, and how can the data from one be leveraged to improve performance in the other domain?"

Q3: "What was the source for VQA work?"
A3 (in-chat): "For VQA, I used MedPix annotations to create the VQA-Med 2019 and 2020 questions and answers. If you mean the VQA-RAD dataset: the questions and answers were written by medical students."


# Byron Wallace

### Zoom chat

Q1: "How does TrialStreamer get updated when papers are retracted?"

Q2: "Have you also looked into how to leverage other types of trials, like cohort studies? Or do you have thoughts on why not to include them?"

Q3: "I am curious if you use the XML version of PMC articles in your pipeline, or do you use the PDF articles?"

**More comments from audience**

Jodi: "Upwork = great place for “expert sourcing”."

yogo: "Byron don't sell your work short! (who cares that its "simple" if it works and is useful?? that's even better if its simple)"

Jodi: "For COVID-19 papers, this is a good list: https://retractionwatch.com/retracted-coronavirus-covid-19-papers/.  Overall I’d recommend the RetractionDatabase (may require licensing) is http://retractiondatabase.org/RetractionSearch.aspx"

Lucy: "the PICO formalism is very nice to have"

### Rocket chat

Q1: “For RobotReviewer, what's the PDF conversion solution? Do you use any underlying utilities, or you and your team have an independent approach?”

A1: “Thanks! We use Grobid actually; it seems to do really well!”

Q2: “About the Evidence Inference (http://evidence-inference.ebm-nlp.com/) app, can a public user upload an article and get the evidence inference results displayed?”

A2: “The models are available, and RobotReviewer will do this, but not a super easy interface for just the inference part yet!”


# Panel

Q1: "As you’ve shown in your work, it seems critically important to partner with actual clinicians.  How did you foster those connections & any advice for us?  Scrambling to connect *after* the epidemic begins seems too late."

Q2: "Can you comment on collaboration modes, in particular "medical folks" defining questions vs them using tools, vs you running things and providing outputs, etc."

Q3: "How well do  you think we have done in communicating science to the larger public in this time? Do you think we have a role to play there? What might some research questions there be?"

Q4: "How do you assess/evaluate output of your work (during initial stages) without asking too much input from Biomed experts. Or is domain knowledge sort of important entry criteria to work?"

Q5: "What is your vision on the policy consequence of scientific NLP (both in biomedical and in general science)? Such as informing better NIH/NSF grant policies for solving replication crisis, exploring unknown frontier, etc."


**Discussion in Zoom chat**

Osnat: "Is it a problem that solving practical, real world problems using exisiting tools is not glamerous enough? (re Byron's comment)"

Yoav: "If solving real world problems with existing tools" is not glamorous enough in NLP, maybe NLP community should focus on empowering the interested parties to solve the problems themselves."

Ruben: "I think it is. If you compare CS to other domains, e.g., engineering, the research is much more applied."

Yoav: "We currently don't offer any such option."

Jodi: "+1 Yoav!"

Yoav (response to panelist answers): "I am still curious about your experience with handing them tools vs handing them results."

Byron: "@Yoav my take on this is that most applications will need some sort of customization; so this lends to bespoke models/tools -- but some sort of flexible set of tools may suffice; agree that we're not there yet though"

Jodi: "There is a field in medicine called “implementation and dissemination science”. I think we need an “implementation and dissemination science” of NLP."

Hoifung: "In my experience, usually it's not so simple as handing tools or results. We often need a substantial investment to understand the problem space and come up with a productive abstraction, which is quite different from what the med folks originally articulate. So I'd say identifying stakeholders and defining problems is first priority. Then come up with evaluation metric and data. Afterward, it's more conventional territory for NLPers :)"

Yoav: "ML "standardized" their tools with sklearn. What can NLP offer? (spacy / hugging-face is not it)"

Osnat: "Very importnat point raised by Yoav indeed"

