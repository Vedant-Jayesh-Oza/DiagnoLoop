# 🩺 DiagnoLoop: AI-Based Clinical Assistant for Symptom-to-Disease Diagnosis

**DiagnoLoop** is an end-to-end intelligent medical assistant that transcribes patient-reported symptoms (audio or text), extracts clinical entities using **AWS Comprehend Medical**, and generates accurate disease predictions using a **fine-tuned LLM** combined with **RAG (Retrieval-Augmented Generation)** and a structured **knowledge graph (Infermedica)**.

## 📄 Preliminary Paper
**[View Preliminary Research Paper](https://drive.google.com/file/d/1xbmrr6zhPp5GIsa0123cEuleYzJ-dUpX/view?usp=sharing)** - Comprehensive analysis of the DiagnoLoop multi-modal AI diagnostic system

---

## 🔬 Use Case

> "I have been having headaches for a while now... I also get nausea, vomiting, and sensitivity to light."

Using just this raw input, DiagnoLoop:
- 🧠 Transcribes voice input using Whisper
- 🏥 Extracts structured symptoms like `"headache"`, `"nausea"`, etc.
- 📚 Retrieves relevant clinical information using FAISS + Sentence Transformers
- 💬 Predicts top diagnoses like `"Migraine"`, `"Vestibular migraine"`
- 🔁 Iteratively refines predictions by asking follow-up questions to patients

---

## 🧠 System Architecture

### 🔄 Full Pipeline Overview

![image](https://github.com/user-attachments/assets/a4042d55-d9c9-4240-a5d6-612d914e17ce)

### 🔁 Iterative Refinement Loop

![image](https://github.com/user-attachments/assets/4ace8e82-4cab-4899-8591-309c1a6d7188)

---

## 🧩 Components

| Module                       | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| `Speech-to-Text (Whisper)`  | Converts patient audio to transcribed text                                 |
| `AWS Comprehend Medical`    | Extracts symptoms and clinical keywords                                     |
| `FAISS + Sentence Transformers` | Retrieves relevant clinical text from a curated medical knowledge base      |
| `LLM Generation`            | Fine-tuned GPT model predicts top 3 diagnoses                              |
| `Infermedica Knowledge Graph`        | Provides structured disease predictions based on symptoms                   |
| `Merge & Rank`              | Combines LLM + KG predictions and ranks based on combined confidence        |
| `Follow-up Loop`            | LLM generates yes/no follow-up questions based on missing symptoms          |

---

## 🚀 Getting Started

### 1. Clone the Repo

```bash
git clone https://github.com/Vedant-Jayesh-Oza/DiagnoLoop.git
cd DiagnoLoop
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Set Up Your Secrets

Create a `.env` file or export these keys in your terminal:

```bash
export OPENAI_API_KEY="YOUR-OPENAI-KEY"
export AWS_ACCESS_KEY_ID="YOUR-AWS-ACCESS"
export AWS_SECRET_ACCESS_KEY="YOUR-AWS-SECRET"
```

---

## 🗂️ Repository Structure

```
DiagnoLoop/
│
├── notebooks/                  # Main Jupyter notebooks
│   ├── medical assistant.ipynb
│   ├── rag dataset cleaning.ipynb
│   └── finetune dataset mapping.ipynb
│
├── Datasets/                   # Processed training & test data
│   ├── symptom-disease-*.csv/jsonl
│
├── rag_knowledge_base/        # RAG documents & metadata
│   ├── rag-dataset.jsonl
│   └── rag-metadata.json
│
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🛠️ Tech Stack

* 🧠 **LLM**: Fine-tuned GPT-4.1 Mini
* 🧬 **Symptom Embedding**: SentenceTransformers (`all-mpnet-base-v2`)
* 📦 **Retrieval**: FAISS for dense similarity search
* 📈 **NER**: AWS Comprehend Medical
* 🌐 **Knowledge Graph**: Infermedica API
* 🎙️ **Transcription**: OpenAI Whisper
* 🧪 **Sentiment Check**: HuggingFace Transformers (SST-2)
* 📊 **Data Preprocessing**: Python, Pandas, JSONL

---

## 🧪 Example Output
![E1612373-40EE-45BF-9AC8-FEFC5A6AF210](https://github.com/user-attachments/assets/1ddfb0bf-8461-4521-a147-9f9bfc9ecb9c)


---
## 🧠 Future Work

* [ ] Web UI for patient interaction
* [ ] Symptom severity scoring
* [ ] Export diagnosis reports (PDF/CSV)
* [ ] Suggest relevant Lab Tests and Reports based on Symptoms to take For a Deeper Diagnosis

---

## 📜 License

This project is licensed under the MIT License.

---

## 🌟 Support

If you find this useful, please ⭐️ the repo and share!
