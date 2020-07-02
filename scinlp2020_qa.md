# SciNLP 2020 Q&A

This is a transcript of questions and answers for our invited speakers.  We recorded conversations on both Rocket Chat and Zoom.  We've edited typed questions/answers that contained typos or grammatical errors, but tried to remain faithful to the original content.  Please let us know if anything in here is incorrect!

In speaker order:
* [Ryan McDonald](#ryan-mcdonald)
* [Vivi Nastase](#vivi-nastase)
* [Doug Downey](#doug-downey)
* [Hoifung Poon](#hoifung-poon)
* [Byron Wallace](#byron-wallace)

# Ryan McDonald

### Zoom chat

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
 
 
 
 
# Vivi Nastase

### Zoom chat

### Rocket chat

Q1: “Did you say that you tried to use the ACL Anthology for your experiments at some point but had problems?”

A1: “We are still working on extracting specific information from the ACL collection -- connecting NLP problems with their solutions -- but, unsurprisingly, it's hard. So that part is still under construction.”

Q2 (follow-up; rephrased): “Have you used the ACL ARC v2 has OCRed and parsed versions of the anthology?”

A2: “We work with the OCR-ed, and even did some word segmentation correction there, but it's hard to extract a nice and clean path from the problem to the solution, which is what we are after. But we'll persist!”



# Doug Downey

### Zoom chat

### Rocket chat

Q1: “Why does Pretrained Transformer perform poor given that Abstract, Title and Conclusion are information dense?”

A1: “You're right that the raw semantic content needed to represent the paper well is there (btw we use just title+abstract, not conclusion, but the point remains the same). The problem is that the embeddings output by the off-the-shelf transformer didn't tend to capture that document-level information well, in our experiments. Finetuning the transformer on the citation objective helps ensure that the document-level semantics ends up in the embeddings.”

Q2: “How would AI2's Longformer (https://github.com/allenai/longformer) fare on the tasks in the table in which SPECTER was compared to baselines?"

A2: “Good question, we are working on this now -- stay tuned 🙂. I think it would help, in particular Longformer would allow us to easily use the text of the paper references, which I expect will be very valuable for our tasks.”


# Hoifung Poon

### Zoom chat

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

A6: “One thing we find helpful is to break down the annotation task into 80/20 stages. Often, finding the core facts is the most time-consuming part, which is what we start with, e.g., drug-gene-mutation for molecular tumor board. And then we keep identifying the next 80/20 opportunities for assisted curation.”
 
Q7: “What do you think of full-text vs. title & abstract? Will full-text mining availability always help? There are definitely more data in full-text but also probably more noise that may confuse the algorithm. Do you have an experience with that?”

A7: “Full text is basically mandatory. E.g., most mutation-level results are not present in abstracts. As a rule of thumb, the most details and nuanced info you are looking for, the more you need full text. Like you said, full text is much noisier, with more complex structures, which is why we are pushing on cross-sentence or document-level relation extraction.”
 
Q8: “It's nice to consolidate the labeling functions / sources of supervision via graphical models. Could you comment on the efficiency/scalability aspect of this approach?”

A8: “Yes. In deep probabilistic logic, we use graphical model for modeling self-supervision, which is in a reduced state space (latent labels), so even standard methods like belief propagation work reasonably well. The end-to-end training uses variational EM, which generally converges after 2-3 iterations.”



# Byron Wallace

### Zoom chat

### Rocket chat

Q1: “For RobotReviewer, what's the PDF conversion solution? Do you use any underlying utilities, or you and your team have an independent approach?”

A1: “Thanks! We use Grobid actually; it seems to do really well!”

Q2: “About the Evidence Inference (http://evidence-inference.ebm-nlp.com/) app, can a public user upload an article and get the evidence inference results displayed?”

A2: “The models are available, and RobotReviewer will do this, but not a super easy interface for just the inference part yet!”
