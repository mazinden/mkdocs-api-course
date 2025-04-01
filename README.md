# mkdocs-api-course

## Описание

Репозиторий демонстрирует базовую настройку документации с использованием [MkDocs](https://www.mkdocs.org/) и темы [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/), а также интеграцию [Swagger UI](https://swagger.io/tools/swagger-ui/download/) и [Яндекс Метрики](https://metrika.yandex.ru/).

## Структура проекта

mkdocs-api-course/
├── docs/                      
│   ├── index.md                    # Главная страница документации
│   ├── openapi.yaml                # OpenAPI спецификация
│   └── dist/                       # Swagger UI со счётчиком Яндекс Метрики
│       ├── index.html              # Встроенный Swagger UI
│       └── swagger-initializer.js  # Указание пути к openapi.yaml
├── overrides/
│   └── main.html                   # Шаблон с Яндекс Метрикой
├── mkdocs.yml                      # Конфигурационный файл MkDocs
└── README.md                       # Описание проекта
