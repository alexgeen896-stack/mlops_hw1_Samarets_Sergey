# MLOps Homework 1

**Repository**: https://github.com/alexgeen896-stack/mlops_hw1_Samarets_Sergey

## Цель проекта
Построение минимального MLOps-контура с воспроизводимостью экспериментов, контролем версий данных и моделей, автоматизацией процесса обучения.

## Структура проекта

<pre>
mlops_hw1/
├── data/
│   ├── raw/           # Исходные данные (Iris dataset)
│   └── processed/     # Обработанные данные (создаются пайплайном)
├── src/
│   ├── prepare.py     # Подготовка данных
│   └── train.py       # Обучение модели
├── dvc.yaml          # Описание пайплайна
├── params.yaml       # Гиперпараметры
├── requirements.txt  # Зависимости
└── README.md         # Документация
</pre>

## Как запустить

1. Клонировать репозиторий
git clone https://github.com/alexgeen896-stack/mlops_hw1_Samarets_Sergey.git
cd mlops_hw1_Samarets_Sergey

2. Установить зависимости
pip install -r requirements.txt

3. Запустить весь пайплайн
dvc repro

4. Запустить MLflow UI (опционально)
mlflow ui --backend-store-uri sqlite:///mlflow.db

## Описание пайплайна

### Стадия prepare
- Загрузка датасета Iris из data/raw/data.csv
- Разделение на train/test (80/20)
- Сохранение обработанных данных в data/processed/

### Стадия train  
- Обучение модели логистической регрессии
- Логирование параметров и метрик в MLflow
- Сохранение модели как model.pkl

## MLflow UI
Для просмотра экспериментов:
mlflow ui --backend-store-uri sqlite:///mlflow.db

Открыть: http://localhost:5000

Показывает:
- **Параметры**: model_type, random_state
- **Метрики**: accuracy
- **Артефакты**: модель, отчеты

## Воспроизводимость
Проект полностью воспроизводим:

git clone <repo>
cd <repo>
pip install -r requirements.txt
dvc repro

**Результат**: модель обучается с accuracy ~0.9667

## Технологии
- **Git** - контроль версий кода
- **DVC** - управление пайплайнами
- **MLflow** - трекинг экспериментов  
- **Scikit-learn** - машинное обучение
- **Pandas** - обработка данных

## Особенности
- Датасет Iris хранится непосредственно в Git (малый размер)
- Все параметры вынесены в params.yaml
- Пайплайн автоматизирован через DVC
- Эксперименты логируются в MLflow
