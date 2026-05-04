# 🧠 English → French Neural Machine Translation

**Seq2Seq (Encoder–Decoder) using LSTM | TensorFlow**

A baseline Neural Machine Translation (NMT) system that converts English to French using a **Seq2Seq model without attention**.

---

# 🚀 Overview

Machine translation = sequence-to-sequence problem:

- Input → English sentence  
- Output → French sentence  

Pipeline:

- Preprocessing & tokenization  
- LSTM Encoder–Decoder  
- Teacher forcing  
- Custom training loop  
- Inference system  

---

# 🧩 Core Idea
```
English → Encoder → Context Vector → Decoder → French
```

- Encoder compresses input  
- Decoder generates output step-by-step  
- No attention → single-vector bottleneck  

---

# 📊 Dataset

- English–French parallel corpus (Kaggle)  
- Aligned sentence pairs (EN ↔ FR)  
- Loaded via `kagglehub`  

---

# ⚙️ Preprocessing

- Lowercasing & cleaning  
- `<start>`, `<end>` tokens  
- Tokenization (separate vocabularies)  
- Padding for fixed-length sequences  

---

# 🏗️ Model

**Encoder:** Embedding + LSTM  
**Decoder:** Embedding + LSTM + Dense  

**Why LSTM?**

- Handles long dependencies  
- More stable than GRU  

---

# 🔁 Training

- **Teacher Forcing** → faster, stable learning  
- **Loss:** Sparse Categorical Crossentropy  
- **Optimizer:** Adam + GradientTape  

---

# 📉 Training Behavior

- Loss: ~3–4 → decreases over epochs  

Red flags:

- Flat loss → not learning  
- NaN → preprocessing/gradient issue  

---

# 📏 Evaluation

**BLEU Score**

- Measures n-gram overlap  
- Doesn’t capture true meaning  

---

# 🔮 Inference

- No ground truth  
- Predict token-by-token  

Steps:

1. Encode input  
2. Start with `<start>`  
3. Predict → feed back  
4. Stop at `<end>`  

---

# 🧪 Example
```
Input: "he is running"
Output: "il court"
```

Works well for short sentences.

---

# ⚠️ Limitations

- No attention → bottleneck  
- Weak on long/complex sentences  
- Limited context understanding  

---

# 🚀 Next Step: Attention

- Focus on relevant encoder states  
- Better fluency & long-sequence handling  

---

# 🧠 Takeaway

End-to-end NMT pipeline:

**Text → Model → Translation**

Foundation for modern NLP systems.
