# LLM + OpenAI API hosted on Kaggle
[Kaggle Notebook](https://www.kaggle.com/code/antonchernov/llm-openai-api?scriptVersionId=196999610)

Запуск любой достаточно маленькой open-source LLM в облаке.

Использует uvicorn + localtunnel для создания временного хостинга, Unsloth для быстрого инференса.

## Запуск
1. Установить зависимости ~5 min
2. Выбрать модель в разделе `Load models`
3. Прогнать все ячейки разделов `Load models`, `Completions`, `Embeddings`, `Chat completions`
5. Запустить хостинг в разделе `Launch API`, указав как можно более уникальное доменное имя `SUBDOMAIN`

## Поддерживаемые эндпоинты
* `POST /v1/chat/completions`

  ```
  curl -X POST "https://very-unique-sub-domain.loca.lt/v1/completions" \
     -H "Content-Type: application/json" \
     -d '{"prompt": "Why is sky blue?", "max_tokens": 100}'
  ```
  <details>
    <summary>Пример ответа</summary>
    <img src="https://github.com/user-attachments/assets/866d76f4-6b3c-478c-9e58-a050cc4b9a57">

  </details>
  
* `POST /v1/completions`
  ```
  curl -X POST "https://very-unique-sub-domain.loca.lt/v1/chat/completions" \
     -H "Content-Type: application/json" \
     -d '{
          "messages": [
              {"role": "system", "content": "Always answer in rhythmes."},
              {"role": "user", "content": "Why is sky blue?"}
          ],
          "max_tokens": 30,
          "temperature": 1,
          "n": 2
     }'
  ```
  <details>
    <summary>Пример ответа</summary>
    <img src="https://github.com/user-attachments/assets/675d3ed9-0536-4649-8aeb-0d3014cec6e0">
  </details>
  
* `POST /v1/embeddings `
  ```
  curl -X POST "http://very-unique-sub-domain.loca.lt/v1/embeddings" \
     -H "Content-Type: application/json" \
     -d '{
           "input": [
             "The quick brown fox jumps over the lazy dog.",
             "Hello, world!",
             "This is a test sentence."
           ]
         }'
  ```        
