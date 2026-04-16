# 2025-2026 Bahar Dönemi Makine Öğrenmesine Giriş Dersi Sunum Konuları

---

## Önemli Not:
Tüm makine öğrenmesi çalışmaları Tensorflow kütüphanesi kullanılarak yapılacaktır.   
Sunum konusunu ilk seçen 1. proje çalışimasını, ikinci seçen ise 2. proje çalışmasını yapacaktır.


## Sunum 1: Makine Öğrenmesine Giriş ve Model Değerlendirme

- Sunacak Öğrenci Sayısı: 2
- 10\. hafta

### 1. ML Pipeline (End-to-End Süreç)
- Veri → Model → Değerlendirme → İyileştirme

### 2. Veri Bölme Stratejileri
- Train / Val / Test
- K-Fold Cross Validation

### 3. Bias – Variance
- Underfitting / Overfitting
- Trade-off

### 4. Model Değerlendirme Metrikleri
- Accuracy, Precision, Recall, F1
- Regression metrikleri (MSE, MAE)

### 5. Temel ML Reçetesi
- Bias nasıl düşürülür?
- Variance nasıl düşürülür?

### Mini Projeler
1. Train/val/test split yaparak model performansını analiz edin  
2. Overfitting gösterimi (küçük vs büyük model)  
<!-- 3. Farklı metriklerin (Accuracy vs F1) karşılaştırılması  -->

---

## Sunum 2: Regularization ve Model Genelleme

- Sunacak Öğrenci Sayısı: 2
- 10\. hafta

### 1. Regularization Temelleri
- Overfitting problemi

### 2. L1 / L2 Regularization
- Weight decay

### 3. Dropout

### 4. Data Augmentation

### 5. Early Stopping

### 6. Model Kapasitesi vs Veri İlişkisi

### Mini Projeler
1. Dropout etkisinin incelenmesi  
2. L2 regularization etkisi  
<!-- 3. Data augmentation ile performans artışı   -->

---

## Sunum 3: Model Eğitimi ve Optimizasyon

- Sunacak Öğrenci Sayısı: 2
- 10\. hafta

### 1. Normalizasyon
- Input scaling

### 2. Gradient Problemleri
- Vanishing / Exploding gradients

### 3. Weight Initialization

### 4. Gradient Descent Türleri
- Batch / Mini-batch / SGD

### 5. Learning Rate ve Batch Size

### 6. Gelişmiş Optimizasyon Algoritmaları
- Momentum
- RMSprop
- Adam

### 7. Learning Rate Scheduling
- Step decay
- Exponential decay
- Cosine annealing (kavramsal)

### Mini Projeler
1. Farklı optimizer karşılaştırması  
2. Learning rate değişiminin etkisi

---

## Sunum 4: Hiperparametre ve Modern Eğitim Teknikleri

- Sunacak Öğrenci Sayısı: 2
- 10\. hafta

### 1. Hiperparametre Tuning
- Grid Search
- Random Search

### 2. Batch Normalization

### 3. Softmax ve Çok Sınıflı Sınıflandırma

### 4. Experiment Tracking
- MLflow / Weights & Biases (kavramsal)

### 5. Data Leakage

### Mini Projeler
1. Random search ile tuning  
2. BatchNorm etkisinin analizi 

---

## Sunum 5: Model İyileştirme ve Transfer Öğrenme

- Sunacak Öğrenci Sayısı: 2
- 11\. hafta

### 1. Error Analysis

### 2. Distribution Shift

### 3. Transfer Learning

### 4. Multi-task Learning

### 5. Fine-tuning vs Feature Extraction

### 6. Fine-tuning Stratejileri
- Freeze layers
- Partial training

### Mini Projeler
1. Pretrained model ile feature extraction  
2. Fine-tuning uygulaması  
<!-- 3. Freeze vs full training karşılaştırması  -->

---

## Sunum 6: CNN Temelleri

- Sunacak Öğrenci Sayısı: 2
- 11\. hafta

### 1. Convolution Mantığı

### 2. Padding ve Stride

### 3. CNN Katman Yapısı

### 4. Pooling

### 5. Basit CNN Mimarisi

### Mini Projeler
1. MNIST CNN modeli  
2. Farklı kernel boyutlarının etkisi  
<!-- 3. Pooling türlerinin karşılaştırılması  -->

---

## Sunum 7: Modern CNN Mimarileri

- Sunacak Öğrenci Sayısı: 2
- 11\. hafta

### 1. LeNet / AlexNet / VGG

### 2. ResNet

### 3. Inception

### 4. MobileNet

### 5. EfficientNet

### Mini Projeler
1. Pretrained model ile inference  
2. Farklı mimarilerin karşılaştırılması  

---

---

## Sunum 8a: Görüntü İşleme Teknikleri

- Sunacak Öğrenci Sayısı: 2
- 11\. hafta

### 1. Data Augmentation

### 2. Transfer Learning (Computer Vision)

### 3. Object Localization

### 4. Sliding Window ve CNN dönüşümü

### Mini Proje
- Basit bir bounding box tahmin modeli oluşturun


---

## Sunum 8: Object Detection (Modern Yaklaşım)

- Sunacak Öğrenci Sayısı: 2
- 11\. hafta

### 1. YOLO

### 2. Intersection over Union (IoU)

### 3. Non-Max Suppression (NMS)

### 4. Anchor Boxes

### 5. mAP (mean Average Precision)

### Mini Projeler
1. YOLO ile nesne tespiti  
2. Farklı confidence threshold analizi  
<!-- 3. IoU hesaplama uygulaması   -->

---

## Sunum 9: Segmentation ve Encoder-Decoder

- Sunacak Öğrenci Sayısı: 2
- 12\. hafta

### 1. Semantic Segmentation

### 2. U-Net

### 3. Encoder-Decoder Mimarisi

### 4. Transpose Convolution

### Mini Projeler
1. U-Net ile segmentation  
2. Mask görselleştirme  
<!-- 3. Augmentation etkisi  -->

---

## Sunum 10: Face Recognition ve Metric Learning

- Sunacak Öğrenci Sayısı: 2
- 12\. hafta

### 1. One-shot Learning

### 2. Siamese Networks

### 3. Triplet Loss

### 4. Embedding Mantığı

### Mini Projeler
1. Embedding çıkarımı  
2. Cosine similarity uygulaması  
<!-- 3. Basit yüz doğrulama sistemi   -->

---

## Sunum 11: Generative Modeller

- Sunacak Öğrenci Sayısı: 2
- 12\. hafta

### 1. Autoencoders

### 2. Variational Autoencoders (VAE)

### 3. Generative Adversarial Networks (GAN)

### 4. Super Resolution

### 5. Latent Space Kavramı

### Mini Projeler
1. Autoencoder reconstruction  
<!-- 2. VAE latent space görselleştirme   -->
2. GAN ile görüntü üretimi  

---

## Sunum 12: Sequence Models (RNN)

- Sunacak Öğrenci Sayısı: 2
- 13\. hafta

### 1. Sequence Türleri

### 2. RNN

### 3. BPTT

### 4. RNN Problemleri

### 5. Gradient Clipping

### Mini Projeler
1. Text classification (RNN)  
2. Time series tahmini  
<!-- 3. Gradient clipping etkisi  -->

---

## Sunum 13: Gelişmiş RNN Yapıları

- Sunacak Öğrenci Sayısı: 2
- 13\. hafta

### 1. GRU

### 2. LSTM

### 3. Bidirectional RNN

### 4. Deep RNN

### Mini Projeler
1. LSTM ile model  
2. RNN vs LSTM karşılaştırma 

---

## Sunum 14: Word Embeddings

- Sunacak Öğrenci Sayısı: 2
- 13\. hafta

### 1. One-hot vs Embedding

### 2. Word2Vec

### 3. GloVe

### 4. Cosine Similarity

### 5. Contextual Embeddings'e Giriş

### Mini Projeler
1. Benzer kelime bulma  
2. Embedding görselleştirme (TSNE)  

---

## Sunum 15: Seq2Seq ve Attention

- Sunacak Öğrenci Sayısı: 2
- 13\. hafta

### 1. Encoder-Decoder

### 2. Beam Search

### 3. BLEU Score

### 4. Attention Mekanizması

### 5. Teacher Forcing

### 6. Perplexity

### Mini Projeler
1. Basit çeviri modeli  
2. Attention görselleştirme  

---

## Sunum 16: Transformer ve Modern NLP

- Sunacak Öğrenci Sayısı: 2
- 14\. hafta

### 1. Transformer

### 2. Self-Attention

### 3. Multi-head Attention

### 4. Positional Encoding

### 5. BERT ve GPT genel bakış

### Mini Projeler
1. HuggingFace inference  
2. Attention weight görselleştirme  
<!-- 3. Küçük fine-tuning denemesi   -->

---

## Sunum 17: Büyük Dil Modelleri (LLM)

- Sunacak Öğrenci Sayısı: 2
- 14\. hafta

### 1. LLM Nedir?

### 2. Pretraining vs Fine-tuning

### 3. Prompt Engineering

### 4. Hugging Face Kullanımı

### 5. Fine-tuning (LoRA vb.)

### 6. Inference Teknikleri
- Temperature
- Top-k / Top-p sampling

### Mini Projeler
1. Prompt engineering deneyi  
2. Küçük model fine-tuning  

---

## Sunum 18: RAG
- Sunacak Öğrenci Sayısı: 2
- 14\. hafta

### 1. RAG Nedir?

### 2. Embedding ve Vector Database

### 3. Retrieval Süreci

### 4. RAG vs Fine-tuning

### Mini Projeler
1. PDF QA sistemi  
2. Embedding karşılaştırma  

---

## Sunum 19: AI Agents

- Sunacak Öğrenci Sayısı: 2
- 14\. hafta

### 1. Agent Kavramı

### 2. Tool Kullanımı

### 3. Planning ve Reasoning

### 4. Multi-agent Sistemler

### 5. Gerçek Dünya Uygulamaları

### Mini Projeler
1. Tool-calling agent  
2. Basit görev planlayan agent  