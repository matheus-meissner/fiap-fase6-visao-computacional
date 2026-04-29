# 🧠 Fase 6 — O Começo da Rede Neural
### FarmTech Solutions — Sistema de Visão Computacional para Detecção de EPIs

**Aluno:** Matheus Meissner | **RM:** 567080  
**Curso:** Inteligência Artificial — FIAP | **Fase:** 6

---

## 🎯 Sobre o Projeto

A **FarmTech Solutions** expandiu seus serviços de IA para a área de **segurança patrimonial de fazendas**, desenvolvendo um sistema de visão computacional capaz de identificar automaticamente se trabalhadores estão utilizando **capacetes de segurança (EPI)**.

O sistema classifica e localiza objetos em duas categorias:
- `helmet` — Pessoa utilizando capacete de segurança ✅
- `no_helmet` — Pessoa sem capacete de segurança ❌

### 💼 Aplicação Real
Fazendas e propriedades rurais enfrentam altos índices de acidentes por ausência de EPIs. Este sistema pode ser integrado a câmeras de monitoramento para **alertas em tempo real**, **logs de conformidade com a NR-6** e **redução de custos de fiscalização humana**.

---

## 📓 Notebook — Acesse aqui

> **👉 [MatheuseMeissner_rm567080_pbl_fase6.ipynb](./MatheuseMeissner_rm567080_pbl_fase6.ipynb)**

O notebook contém todo o passo a passo executado: código comentado, saídas, gráficos e análises críticas em Markdown. Está organizado em duas entregas:

### 🔵 Entrega 1 — YOLOv5 Customizado
- Preparação do ambiente e verificação de GPU
- Carregamento do dataset do Google Drive (80 imagens rotuladas via MakeSense.AI)
- Configuração do `data.yaml` com caminhos absolutos
- Treinamento com **30 épocas** — Simulação 1
- Treinamento com **60 épocas** — Simulação 2
- Comparação de métricas: mAP, Precision, Recall, Loss (9 gráficos)
- Inferência nas 8 imagens de teste com bounding boxes preditas
- Avaliação formal com `val.py` + Matriz de Confusão
- Análise crítica e conclusões

### 🔴 Entrega 2 — Comparação de Abordagens
- YOLO Padrão (pesos COCO, sem customização) — demonstração de limitação
- CNN treinada do zero (TensorFlow/Keras, 4 blocos convolucionais)
- Gráfico radar comparativo das 3 abordagens
- Análise crítica com recomendação técnica para a FarmTech

---

## 🏆 Resultados Obtidos

### Entrega 1 — YOLOv5 (30 vs 60 Épocas)

| Métrica | 30 Épocas | 60 Épocas |
|---------|-----------|-----------|
| mAP@0.5 | ~0.82 | **~0.91** |
| Precision | ~0.84 | **~0.90** |
| Recall | ~0.80 | **~0.89** |
| Tempo de treino | ~8 min | ~16 min |

### Entrega 2 — Comparação das 3 Abordagens

| Abordagem | Precisão | Localiza Objeto | Aplicabilidade |
|-----------|----------|-----------------|----------------|
| YOLOv5 Customizado | ✅ ~91% mAP | ✅ Sim (bbox) | ✅ Excelente |
| YOLO Padrão (COCO) | ❌ Inutilizável | ✅ Bbox errada | ❌ Inadequado |
| CNN do Zero | ⚠️ 50%* | ❌ Não | ⚠️ Parcial |

> *A CNN atingiu 50% de acurácia (equivalente a classificação aleatória) devido ao tamanho reduzido do dataset (32 imagens/classe) e ausência de Transfer Learning. Análise detalhada no notebook, seção 2.4.

---

## 🎬 Vídeo Demonstrativo

> **📹 [Assista no YouTube (não listado)](https://youtu.be/T6GcwftA5zk)**

---

## 📁 Estrutura do Repositório

```
📁 fase6-farmtech/
│
├── 📓 MatheuseMeissner_rm567080_pbl_fase6.ipynb  ← Notebook principal
│
├── 📁 resultados/
│   ├── dataset_amostras.png         # Amostras com bounding boxes (MakeSense.AI)
│   ├── comparacao_30vs60.png        # Curvas 30 vs 60 épocas (9 métricas)
│   ├── resultados_teste_yolo.png    # Detecções YOLOv5 nas imagens de teste
│   ├── confusion_matrix_yolo.png    # Matriz de confusão YOLO (teste)
│   ├── yolo_padrao_teste.png        # YOLO padrão COCO (sem customização)
│   ├── cnn_curvas.png               # Curvas de aprendizado CNN
│   ├── cnn_predicoes.png            # Predições da CNN no conjunto de teste
│   ├── cnn_confusion.png            # Matriz de confusão CNN
│   └── radar_comparativo.png        # Gráfico radar — 3 abordagens
│
└── 📄 README.md
```

---

## 🛠️ Como Executar

### Pré-requisitos
- Conta Google (Colab + Drive)
- GPU habilitada: `Runtime → Change runtime type → T4 GPU`

### Estrutura esperada no Google Drive
```
Meu Drive/
└── fase6_farmtech/
    └── dataset/
        ├── images/
        │   ├── train/   # 32 helmet + 32 no_helmet
        │   ├── val/     # 4 + 4
        │   └── test/    # 4 + 4
        └── labels/
            ├── train/   # .txt no formato YOLO
            ├── val/
            └── test/
```

### Execução
1. Abra o `.ipynb` no Google Colab
2. Ative a GPU: `Runtime → Change runtime type → T4 GPU`
3. Execute as células em ordem (Célula 1 → 20)
4. Os resultados são salvos automaticamente no Drive em `fase6_farmtech/resultados/`

---

## 📊 Tecnologias Utilizadas

| Tecnologia | Uso |
|------------|-----|
| YOLOv5 (Ultralytics) | Detecção de objetos customizada |
| TensorFlow / Keras | CNN treinada do zero |
| PyTorch | Backend do YOLOv5 |
| MakeSense.AI | Rotulação das imagens (formato YOLO) |
| Google Colab + Drive | Ambiente de treinamento (GPU T4) |
| Matplotlib / Seaborn | Visualizações e gráficos |

---

## 📚 Referências
1. Ultralytics YOLOv5 — https://github.com/ultralytics/yolov5
2. MakeSense.AI — https://www.makesense.ai
3. TensorFlow — https://tensorflow.org
4. Redmon et al. (2016) — *You Only Look Once: Unified, Real-Time Object Detection* — CVPR
5. FIAP — Material Redes Neurais, Capítulos 3 e 4

---

*Matheus Meissner | RM 567080 — FIAP Inteligência Artificial — Fase 6 — 2025*
