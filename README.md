# Приложение AI Chat

Чат-приложение, использующее API OpenRouter для взаимодействия с различными моделями искусственного интеллекта.

## Начало работы

### Установка и настройка

1. **Установка необходимого ПО**
   - Установите [Git](https://git-scm.com/downloads)
   - Установите [Python 3.9+](https://www.python.org/downloads/)
   - Установите [Visual Studio Code](https://code.visualstudio.com/download)

2. **Клонирование проекта**
   ```bash
   # Клонируйте репозиторий
   git clone https://github.com/neuro-fill/51-lesson.git
   # Перейдите в директорию проекта
   cd 51-lesson
   ```

3. **Настройка VSCode**
   - Откройте VSCode
   - Установите рекомендуемые расширения:
     - Python (ms-python.python)
     - Python Environment Manager
     - Python Extension Pack
   - Откройте проект: File -> Open Folder -> выберите папку 51-lesson
   - Выберите интерпретатор Python: 
     1. Нажмите F1 или Ctrl+Shift+P
     2. Введите "Python: Select Interpreter"
     3. Выберите Python 3.9 или выше

4. **Настройка виртуального окружения**
   ```bash
   # Создание виртуального окружения
   python -m venv venv
   
   # Активация виртуального окружения
   # Для Windows:
   .\venv\Scripts\activate
   # Для Linux/Mac:
   source venv/bin/activate
   ```

5. **Настройка переменных окружения**
   - Скопируйте файл `.env.example` в новый файл `.env`
   - Откройте `.env` и замените `your_api_key_here` на ваш API ключ OpenRouter
   - Остальные настройки можно оставить по умолчанию

## Сборка приложения

### Требования

- Python 3.9 или выше

### Сборка для Windows

1. Установка зависимостей:
```bash
pip install -r requirements.txt
```

2. Сборка исполняемого файла:
```bash
python build.py
```

Исполняемый файл будет создан по пути `bin/AIChat.exe`

### Сборка для Linux

1. Установка зависимостей:
```bash
pip install -r requirements.txt
```

2. Сборка исполняемого файла:
```bash
python3 build.py
```

Исполняемый файл будет создан по пути `bin/aichat`

3. Установка прав на выполнение:
```bash
chmod +x bin/aichat
```

## Конфигурация

Создайте файл `.env` в корневой директории со следующим содержимым:
```
OPENROUTER_API_KEY=ваш_api_ключ
BASE_URL=https://openrouter.ai/api/v1
DEBUG=False
LOG_LEVEL=INFO
MAX_TOKENS=1000
TEMPERATURE=0.7
```

## Структура проекта

```
├── assets/                # Ресурсы приложения
│   └── icon.ico           # Иконка приложения
├── bin/                   # Скомпилированные исполняемые файлы
├── build/                 # Временные файлы сборки
├── exports/               # Директория для экспортированных чатов
├── logs/                  # Логи приложения
├── src/                   # Исходный код
│   ├── api/               # API интеграции
│   │   ├── __init__.py
│   │   └── openrouter.py  # Взаимодействие с OpenRouter API
│   ├── ui/                # Пользовательский интерфейс
│   │   ├── __init__.py
│   │   ├── components.py  # UI компоненты
│   │   └── styles.py      # Стили интерфейса
│   ├── utils/             # Утилиты
│   │   ├── __init__.py
│   │   ├── analytics.py   # Аналитика использования
│   │   ├── cache.py       # Кэширование
│   │   ├── logger.py      # Система логирования
│   │   └── monitor.py     # Мониторинг системы
│   ├── main_simple.py     # Упрощенная версия main.py с урезанным функционалом
│   └── main.py            # Точка входа приложения
├── .env.example           # Пример конфигурации
├── .gitignore             # Исключения Git
├── build.py               # Скрипт сборки
├── requirements.txt       # Зависимости Python
└── README.md              # Документация
```

## Подробное описание функционала

### Основные возможности

1. **Чат с AI моделями**
   - Поддержка различных моделей через OpenRouter API
   - Контекстные диалоги с сохранением истории
   - Настраиваемые параметры генерации (температура, максимальное количество токенов)

2. **Управление историей чатов**
   - Автоматическое сохранение истории диалогов
   - Возможность просмотра предыдущих бесед
   - Экспорт диалогов в различные форматы

3. **Аналитика использования**
   - Отслеживание использования различных моделей
   - Статистика по количеству запросов
   - Мониторинг потребления токенов

4. **Системные функции**
   - Кэширование для оптимизации производительности
   - Подробное логирование работы приложения
   - Мониторинг системных ресурсов

### Технические особенности

- **Кэширование (utils/cache.py)**
  - Локальное хранение истории чатов
  - Оптимизация повторяющихся запросов
  - Управление размером кэша

- **Логирование (utils/logger.py)**
  - Настраиваемые уровни логирования
  - Ротация лог-файлов
  - Детальная информация об ошибках

- **Аналитика (utils/analytics.py)**
  - Сбор статистики использования
  - Анализ популярности моделей
  - Отчеты по использованию ресурсов

- **Мониторинг (utils/monitor.py)**
  - Отслеживание производительности
  - Контроль использования системных ресурсов
  - Уведомления о критических событиях

- **Пользовательский интерфейс (ui/)**
  - Современный дизайн
  - Настраиваемые темы оформления
  - Адаптивный интерфейс

- **API интеграция (api/)**
  - Безопасное взаимодействие с OpenRouter
  - Обработка ошибок и повторные попытки
  - Поддержка различных моделей AI (более 215 моделей, в том числе более 20-ти бесплатных)
