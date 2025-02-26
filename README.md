# Finetuning of Falcon-7B LLM using QLoRA on Mental Health Conversational Dataset

## Introduction:
Mental health issues are often misunderstood or not fully grasped by the general public. This lack of understanding can lead to fear, discomfort, and negative perceptions about mental health conditions. Media portrayals of mental health often perpetuate negative stereotypes, leading to misconceptions and fear. Overcoming mental health stigma requires a multi-faceted approach that involves education, raising awareness, promoting empathy and understanding, challenging stereotypes, and ensuring accessible and quality mental health care. Mental health directly impacts an individual's overall well-being, quality of life, and ability to function effectively in daily life. Good mental health is essential for experiencing happiness, fulfilment, and a sense of purpose. Mental health and physical health are closely intertwined. Untreated mental health issues can lead to or worsen physical health problems, such as cardiovascular diseases, weakened immune systems, and chronic conditions.

## Features
- **Falcon-7B LLM**: Uses Falcon-7B for generating human-like responses.
- **PEFT Fine-Tuning**: Optimized model fine-tuning for efficient performance.
- **LangChain Integration**: Manages conversation flow and memory.
- **Gradio UI**: Simple and user-friendly chatbot interface.
- **Mental Health Focus**: Designed to provide supportive and empathetic responses.

## Core Rationale:
Chatbots offer a readily available and accessible platform for individuals seeking support. They can be accessed anytime and anywhere, providing immediate assistance to those in need. Chatbots can offer empathetic and non-judgmental responses, providing emotional support to users. While they cannot replace human interaction entirely, they can be a helpful supplement, especially in moments of distress.

_NOTE: It is important to note that while mental health chatbots can be helpful, they are not a replacement for professional mental health care. They can complement existing mental health services by providing additional support and resources._

## Dataset:
The dataset was curated from online FAQs related to mental health, popular healthcare blogs like WebMD, Mayo Clinic and Healthline, and other wiki articles related to mental health. The dataset was pre-processed in a conversational format such that both questions asked by the patient and responses given by the doctor are in the same text. The dataset for this mental health conversational AI can be found here: [heliosbrahma/mental_health_chatbot_dataset](https://huggingface.co/datasets/heliosbrahma/mental_health_chatbot_dataset)
.

_NOTE: All questions and answers have been anonymized to remove any PII data and preprocessed to remove any unwanted characters._

## Model Finetuning:
This is the major step in the entire project. I have used sharded Falcon-7B pre-trained model and finetuned it to using the QLoRA technique on my custom mental health dataset. The entire finetuning process took less than an hour and it was finetuned entirely on GPU P-100 from Kaggle. It could also be trained on free-tier GPU using Nvidia T4 provided by kaggle. In that case, we have to ensure to use max_steps less than 150. The rationale behind using sharded pre-trained model is mentioned in my blog post: [Fine-tuning of Falcon-7B Large Language Model using QLoRA on Mental Health Dataset](https://medium.com/@iamarunbrahma/fine-tuning-of-falcon-7b-large-language-model-using-qlora-on-mental-health-dataset-aa290eb6ec85)
Adding here the training loss metrics tracking report from WandB monitoring logs for 10 steps training run: [train/loss logs for Falcon-7B PEFT](https://wandb.ai/atickft13129-green-university-of-bangladesh/huggingface?nw=nwuseratickft13129&panelDisplayName=train%2Floss&panelSectionName=train) 

_NOTE: Try changing hyperparameters in TrainingArguments and LoraConfig based on your requirements. With the settings mentioned in notebook, I achieved 1.3673 training loss after 10 steps._

## Model Inference:
PEFT fine-tuned model has been updated here: [Hugging Face Link](https://huggingface.co/FardinAbrar/Falcon-7b-model-Finetuned-By-Mental-Health-Data).

Run `gradio_chatbot_app.ipynb` notebook to get a chatbot like interface using Gradio as frontend for demo. Play around with different hyperparameter config settings for answer generation and run multiple queries to check for the quality of generated response.

It takes less than 30 seconds to generate the model response. Compare the PEFT model response with the original model response in `falcon-7b-model-finetuned-by-mental-health-data.ipynb` notebook.

## Future Improvements
- Improve response accuracy with better fine-tuning.
- Integrate a **vector database** for knowledge retrieval.
- Deploy the chatbot as a **web application**.

## Conclusion
This project serves as a valuable practice and experimental setup for exploring [Finetuning of Falcon-7B LLM using QLoRA on Mental Health Conversational Dataset]. Through this implementation, I experimented with different techniques, models, and fine-tuning strategies to enhance performance and gain deeper insights into the problem domain.

By leveraging Kaggle as the development environment, I effectively tested and refined my approach while ensuring reproducibility. The project is a stepping stone toward more advanced implementations, and the findings here can be further expanded for real-world applications.

Future improvements could involve optimizing model performance, incorporating more datasets, or fine-tuning hyperparameters to achieve even better results. This experimentation lays the groundwork for future research and practical implementations in this field.