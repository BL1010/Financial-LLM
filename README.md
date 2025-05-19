# 🧠 FinGPT Forecaster

A lightweight Financial Language Model pipeline that leverages GPT-4 to generate training data for forecasting financial asset price movements. This project supports DOW-30, EURO-STOXX-50, and cryptocurrencies, and prepares the data for fine-tuning smaller models like TinyLlama.

---

## 🚀 Features

- **Symbol-wise data preparation** with fundamentals (if applicable)
- **GPT-4 querying** using custom prompts for financial prediction
- **Data transformation** into LLM-friendly prompt-answer pairs
- **Support for multiple indices**: DOW-30, EURO-STOXX-50, CRYPTO
- **Train/test dataset creation** with customizable train ratio
- **Ready for fine-tuning** models like LLaMA, TinyLLaMA, or other lightweight LLMs

---

## 📁 Project Structure

├── data/ # Saved raw and processed data
├── prompt.py # Prompt templates for GPT-4
├── data.py # Data preprocessing and GPT querying logic
├── indices.py # List of index symbols
├── main.py # Main launcher script
├── utils/ # (Optional) Utility scripts
└── README.md # This file
Fine tuning of Llama using Lora 

## ⚙️ How It Works

1. **Data Preparation**: 
   Downloads or reads stock/crypto data and optionally includes basic financial metrics.

2. **Prompt Generation**: 
   Constructs GPT-4 prompts of the form:


3. **GPT-4 Querying**: 
Sends prompts to GPT-4 and records its prediction and analysis.

4. **Dataset Formatting**: 
Transforms the prompt and answer into instruction-following format with:
- `system_prompt`
- `prompt`
- `answer`

5. **Training Ready**: 
Outputs a HuggingFace `DatasetDict` with `train` and `test` splits.

---

## 🔧 Usage

Run the main pipeline:
```bash
python main.py \
--index_name crypto \
--start_date 2022-12-31 \
--end_date 2023-12-31 \
--min_past_weeks 1 \
--max_past_weeks 4 \
--train_ratio 0.6
