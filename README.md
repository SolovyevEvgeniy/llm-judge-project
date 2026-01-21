# llm-judge-project

Быстрый старт
1. Установка зависимостей
bash
# Создание виртуального окружения
python -m venv venv
source venv/bin/activate  # Linux/Mac
# или .\venv\Scripts\activate  # Windows

# Установка пакетов
pip install -r requirements.txt
2. Запуск vLLM сервера
bash
# Запуск на CPU
vllm serve Qwen/Qwen2-0.5B-Instruct \
    --host 0.0.0.0 \
    --port 8000 \
    --dtype float32 \
    --device cpu
3. Проверка работы сервера
bash
curl http://localhost:8000/health
Ожидаемый ответ: {"status":"healthy"}

4. Запуск демонстрационных скриптов
bash
# Тест взаимодействия с vLLM
python vllm_interaction.py

# Запуск эксперимента MLflow
python mlflow_experiment.py
5. Просмотр результатов в MLflow
bash
mlflow ui --port 5000
Откройте в браузере: http://localhost:5000

Структура проекта
text
hometask/
├── vllm_interaction.py     # Скрипт взаимодействия с vLLM
├── mlflow_experiment.py    # Эксперимент с метриками LLM-as-Judge
├── requirements.txt        # Зависимости Python
└── README.md              # Эта инструкция

Что оценивается
Метрика LLM-as-Judge проверяет ответы по шкале 1-5 на основе:
Релевантность — отвечает ли на вопрос
Точность — корректность информации
Четкость — структурированность ответа

Технические детали
Модель: Qwen2-0.5B-Instruct (оптимизирована для CPU)
API: Совместим с OpenAI API
Сервер: vLLM на порту 8000
Мониторинг: MLflow на порту 5000

