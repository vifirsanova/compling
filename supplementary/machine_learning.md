# Шпаргалка по машинному обучению
*курс В.И. Фирсановой по компьютерной лингвистике НИУ ВШЭ СПб*

## Теорема Байеса (Томас Байес (1702 - 1761))
- **Определение:** теорема теории вероятности, позволяет предсказать некое событие с определенной степенью вероятности на основе предварительных (априорных) знаний или условий, относящихся к нему.
- **Пример:** теорема Байеса может использоваться для поиска спама на основе наличия в электронном письме определенных слов.
- **Формула:** P(A|B) = ( P(B|A) P(A) ) / P(B)

Где:
- P(A|B) - вероятность события A, когда событие B произошло
- P(B|A) - вероятность событитя B, когда событие A произошло
- P(A) - априорная вероятность события A
- P(B) - априорная веростность события B

## Искусственный интеллект
- **Базы знаний:** форма представления знаний в формате графа, используется для создания правил для извлечения информации и принятия решений с помощью автоматической системы (пример: *Cyc*)
- **Машинное обучение:** система, которая учится решать задачу (учится предсказывать наиболее вероятное ее решение) на основе данных без программирования конкретных правил (пример: *логистическая регрессия для классификации признаков*)
- **Глубокое обучение:** разновидность машинного обучения; множество слоев искусственных нейронных сетей используются для решения задач, требующих абстрактного представления (пример: *сверточная нейронная сеть для автоматического распознавания рукописных цифр*)

## Машинное обучение vs классическое программирование
- **Классическое программирование:** эксплицитно прописывает этапы решения задачи (например, создаем правила, описывающие морфологию естественного языка, для автоматизации частеречной разметки)
- **Машинное обучение:** можно назвать "моделированием интуитиции"; на основе данных (изображения, тексты, таблицы и т.д.) модель учится делать обобщения и извлекать паттерны, чтобы делать предсказания или принимать решения (например, определять классы тональности текстов или выделять тематические кластеры)

## Три типа машинного обучения
- **С учителем (Supervised Learning):** модель извлекает признаки из размеченных данных (пример данных: *{Текст: "Я ненавижу тебя!; Метка: "Негативный сентимент"}*; пример алгоритма для решения задачи: *сверточная нейронная сеть*) 
- **Самоконтролируемое обучение (Self-Supervised Learning):** используется в языковых моделях (таких как GPT); данные играют роль обучающего материала и меток одновременно (пример данных: *{Текст: "Привет! Как твои дела? Давно не..."}*, пример алгоритма для решения задачи: *рекуррентная нейронная сеть*) 
- **Без учителя (Unsupervised Learning):** модель извлекает признаки из неразмеченных данных, чтобы обнаружить скрытые паттерны и структуры (пример данных: *набор изображений для извлечения основных цветов*, пример алгоритма для решения задачи: *К-средних*)
- **Обучение с подкреплением (Reinforcement Learning):** модель (агент) взаимодействует со средой и выучивает политики в процессе максимизации подкрепления; подкрепление может быть положительным или отрицательным в зависимости от приближения агента к цели (пример: *обучение моделей в среде аркадных игр Atari*)

## Словарик учителя нейросетей
- **Слои:** объединенные комплексы искусственных нейронов для обработки входных данных
- **Параметры:** обучаемые переменные, которые описывают признаки, характерные для заданных классов, кластеров и т.д.
- **Weights & Biases (веса и смещение):** параметры, которые настраиваются автоматически в процессе обучения нейросети; определяют силу связи между нейронами (признаками) и помогают находить паттерны в данных
- **Гиперпараметры:** конфигурация модели; параметры, которые задаются прежде, чем начинается обучение, и определяют процесс обучения (например, *скорость обучения (learning rate)*, *размер окна (для эмбеддингов)*, *количество эпох обучения*)
- **Функция потерь:** оценка разницы между предсказанными моделью и заданными в обучающих данных метками; в процессе обучения мы стремимс минимизировать потери
- **Оптимизация:** процесс настройки весов (weights) для минимизации потерь в ходе обучения
- **Градиентный спуск:** алгоритм оптимизации, который обновляет (настраивает) веса на основе градиента (направления вектора) функции потерь

## Выборки для машинного обучения
- **Обучающая выборка (Train Set):** на этих данных модель обучается, обычно составляет 60% всех данных
- **Проверочная выборка (Validation Set / Dev Set):** с помощью этих данных мы оцениваем производительность (с помощью *метрик оценки*) модели в ходе обучения, ~20% всех данных
- **Тестовая выборка (Test Set):** эти данные мы используем, чтобы оценить итоговую производительность модели после ее обучения, ~20% данных

## Генерализация
- **Переобучение (Overfitting):** модель выучила не только общие черты, но и *шум* обучающих данных; такая модель не модель не может делать предсказания для *не виденных ранее* данных; высокая производительность на обучающих данных, низкая - на тестовых
- **Недообучение (Underfitting):** модель не научилась находить обобщения в данных, скрытые структуры, паттерны; низкая производительность на обучающих и тестовых данных
- **Оптимальное решение (Capacity):** модель нашла паттерны, которые помогают маштабировать решение и адаптироваться под новые, не виденные ранее данные; высокая производительность на обучающих и тестовых данных
