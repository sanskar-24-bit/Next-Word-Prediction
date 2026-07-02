🧠✨ Next Word Prediction with LSTM

Predict what comes next — one word at a time.

A deep learning app that reads your sentence and predicts the next word using a custom-trained LSTM neural network, wrapped in a clean Streamlit interface

🎯 What This Does

Give it a phrase, and the model predicts the most likely next word — trained on a dataset of quotes to learn natural word flow and sentence rhythm.

✍️  Input:   "what are you"
🔮  Output:  "..."

✍️  Input:   "are you a"
🔮  Output:  "..." → can be chained into full phrases! 🪄


🚀 Features


🔤 Real-time next-word prediction via a simple, elegant web UI
🧠 Custom LSTM model trained from scratch (Embedding → LSTM → Dense/Softmax)
⚡ Instant inference with a cached model (no reload lag between predictions)
🔁 Multi-word generation — chain predictions to auto-complete full phrases
📦 Fully reproducible pipeline — from raw quotes to trained model, all in one notebook
🎨 Clean, minimal Streamlit interface — no clutter, just type and predict

🧩 How It Works

📄 Raw Quotes  →  🧹 Clean & Lowercase  →  🔢 Tokenize  →  ✂️ Generate N-gram Sequences
       →  📏 Pad Sequences  →  🏗️ Embedding + LSTM + Dense(softmax)  →  🎯 Predicted Word

StepWhat Happens1️⃣ PreprocessingQuotes lowercased & stripped of punctuation2️⃣ TokenizationKeras Tokenizer builds a 10,000-word vocabulary3️⃣ SequencingEach quote is split into growing input → next-word pairs4️⃣ PaddingSequences pre-padded to a fixed max_len5️⃣ ModelingEmbedding(150-d) → LSTM(128 units) → Dense(softmax)6️⃣ TrainingAdam optimizer + categorical cross-entropy loss7️⃣ InferenceModel outputs a probability over the vocabulary → top word returned


🗂️ Project Structure

📦 next-word-prediction
├── 📓 next_word_prediction.ipynb   # Data prep, model building & training
├── 🚀 app.py                       # Streamlit app for live predictions
├── 🧠 lstm_model.h5                # Trained LSTM model
├── 🔤 tokenizer.pkl                # Fitted Keras tokenizer
├── 📏 max_len.pkl                  # Max sequence length for padding
├── 📊 qoute_dataset.csv            # Training data (quotes)
├── 📋 requirements.txt             # Dependencies
└── 📖 README.md


⚙️ Model Architecture

LayerDetails🔡 Embeddinginput_dim=10000, output_dim=150🔄 LSTM128 units🎯 Dense (Output)10000 units, softmax activation🧮 LossCategorical Cross-Entropy🏃 OptimizerAdam

<details>
<summary>📐 <b>Click to see the layer flow diagram</b></summary>
Input Text
   │
   ▼
Embedding Layer  (vocab_size=10000, dim=150)
   │
   ▼
LSTM Layer  (128 units)
   │
   ▼
Dense Layer  (10000 units, softmax)
   │
   ▼
Predicted Next Word 🎉

</details>

🛠️ Getting Started

1️⃣ Clone the repo

bashgit clone https://github.com/sanskar-24-bit/<repo-name>.git
cd <repo-name>

2️⃣ Install dependencies

bashpip install -r requirements.txt

3️⃣ (Optional) Retrain the model

Run next_word_prediction.ipynb end-to-end to regenerate:
lstm_model.h5 · tokenizer.pkl · max_len.pkl

4️⃣ Launch the app

bashstreamlit run app.py

Open the local URL (usually http://localhost:8501) and start typing! ⌨️


📋 requirements.txt

streamlit
tensorflow
numpy


🎨 App Preview

┌─────────────────────────────────────────┐
│  🧠 Next Word Prediction (LSTM)          │
│                                           │
│  ✍️ Enter text: [ what are you        ]  │
│                                           │
│         [ Predict Next Word ]            │
│                                           │
│  ✅ Predicted Next Word: doing           │
└─────────────────────────────────────────┘


⚠️ Limitations

📚 Trained on a single-domain dataset (quotes) — predictions are strongest on similarly styled text
🔗 Single LSTM layer captures short/medium-range context, not long-range dependencies
❓ Out-of-vocabulary words are dropped during tokenization


🔮 Roadmap

 Expand training data across multiple text domains
 Add Bidirectional LSTM / GRU / Attention-based variants
 Replace greedy argmax decoding with top-k / temperature sampling
 Deploy live on Streamlit Community Cloud
