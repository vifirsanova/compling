# Transformer
## 3 типа внимания
### Encoder-Decoder Attention [(Bahdanau et al., 2014)](https://arxiv.org/abs/1409.0473)
* Моделирование контекста, нейросетевой аналог *выравнивнивания* из статистического машинного перевода.
* Конкатенация выходных представлений (эмбеддингов) кодера и весов внимания. *Веса внимания* отражают силу связи между каждым входным и выходным токеном.
* Позволяет выделить самые важные слова для перевода данного токена. Декодер получает на вход *контекстно-наполненное представление входных данных*.
### Dot Product Attention
* В основе - *матричные вычисления*, альтернатива последовательным операциям Encoder-Decoder Attention. Позволяет добиться большей распараллеливаемости.
* Данные представляются в виде трёх матриц: *Queries*, *Keys*, *Values*. В процессе исчилений методом обработного распространения ошибки матрицы взвешиваются - так мы оцениваем силу связи между токенами.
* Строительный блок для других, более сложных вычислений. Например, *Masked Dot Product Attention* используется для моделирования однонаправленных моделей (декодеров).
### Self Dot Product Attention [(Vaswani et al., 2017)](https://arxiv.org/abs/1706.03762)
* Матрицы *Queries*, *Keys*, *Values* содержат одни и те же данные. Так мы оцениваем силу связи между токенами внутри одной и той же последовательности.
* Позволяет производить *разрешение анафоры* и таким образом находить общеязыковые признаки, подтверждая дистрибутивную гипотезу Харриса. 
* Основа архитектуры *Transformer*. Поскольку модели обрабатывают большие квадратные матрицы, также применяется метод скалирования (Scaled Dot Product Attention). 
## 3 типа моделей
### Transformer encoder [(Devlin et al., 2018)](https://arxiv.org/abs/1810.04805)
* **Контекстуальные представления** входных последовательностей.
* **Задачи**: классификация последовательностей, анализ тональности, извлечение ответов на вопросы.
* **Пример**: BERT, стак кодеров для построения глубокого представления.
### Transformer decoder [(Radford et al., 2019)](https://openai.com/research/better-language-models)
* **Генерация последовательностей**, обусловленная закодированными представлениями входных данных.
* **Задачи**: генерация текста, диалоговые системы.
* **Пример**: GPT, декодер, создает глубокие представления для генерации текста.
### Transformer autoencoder [(Lewis et al., 2019)](https://arxiv.org/abs/1910.13461)
* **Комбинация кодера и декодера**, совместные представления для входных и выходных последовательностей.
* **Задачи**: суммаризация, машинный перевод.
* **Пример**: BART, аналог оригинального Transformer, обучался методом денойзинга, подходит для трансфера знаний.
## Transfer Learning
### Определение
* Применяем знания, полученные в процессе обучения исходной модели, для повышения производительности целевой модели.
* Преимущества: решение проблемы ограниченного ресурса, требуется меньше времени на тонкую настройку, высокое качество генерализации.
### Этапы:
* **Pre-training**: обучение большой модели на большом датасете открытой предметной области для генерализации знаний.
* **Fine-tuning**: тонкая настройка предобученной модели для решения конкретной задачи, небольшой датасет.
### Примеры:
* **CV:** обучаем ResNet на ImageNet открытой предметной области, тонко настраиваем на данных для распознавания лиц.
* **Robotics:** обучаем 3D-симуляцию робота, тонко настраиваем машину в физическом пространстве.
* **NLP:** обучаем BERT, тонко настраивает модель для извлечения ответов на вопросы.
## RLHF 
### Определение
* Reinforcement Learning for Human Feedback (RLHF), метод разработки больших языковых моделей на основе отзывов людей; использует элементы обучения с подкреплением.
* Преимущества: отзывы людей помогают "выравнивать" выдачи модели с намерением пользователя, выраженном в его промпте.
### Этапы:
* **Данные:** генерация текстов с помощью большой языковой модели на разных промптах.
* **Ранжирование:** тексты ранжируются на основе предпочтений людей.
* **Политики:** обучаем модель с подкреплением, учим агента выбирать действия, которые приведут к генерации текста, который понравится пользователю.
### Примеры:
* [OpenAI ChatGPT](https://openai.com/research/instruction-following)
* [Gemini](https://gemini.google.com/)
* [LoRA](https://www.microsoft.com/en-us/research/publication/lora-low-rank-adaptation-of-large-language-models/)