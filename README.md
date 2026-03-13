# Avaliação Comparativa de Modelos de Question Answering

Projeto da disciplina de Processamento de Linguagem Natural — CTEIA/UFC.

Avaliação comparativa entre dois modelos de *extractive question answering* pré-treinados no SQuAD 2.0, aplicados sobre um dataset de 1.000 exemplos.

---

## Modelos Avaliados

| Modelo | Parâmetros | Base |
|--------|-----------|------|
| [deepset/tinyroberta-squad2](https://huggingface.co/deepset/tinyroberta-squad2) | ~82M | RoBERTa distilado |
| [deepset/bert-base-uncased-squad2](https://huggingface.co/deepset/bert-base-uncased-squad2) | ~110M | BERT Base |

---

## Dataset

`shard_017.csv` — 1.000 exemplos com pares de contexto e pergunta em inglês, carregado diretamente do repositório.

---

## Critérios de Avaliação

| Critério | Descrição |
|----------|-----------|
| **A** | Tamanho médio das perguntas (query) |
| **B** | Score médio de confiança dos modelos |
| **C** | Overlap entre contexto e resposta (verificação de alucinação) |
| **D** | Análise qualitativa por amostragem guiada (10 melhores, 10 piores e 5 exemplos divergentes por modelo) |

---

## Resultados

| Métrica | TinyRoBERTa | BERT Base |
|---------|------------|-----------|
| Score médio | **0.365** | 0.291 |
| Overlap médio | 99.57% | **99.71%** |

O TinyRoBERTa apresentou score médio superior em todos os subconjuntos analisados. Ambos os modelos mantiveram overlap próximo a 100%, confirmando o comportamento extractivo — as respostas são extraídas diretamente do contexto, sem geração de texto livre.

---

## Dependências
```bash
pip install transformers pandas numpy matplotlib seaborn tqdm
```

---

## Autor

**Guilherme Hermano de Paula Ferreira**  
CTEIA — Universidade Federal do Ceará
