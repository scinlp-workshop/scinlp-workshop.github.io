# SciNLP 2020 Invited Speaker Q&A

This is a transcript of questions and answers for our invited speakers.  We recorded conversations on both Rocket Chat and Zoom.  We've edited the typed questions/answers that contained typos or grammatical errors, but tried to remain faithful to the original content.  

We've also transcribed answers to questions that were given live during the presentation.  These aren't verbatim but we've tried to faithfully capture speakers' responses.  Please let us know if anything in here is incorrect!

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

The talks are all available on [YouTube](https://www.youtube.com/playlist?list=PLOTELVgUs9jKW2EkJbAyi6DcunfaXf0r6). 

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

**Unanswered**

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

Q4: "Are the news outlets primarily located in us/canada and northern european countrys?"

A4 (audience-answered; in chat): "yes they are U.S. news outlets"

**Comments from audience:**

L: "Foreign institutions may not have press offices that are well connected to these news outlets though."

Y: "Authors who publish in English are most definitely not necessarily fluent in English!"

David's repsonse: "Fully agree Y and L! I do think that lots of journalists initially communicate via email which might be easier for less fluent authors though (that said, controlling for this better is something we’re looking at)"

**Unanswered**

Zoom: "Random effects for journalists?"


# Robert Stojnic

### Zoom chat

Q1: "Is "papers with code" in your view meant primarily for academic researchers or for industry researchers?"

A1 (live): We tried to have both use cases served. For academic researchers, maybe in your field you know very well how the latest papers compare, but as soon as you go to an adjacent field, it's hard to keep up with what's happening.  We're trying to collect this information for researchers like "I'm maybe an NLP researcher but what's happening in computer vision?" We want to help researchers follow what's the cutting edge in machine learning.  But we're also trying to help machine learning engineers at the same time - When building NLP models, it's nice to see all the methodologies & code libraries to see which one is easiest to use/fits my use case.  By linking all these artifacts, I'm hoping we can serve all these use cases.

Q2: "How do you link entities of tasks from each paper? (Is the information easy to download for the public? i.e. is it within one of the three available download links in the about section?)"

A2 (live):  For task linking, it's probably the most rudimentary of all the stuff we're doing.  We look at abstracts and do some basic keyword matching, and then the community comes in and curates it. That works relatively well (kind of).  There's problems with recall. We're working on a new way of doing this by looking at the citations, what types of datasets they're looking at, looking at the tables, but it hasn't hit production yet.

Q3: "Are components of this platform open, and can people adapt them for other collaborative efforts around paper extractions, maybe for results in other domains?"

A3 (live): Everything we do in terms of extraction is on our GitHub.  So you can go and have a look there.

Q4 (follow-up from another audience member): "+1 and also, is the data (papers + extracted results) available for e.g. creating a dataset for training supervised extraction?"

A4 (live): 100% of the data is free under CC-BY-SA.  It's essentially a collection of JSONs.  You can download all of them and do whatever kind of research you want on that.  If you want to do some type of research, you can also get in touch and I might be able to help you.

**Unanswered**

Zoom: "Is the focus on equating tasks with scores on datasets good or bad for DL-science in the long run?"

Zoom: "At any point do you envision your platform (since you have both code and the paper) where one might interactively play with the parameters and see results in relation to the rest of the results / papers you index.. sort of live experiments where possible?"

Zoom: "The new accessibility standards for PDF require rather strict formatting of tables for the software for visually challenged users to read them.  Do you plan to use this formatting when available?"


**More comments from audience:**

J: "Thanks for baking licensing in! :)"


# Iris Shen

### Zoom chat

Q1: "How does MAG discard (if it does!) articles of dubious standing (say pseudoscience or extremely controversial content) from its publication index?"

A1 (live): For low-quality content, we actually leverage some external/whole web information by calling the Bing API to see if the top results are really coming from more prestigious/reputable domains, and we'll do classification from there.

**Unanswered**

Zoom: "With the increased availability of full-text open access articles, will it be possible for MAG to parse the entirety of the content in articles (not only abstracts)? Is it expected to reduce the number of orphan fields of study?"

Zoom: "What about a new concept clusters / trees?  As in, a group of new concepts can arise all at once.  How does the algorithm handle cases like this? Some may be leaf nodes of other new concepts..."

Zoom: "Is BERT-Large performing better than AllenAI models (SciBERT and siblings) for MAG?"



# Doug Downey

### Zoom chat

Q1: "Could you please explain more how the input of the pretrained transformer is represented ? every paper is represented as a sentence with |SEP| between the three papers?"

A1 (chat): "The input to the transformer is just the title and abstract (separated by [SEP]) of one paper, and the output is the embedding for that paper.  At training time, we run three identical (i.e., with tied weights) SciBERT models in parallel, one for each paper in the triple, and train the transformer weights on the loss function shown on the slide."

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

L: "My quick guess on Sidhu’s question: Unlike other domains, science is all about using the same terminology to talk about new ideas. Citation is expert-label data on the hidden association between ideas, which may or may not be easily recognized by machines."

**More comments from audience**

S: "by Stigler's Law: typically everyone cites the *second* paper ;)"

A: "Acronym identification will be a core requirement for future summarization tools"

M: "I like the simplicity of the SPECTER approach; really neat!"



# Hoifung Poon

### Zoom chat

Q1: "KBs can also contradict one another (esp since some are more up to date). What's the effect of this when using them for distant supervision? Do you prioritize relationships that are more trustworthy?"

A1 (in-chat): "Excellent question! That's partially the motivation for deep probabilistic logic. We want to be able to express and reason such prior belief about the quality of prior knowledge. It's straightforward to do. We are also extending DPL with the capability to propose new self-supervision, which can be directly added to the model or vetted by experts (as in feature-based active learning). The initial results are very promising."

**More comments from audience**

L: "exchange coffee for knowledge :D"

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

A1 (live): The goal is to build a system that is able to support customer service and the NLM in answering questions that the NLM receives everyday.  We built a first consumer-health QA system called CHIQA which is available online at [https://chiqa.nlm.nih.gov/](https://chiqa.nlm.nih.gov/). The system is able to answer a wide range of medical questions, but we continue to investigate and improve the system by working on summarizing the answers / analyzing more questions / improving the answers for several question types / adding more images or videos related to the answers.

Q2: "What are some interesting distinctions between clinical and consumer domains"

A2 (live): For consumers, it's more questions asked by patients or their families, so we are all health consumers.  So for healthcare, so there'll be more types of questions than there are asked by professionals or other actors within the healthcare system.  

Q3: "How can the data from one be leveraged to improve performance in the other domain?"

A3 (live): Yes, I think all the experiments I did since 2016, I usually use the collection of questions asked by family doctors (clinical questions) and they always help/improve results when I use them for training models for consumer-health questions.

Q3: "What was the source for VQA work?"

A3 (in-chat): "For VQA, I used MedPix annotations to create the VQA-Med 2019 and 2020 questions and answers. If you mean the VQA-RAD dataset: the questions and answers were written by medical students."


# Byron Wallace

### Zoom chat

Q1: "How does TrialStreamer get updated when papers are retracted?"

A1 (live):  I guess right now we don't, so that's something we should probably do.  That's a fair point, we should!

Q2: "Have you also looked into how to leverage other types of trials, like cohort studies? Or do you have thoughts on why not to include them?"

A2 (live):  We haven't.  I would like to get to a point where we can really meaningfully tease out the semantic representations of the RCTs because that's such a nice understandable design.  Once we can do that (and we're getting there) then I would love to move on to other designs.  Of course you can do meta-analyses of non-RCTs.  I like RCTs as a problem because it constitutes a constrained-enough universe where I feel like we can make real progress (and it's already pretty hard).  We're not right now, but of course I would like to.

Q3: "I am curious if you use the XML version of PMC articles in your pipeline, or do you use the PDF articles?"

A3 (live):  RobotReviewer will operate over PDFs, in general.  But for Evidence Inference & the sake of the data being released, we obviously use the XMLs because they're much nicer.

**More comments from audience**

J: "Upwork = great place for “expert sourcing”."

Y: "Byron don't sell your work short! (who cares that its "simple" if it works and is useful?? that's even better if its simple)"

J: "For COVID-19 papers, this is a good list: https://retractionwatch.com/retracted-coronavirus-covid-19-papers/.  Overall I’d recommend the RetractionDatabase (may require licensing) is http://retractiondatabase.org/RetractionSearch.aspx"

L: "the PICO formalism is very nice to have"

### Rocket chat

Q1: “For RobotReviewer, what's the PDF conversion solution? Do you use any underlying utilities, or you and your team have an independent approach?”

A1: “Thanks! We use Grobid actually; it seems to do really well!”

Q2: “About the Evidence Inference (http://evidence-inference.ebm-nlp.com/) app, can a public user upload an article and get the evidence inference results displayed?”

A2: “The models are available, and RobotReviewer will do this, but not a super easy interface for just the inference part yet!”


# Panel

**Q1: "Could you describe how you've been thinking about the promise of scientific NLP as it relates to the current pandemic situation, and whether we're meeting/delivering on those promises?"**

Asma (live):  This is a good opportunity for the NLP community to apply all the efforts & models that have been developed during these years in a real and concrete problem that affects a lot of our lives.  It was really great to see how interested researchers are by creating datasets.  AI2 was the first to create and propose the COVID-19 dataset & create challenges (e.g. TREC).  Of course, there are new challenges now.  Researchers all over the world are creating teams to contribute and participate in all of these.  It's true that it's a hard problem, but if I think about the QA problem, for example, systems trained on the data we have are able to answer questions by people like us (e.g. What are the symptoms?).  But also the harder problem of answering questions asked by doctors/professionals, and I think this is where it's more interesting - analyzing scientific articles and extracting/linking new discoveries/information.  It's great to see more efforts in this direction.

Byron (live):  Mostly reiterate those points.  It's been really exciting to see the focus on the potential of using these tools to rapidly respond to this pandemic.  I think hopefully one silver lining will be galvanization of more folks in NLP on these problems.  So that's been exciting, I guess.

Hoifung (live):  I want to echo Asma & Byron.  First, I want to echo Asma's shout-out for AI2 creating CORD-19, which has had instant impact and attracted a lot of systems / official evaluations built on this dataset.  This really creates opportunity for raising awareness for biomedicine and healthcare for the NLP community.  I can tell you at Microsoft, one thing I've been trying hard since I've joined is to persuade other computer scientists/NLP/machine learning to work on biomedicine.  Oftentimes, the natural reaction is "Oh well, it seems like such a messy world.  It's more comfortable to stay in more mainstream topics.  At least we can understand the text."  But I can see COVID-19 feels like a catalyst - there are so many people reaching out asking for collaboration.  So we actually have some pretty exciting internal collaborations centering around BioMedNLP.  We have some efforts specifically for COVID-19, so hopefully we can release those results soon.  For COVID-19 specifically, but also some lessons over the year for BioMed, we learned the first thing to figure out is less about whether we should use BERT or T5 but more about what's actually the key problem.  Asma & Byron really touched on "Who are the stakeholders we're trying to help?"  For COVID-19, one thing we find quite productive is we have conversations with the Cleveland Clinic folks and they've been generous to share what the useful/meaningful queries.  And each one looks like a mini-proposal.  And one thing we need to realize is that conventional search engines completely broke down (if you run them on PubMed, it doesn't return anything).  I think there's an intersection between information retrieval and core NLP where this BioMed search & NLP.

Lucy (live):  Yeah so it seems like all of you are alluding to - You've been working in BioNLP for a while, but this is a moment in time when a lot of people are being introduced to these problems for the first time & seeing how difficult it is to work in this field.  But it's also a great moment to recruit them.


**Q2: "What are some suggestions you have for partnering with medical experts and clinicals on these challenges? How do we foster these connections between the NLP community and these experts?"**

Byron (live):  Some of it is just luck - like I just keep stumbling upon these wonderful collaborators.  I actually don't think that's a huge problem in my experience.  I have more medical folks approach me than I can actually work with.  I think there's a huge demand, and one of the things I love about working on these problems is just the utility.  I'll go to the Cochrane meeting and I'll be the only computer scientist there and a lot of the stuff they have to do (e.g. making sense of literature) they really want to not have to do it.  They would love to have a system make these thigns less painful for them.  I think we can do that in NLP.  I guess what I'm getting at is that there's a lot of demand from the medical side.  

Byron (live): Maybe trying to establish venues where folks from both communities show up is a little difficult.  I'll give a shameless plug for Machine Learning for Healthcare which is a small conference we run; we try to bring folks from machine learning and physicians together to work on problems.  If you're interested, check that out - We explicitly have opportunties to get matched with physician collaborators.  

Byron (live): I do think one challenge I've found (and we've probably all faced this) is a lot of times the most useful things we can do for the physician collaborators is not the most interesting thing. Like it's not the thing that's going to get you an ACL paper. For me there's a lot of thought that goes into - I want this thing to be both interesting methodologically and useful. That may be the hardest part about collaboration for me.

Asma (live):  Collaboration is very important.  I've seen efforts made by computer scientists (e.g. QA datasets) without any doctors involved in the work, though it seems they're now aware of the importance of communicating with medical professionals.  There are a couple levels in collaboration:  (1) Defining and choosing the task to work on, (2) Deciding what are the areas that doctors will work on - Is it creating data, is it evaluating output of the created systems, is it defining what is a good training/test set.  We need to be clear on what is the task, and how can each of us contribute to it.  Doctors don't have too much time, so it's important to define things very well to avoid wasting time and have better results for that collaboration.

Hoifung (live):  This is really a good time for NLP folks to jump into the field.  I remember years ago when I first started, I went to some biomed conferences and people didn't know what NLP is.  And they'll ask you "Do you mean text mining?"  Now if you go and mention you're an NLP-er, they'll try to grab you as a collaborator.  And partially this is part of disruption happening in medicine.  EMR (electronic medical records) was not really a thing 10 years ago (maybe 10% adoption), and now it's universal in the US.  That creates a lot of text to extract information from.  You really need PubMed-scale extraction.  In the old days, cloning a gene would take 6 months to 2 years.  You could build your whole career studying a single gene, so you could read the 5000 papers about that gene.  But now, all of a sudden, a high schooler can get you 20000 genes in an afternoon, but nobody can memorize all those facts.  So that poses a serious need for the field.  

Hoifung (live): One thing in my own experience & also related to Y's question in the chat  (see below), when I first got into the field, I expected I'd go to a medical conference and doctors would tell me exactly what I need to do.  Usually it's not like that.  On the other side, they don't know what we can do.  On one hand, they think of us as IT++ (e.g. Can you show 50 results instead of 20 results).  On the other spectrum, they think of us as being able to do anything that can be done by humans.  So we (computer scientists) need to get into a little bit of the medical lingo & know enough to figure out their pain points and match that pain point to what NLP is capable of doing.  We're very far from AI-complete, so there are only certain things we can help.  But like Byron & Asma mentioned, once you find those initial matches, the opportunities just...  (Hoifung indicated here there's a lot). 


**Q3:  "How much domain knowledge do you need to get started in BioMed work?  Do you have to start from a point where you understand this text as an NLP researcher?"**

Hoifung (live):  One interesting thing Mausam said many years ago when he saw one of the PubMed slides was "Is this English?" :D  It can be intimidating the first time you see some BioMed text.  There are a couple things:  (1) Biology and medicine is a very intimate subject.  You learn about that and it's actually useful everyday.  So it can be very joyful to learn about some of those things.  (2) I posed that exact question when I first joined MSR.  I said "David, I'm definitely a layman.  Can I make contributions?"  And he (David Heckerman) said that biomedicine is like a sea that's only 1 meter deep.  It has a lot of concepts (e.g. UMLS has millions of concepts), but for any particular use case (e.g. precision oncology) you can quickly learn enough to be able to understand the abstract problem.  It's not like quantum mechanics where you need 10 years and a post doc to even understand what's going on.  I wouldn't consider that as a big deterrent.  But we as a community can definitely help lower the entry barrier - e.g. if you look at in NLP, there are tons of leaderboard, benchmarks, open source code, etc.  So I think for BioMed or SciNLP in general, if we as a community can start to combine with these benchmarks & leaderboards so they can substantially lower the entry barrier.


**Q4: "How well do you think we have done in communicating science to the larger public in this time? What do you think is the role of NLP researchers in this?"**

Byron (live):  Maybe some work in simplification can go a long way.  And it's probably a pretty do-able thing.  You can try to build models that can simplify technical literature.  Maybe this is tangentially-related, but it's something I've been thinking about a lot.  As summarization systems have gotten quite good, if we're going to start doing that, then the issue of factuality in abstractive summarization becomes paramount in a way that seems super important.  Of course it's always important in summarization, and maybe I'm showing my own biases, but I think that's a really important direction - Enforcing factuality in a system that's summarizing scientific literature.

Asma (live):  Scientists have an important role, especially in defining research directions in the future.  Simplifying the language to make it more understandable by non-professional / non-expert users.  Also, fact-checking, for example, is one of the tasks that we need to work on, to at least check the information that has been published these last months (and maybe years in the future), because now people are publishing faster than before & we don't have the time to check things.  Working on models for fact-checking and misinformation is one of the directions that's very important, in addition to simplifying scientific papers for the public.  

**Q5: "What is your vision on the policy consequence of scientific NLP (both in biomedical and in general science)? Such as informing better NIH/NSF grant policies for solving replication crisis, exploring unknown frontier, etc."**

Hoifung (live): We try to separate problems into "machine reading" (e.g. take the author at face value and extract; a task that's relatively easy to evaluate by anyone who's knowledgable about the domain), and on top of that is a much harder problem.  That is, we have an ocean of author face-value statements from 30M papers - What do make of it?  What's the consensus of the community?  How much should I trust this more than others?  That part we attribute to "assembly" or "reasoning".  For that part, it's much harder to get to "ground-truth".  The top scientists might not even agree on something.  That's why we started with some work in knowledge graph embedding & reasoning, but we've sort of retreated back into the safe zone in "machine reading" because we know how to evaluate it.  But I think there's a huge opportunity - How do we actually reason about corpus-level belief?

Lucy (live):  Absolutely, and I think with generative models, it is gonna be a huge challenge moving forward in terms of evaluation & how to use these in real-world application.  Asma, does the NIH have any policies about how to use generative models or the results of generative models to inform policy?

Asma (live):  Maybe it's a little bit early now to know this.

Lucy (live):  Going back to Byron's earlier comment where, sometimes, it's hard to find a collaboration where you can get an ACL paper out of it and get something effective working for the medical community.  There's a lot of responses in the chat responding to that comment. 

Byron (live):  :D  There's a reason I spent a lot of time doing stuff that's, in large part, not that glamorous.  I don't know if I have sage advice for the community at-large to do about it.  I'm sure we've all faced this. 

Lucy (live):  Absolutely. It certainly matches my experience, which is very frustrating.  For the medical experts who want our help, they have a very specific task in mind and you can actually change the way they do something in clinic.  But the methods used as not novel enough to engage experts in our domain.

Asma (live):  It may be good to balance doing work that's publishable in ACL and other NLP conferences, and also doesn't mean all of our papers should be like that.  We know that it's important / meaningful sometimes to publish in workshops or in medical informatics conferences, like AMIA, because it's there where we understand what doctors and medical professionals need and learn how we can help to change what they're doing daily.  At conferences (e.g. ACL, MEDINFO, etc.) it was interesting to meet NLP researchers working on medical informatics.  I found it interesting to publish in these different venues because it's how we learn more about how we can help with what we do.

Asma (live):  Venues like ACL also has an important role to play in this.  Maybe inviting more people who are working on BioNLP and medical-related tasks.  Making more workshops where people from both communities can meet and work together and exchange thoughts. 

Hoifung (live):  Byron sort of nailed it in terms of funding and publication - 2 important deterrents for people entering new territory, especially a highly-specialized application area.  At least I personally lucked out in MSR because my first year I didn't publish any papers and nobody frowned at me.  But I know that's a luxury not everybody can have.  I think last NAACL, I suddenly noticed more BioMed-related papers.  I'm quite optimistic.  I also think COVID-19 drew us out of the comfort zone.  I heard from multiple people (e.g. Regina Barzilay) when you run into really unfortunate medical events, that really puts things into perspective - Do I really want to increase 2 points in my parser, or do I actually want to help speed up the next life-saving drug?  I'm starting to see some tracks that some people are putting in NLP conferences that are more specific to these applications, and workshops like this are super helpful to raise awareness & get like-minded people to join forces.

Byron (live):  I think that's a great challenge for the community to figure out a sweet spot between being practically useful and advancing core language technologies forward.  Will defer to the prior responses :)


### Other questions

Zoom: "How do you assess/evaluate output of your work (during initial stages) without asking too much input from Biomed experts. Or is domain knowledge sort of important entry criteria to work?"

Asma (offline): "Generally, by designing and creating a (small) test set for the targeted task, manually validated (or annotated, if possible) by domain experts. Defining and validating the annotation guidelines with medical experts is a good starting point towards learning more about the domain and the task before building automatic systems."




**Discussion in Zoom chat**

O: "Is it a problem that solving practical, real world problems using exisiting tools is not glamerous enough? (re Byron's comment)"

Y: "If solving real world problems with existing tools" is not glamorous enough in NLP, maybe NLP community should focus on empowering the interested parties to solve the problems themselves."


R: "I think it is. If you compare CS to other domains, e.g., engineering, the research is much more applied."

Y: "We currently don't offer any such option."

J: "+1 Y!"

Y (response to panelist answers): "I am still curious about your experience with handing them tools vs handing them results."

Byron: "@Y my take on this is that most applications will need some sort of customization; so this lends to bespoke models/tools -- but some sort of flexible set of tools may suffice; agree that we're not there yet though"

J: "There is a field in medicine called “implementation and dissemination science”. I think we need an “implementation and dissemination science” of NLP."

Hoifung: "In my experience, usually it's not so simple as handing tools or results. We often need a substantial investment to understand the problem space and come up with a productive abstraction, which is quite different from what the med folks originally articulate. So I'd say identifying stakeholders and defining problems is first priority. Then come up with evaluation metric and data. Afterward, it's more conventional territory for NLPers :)"

Y: "ML "standardized" their tools with sklearn. What can NLP offer? (spacy / hugging-face is not it)"

O: "Very importnat point raised by Y indeed"

