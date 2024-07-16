# Introduction
The study in textual emotion analysis has primarily focused on recognizing emotions in static text, neglecting the intricate dynamics of real-time conversations. The project addresses the gap by exploring the underlying causes of emotions in conversational dialogues. Although the previous studies in the field have primarily relied on static sources like social media posts, our study delves into the intricacies of conversational contexts, comprising of textual elements. Our study aims to extract emotion-cause pairs from conversations, identifying causes for expressed emotions using a dataset from the renowned TV series "Friends." We aim to develop a sophisticated system to analyze conversational instances and showcase the effectiveness of our approach through results.

<img width="1219" alt="Screenshot 2024-07-17 at 12 42 29 AM" src="https://github.com/user-attachments/assets/b5f336b6-85bb-47ab-915d-f1b1205774b3">

# Methodology
We break the problem statement into two specific tasks. Task 1 is based on identifying the underlying emotions within a conversation, i.e., Emotion Recognition in Conversation, while task 2 is based on finding the causal spans within a conversation, i.e., identifying the triggers (causes) that led to a specific emotion within the context of a conversation.

For model 1, we accounted for the speakers and utilized the context of the conversation. We created Conversation Context Embeddings by concatenating the context of an utterance in its conversation. We included the speaker context by prepending the speaker names in the sentences, and passed the embeddings to the BERT encoder, and BertForSequenceClassification model for predicting the emotions. For model 2, we let the BERT itself learn the context by first predicting emotions for all utterances in conversation, and then backpropagating the combined loss, enabling to optimize all emotions of a conversation at once.

For Task 2, we developed two different models. In Model 1 we fine-tune a BERT model for question answering task to identify the causal span. For our task, question is referred to the target utterance, and context is analogous to all other utterances in the conversation. We input the targets and contexts to BertForQuestionAnswering model to predict the causal spans. Model 2 is combination of two BERT models fine-tuned to first extract the target-cause utterance pairs and then identify the specific spans within the sentence, which acted as the primary cause for expressing emotion.

<img width="1300" alt="Screenshot 2024-07-17 at 12 43 49 AM" src="https://github.com/user-attachments/assets/ef256a15-ef00-4d2f-9a47-2aa9e0d83c97">

# Experimental Setup

<img width="1264" alt="Screenshot 2024-07-17 at 12 47 40 AM" src="https://github.com/user-attachments/assets/990abd33-62fe-443b-b441-20a98e11cdb2">

# Results
The results of the models are as follows:

* ERC Task 1: F1-Score: 0.53, Accuracy: 0.55
* Cause Span Task 2: F1-Score: 0.94, Accuracy: 0.95

# Authors
* Vasan Vohra
* Sachin Sharma
* Ritwik Harit
* Tanmay Singh


