# WWW24_rebuttal
We sincerely thank all the reviewers for the valuable comments and suggestions they provided. We add our response as follows:

**Response to Reviewer1**

We sincerely thank the reviewer for the suggestions and below please find our response

$\underline{Response \space to \space the \space weaknesses}$
1. In terms of question classification, our approach did not involve data filtering, as no data was excluded from our training samples. Instead, our focus in the clarification question classification was on categorizing questions based on their suitability for images. This classification is crucial because, in real-world scenarios, a search system lacks the foresight to determine which clarifying questions should accompany image. We believe this preemptive classification, conducted prior to image attachment, adds robustness to our method and is therefore necessary in the whole framework.
  
2. It is true that image plays a vital role in the retrieval performance, which also verifies our idea that adding images to the clarification phase can lead to efficient performance lift. The only issue is that choosing which image to attach is important. Despite our rigorous quality control measures and cross-check procedures during the creation of Melon, minor noise or deviations in the dataset remain inevitable due to human annotators. Therefore, we need to re-check the image quality again from the model part, and that’s why we design the multimodal-enhanced question classification module and image selection module. This ensures a re-evaluation of image quality from the model's perspective, aiming to mitigate human bias and inaccuracies. his is substantiated by specific cases (e.g., case 4 & 5 in Table 6) where the model successfully avoids human-annotated biases. In these instances, the model determines that certain questions do not require accompanying images, contrary to the assertions made by human evaluators. Our ongoing work involves delving into more advanced techniques in our future work to further diminish human bias and enhance accuracy.

3. (i) We completely agree that preparing good training examples during the dataset collection phase is crucial and helps reduce the burden of question classification. However, our preliminary experiments show that the model prediction does not always agree with the human classification models (we use some cases listed in Table 6 to discuss why this happens). (ii) Furthermore, training a model with the capability to automatically classify questions would prove beneficial. In real life scenarios, when a clarifying question is generated, the model does not know whether it will need a question or not. This lack of foresight in discerning the necessity for image attachment emphasizes the design of our classification module.

$\underline{Response \space to \space the \space questions}$

1.	We are extremely grateful to the reviewer for pointing out this typo for us. We will correct it in the camera-ready version. Yes, it should be ‘when a conversational system enters the question clarification phase after a user query submission’.
   
2.	We sincerely apologize for not elaborating more data preparation details in our paper due to page limit. Initially, all the clarifying questions in our dataset consist of set 1 (discussed in Line 353) and set 2 (discussed in Line 360) questions. Set 1 questions contain both multimodal and unimodal cases and were originated from ClariQ. To categorize them, we engaged annotators to manually assess whether a ClariQ question is multimodal or unimodal. It's important to note that we retained both multimodal and unimodal questions in our dataset. Set 2 questions are all multimodal, collected anew from AMT. Specifically, we hire AMT workers to strictly follow the rules in Line 367 to generate multimodal questions from scratch. We design these strategies to reuse ClariQ questions while collecting the new multimodal questions at the same time in order to figure out what’s the difference between human-determined multi/unimodal questions. Also, this will help us harvest more multimodal questions since the ClariQ question set is rather small.

We thank again for the time the reviewer spent on our paper. We will improve the paper according to all the issues the reviewer mentioned in our next version.

**Response to Reviewer2**

We sincerely thank the reviewer for the suggestions and below please find our response

$\underline{Response \space to \space the \space weaknesses}$

1. In terms of RQ4, we are very grateful to the concern the reviewer makes. We will consider re-formulate the research question in a better way in our next version.

2. For the ClariQ dataset, according to the original paper, all the topics and documents are borrowed directly from the Trec Web Track dataset (https://trec.nist.gov/data/webmain.html). And all the documents originate from the ClueWeb09/12 set. For the LambdaMart baseline, we borrow the 46 features in the LETOR 4 paper to represent the features of ClueWeb documents. Therefore, the entire dataset is based on the ClueWeb set.

3. We adopt the generative document retrieval method as a second-stage re-ranker. For the first stage, we adopt BM-25 to first retrieve top-100 documents (illustrated in Line 1258). For the reason of why we adopt generative retrieval, please see our third response to the questions.

4. We apologize for the typo in Figure 6(a). Yes, the ylabel should be loss. We thank the reviewer for pointing this out and will modify it in our next version.
  
5. Yes, we evaluate the system mainly based on the retrieval performance. Since document retrieval is the ultimate goal of how good a search system is, we only report the retrieval performance in our paper. However, we attach the precision, recall, and f1 score of it in the following table for the reviewer to have some idea of the performance of our image selection module. **mark**



$\underline{Response \space to \space the \space minor \space comments}$

1. We are sorry for the ambiguity of the sentence. What we're trying to mean is that VLT-5 is a state-of-art multimodal pretrained model that takes a pair of image and text as input and outputs a natural language text sequence, which perfectly fits to our generative retrieval scenario.
  
2. We sincerely apologize for the misunderstanding. Yes, these documents are retrieved, and we will change it to ‘finally presents the retrieved documents to the user’.
   
3. We calculate the answer length by counting the terms used in the answer. When counting terms, we take into account the individual words that appear in an answer. For example, for the answer ‘I don’t know’, the length is 3.

$\underline{Response \space to \space the \space questions}$

1. We randomly select VEQ and TEQ answers from three random VEQ categories and two TEQ categories. Listing one example for each category.
   
2. As illustrated above, we use the ClueWeb09/12 document corpus.
   
3. The advantages of generative retrieval are multifold. First of all, we show that generative retrieval outperforms traditional dense retrieval in terms of several metrics. In table 6, we record the performance of the traditional dense Bert (line 707)/VisualBert (line 709) retrieval. We can see that Marto (line 711) has better performance with a generative paradigm. Then, we show that generative retrieval has more advantages and saves more training time in terms of efficacy (Figure 6 and Table 4). Furthermore, we believe that in the era of Large Language Models (LLMs), generative retrieval holds several advantages that align with the capabilities of these advanced language models.
   
4. We see all the components in Section 3 as modules of a modern search system, whose ultimate goal is to provide accurate retrieval results. Therefore, we evaluate these modules as a whole system, reporting the downstream retrieval performance. Also, to evaluate the effectiveness of each system, we perform some ablation study on the variants of the model (e.g. Marto_w/o QC in Line 712). We didn’t report the classification/image selection performance in the paper to save space for more analysis. However, we attach the results below for providing an overview of how these modules work. We will add them to the Appendix in our next version.
   
5. We believe that this dataset can be used for future improved systems. Since it is the very first conversational clarification dataset that contains multimodal information. It can be used to upgrade the modules into more advanced format (e.g. image selection), or making room for the multimodal query clarification in the LLM era.


We thank again for the time the reviewer spent on our paper. We will improve the paper according to all the issues the reviewer mentioned in our next version.

**Response to Reviewer3**

We sincerely thank the reviewer for the suggestions and below please find our response

$\underline{Response \space to \space the \space weaknesses}$

1.The work focuses on the mixed-initiative search systems, which is a popular research direction in the modern search system. In a search system, the problem setting is that the users would like to search for a bunch of documents given a single user query (one of the most typical real cases is the search engine). The idea of asking clarification questions is to turn the simple ‘click-search-return’ paradigm into a conversational experience for better knowing the user’s real intention. Therefore, different from a conversational QA system, we only focus on the search document retrieval system, where returning the summarization of documents is beyond our scope. We will make this setting clearer in our next version. (@Mohammad maybe you could illustrate more?)

2. We agree with the reviewer’s opinion about generating clarification questions instead of retrieving. In fact, both generation and retrieval of clarification questions  
have its pros and cons (generating can result in flexible but risky results, while retrieval is quicker and safer while less interesting). However, in this work, since obtaining text-only clarification questions is not the main focus and there are already plenty of works in this area [1,2,3], we just directly borrow the same setting in ClariQ, retrieving and selecting the most suitable question. This avoids us from collecting LLM generated questions from scratch and saves us much time and effort. However, we keep the LLM clarification question generation as our on-going direction and we will list it as an important future work direction.


3.We’re sorry that we are not able to provide details for why we design the workflow in detail for the page limit.
(a)   For generative retrieval design, we performed some preliminary experiments when choosing the right model. We compared the generative model with its pre-trained discriminative counterpart VisualBert and found the performance is better (listed in Table 3) and the convergence speed is much faster (in Figure 6). We also compare it with some traditional lexical models (e.g. LambdaMart). For the format of doc-id, we follow the setting in ref[??] (where they compare the performance of keywords id with other formats), and also adopt the keywords as the unique doc-id.
(b)  For the reason why we chose VLT5 as the base model, we also performed some experiments. First, VLT5 is among the models that perfectly fit our requirement, taking the image and text as input and outputting the text. For other pre-trained models that share this structure, we also try VLP [4], and report the performance in Marto_VLP in Table 3. Also, we tested VLBart as our backbone and report the performance as follows (53.62, 51.25, 38.22, 36.09, 27.47, 23.88, 23.65, 14.03, 18.48, 20.80) (We will update it in our next version). Of course, we also try CLIP for document retrieval, but the performance is not satisfactory. Because to perform the document retrieval, the model should be able to take multimodal inputs (clarifying questions and associated images) and incorporate these features. While directly concatenating pre-trained CLIP embeddings to retrieve the documents with cosine similarity does not have a good performance. However, for cross-modal image selection, CLIP shows perfect cross-modal retrieval advantage without any training. For we only need to calculate the similarity between each image and clarifying questions to directly retrieve the images.
[1] Answer-based Adversarial Training for Generating Clarification Questions
[2] Asking clarifying questions in open-domain information-seeking
conversations
[3] A Survey on Asking Clarification Questions Datasets in Conversational Systems
[4] Unified Vision-Language Pre-Training for Image Captioning and VQA
 
4.(a) Yes, there’s some topic overlap between set1&2 questions. However, even though the topics are the same, interestingly, we found that set 2 workers often focus on different facets of the topic compared with ClariQ results. This observation suggests a nuanced diversity in the perspectives and considerations brought forth by set2 workers when exploring shared topics.
(b) 
(c)We adopt a python toolkit to extract the keywords automatically (spacy: https://github.com/wjbmattingly/keyword-spacy). We will add this detail to our next version.
(d)   We only report the top-1,3,5 results because in the real scenario, users tend to focus more on the top contents that appear in the first page of the returned search results. This tendency underscores the significance of focusing on the top-5 documents, as they often encapsulate the most relevant and immediately accessible information. Also, in this work, rather than focus on the first-stage ranker that puts emphasis on top-100,1000 document retrieval, we focus on the second-stage re-ranker, which aims to retrieve high-quality and accurate top retrieval results. However, we also tested our model on top-10 performance but didn’t report it in the paper for space limit. We found our method still outperforms all the baselines and passes the confidence test.
(e)  We only mention efficiency but not effectiveness because we compare our method with other baselines in terms of effectiveness in Table 3. Our model outperforms all the baselines, which shows the effectiveness of our model. Also, in Table 6 (b), we also find that our model reaches good performance in a relatively short time, which also verifies the effectiveness of it. We will add more elaborations to it in the future version.
 


