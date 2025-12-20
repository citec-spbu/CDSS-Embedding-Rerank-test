## Развертывание

```bash
docker-compose up -d
```

## Критерии выбора моделей
- Скорость работы
- Качество работы
- Умеренный размер модели
- Работа с русским языком


## Embedding model
Была использована [модель](https://huggingface.co/jinaai/jina-embeddings-v3) от JinaAI с оберткой `FastAPI`.

Её выбор был обусловлен тем, что она поддерживает `cpu` и `gpu` и имеет относительно небольшой размер. При этом, обеспечивая высокую скорость работы и удовлеворительное качество для русского языка, как следует из данной [статьи](https://arxiv.org/abs/2409.10173).

После развертывания полная документация доступна по [ссылке](http://localhost:8000/docs).

#### NOTE:
 - На данный момент использует только `cpu`, под инференс модели с `gpu` следует использовать базовый образ с поддержкой `cuda`

## Re-rank model
Использована [модель](https://huggingface.co/cross-encoder/ms-marco-MiniLM-L12-v2) типа `cross-encoder` с оберткой `FastAPI`.

Выбор `cross-encoder` архитектуры обусловлен её лучшими результатами по сравнению с `bi-encoder` моделью в данном случае реранка. Об этом говорится в исследовании [Beyond Retrieval: Ensembling Cross-Encoders and GPT Rerankers with LLMs for Biomedical QA](https://arxiv.org/abs/2507.05577) и [Learning to Fuse Retrieval Signals: A Lightweight Meta Relevance Classifier for RAG Pipelines](https://www.sciencedirect.com/science/article/pii/S187705092502753X).

После развертывания полная документация доступна по [ссылке](http://localhost:8001/docs).