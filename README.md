# MLOps Homework 1

**Repository**: https://github.com/alexgeen896-stack/mlops_hw1_Samarets_Sergey

## Цель проекта
Построение минимального MLOps-контура с воспроизводимостью экспериментов, контролем версий данных и моделей, автоматизацией процесса обучения.

## Структура проекта
```
mlops_hw1/
├── data/
│   ├── raw/           # Исходные данные (версионируются через DVC)
│   └── processed/     # Обработанные данные
├── src/
│   ├── prepare.py     # Подготовка данных
│   └── train.py       # Обучение модели
├── dvc.yaml          # Описание пайплайна
├── params.yaml       # Гиперпараметры
├── requirements.txt  # Зависимости
└── README.md         # Документация
```

## Как запустить

```bash
# 1. Клонировать репозиторий
git clone https://github.com/alexgeen896-stack/mlops_hw1_Samarets_Sergey.git
cd mlops_hw1_Samarets_Sergey

# 2. Установить зависимости
pip install -r requirements.txt

# 3. Загрузить данные через DVC
dvc pull

# 4. Запустить весь пайплайн
dvc repro

# 5. Запустить MLflow UI (опционально)
mlflow ui --backend-store-uri sqlite:///mlflow.db
```

## Описание пайплайна

### Стадия prepare
- Загрузка датасета Iris
- Разделение на train/test (80/20)
- Сохранение обработанных данных

### Стадия train  
- Обучение модели логистической регрессии
- Логирование параметров и метрик в MLflow
- Сохранение модели

## MLflow UI
Для просмотра экспериментов:
```bash
mlflow ui --backend-store-uri sqlite:///mlflow.db
```
Открыть: http://localhost:5000

## Воспроизводимость
Проект полностью воспроизводим:
```bash
git clone <repo>
cd <repo>
pip install -r requirements.txt
dvc pull
dvc repro
```
Результат: модель обучается с accuracy ~0.9667