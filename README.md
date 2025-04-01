# mkdocs-api-course

## Описание

Репозиторий демонстрирует базовую настройку документации с использованием [MkDocs](https://www.mkdocs.org/) и темы [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/), а также интеграцию [Swagger UI](https://swagger.io/tools/swagger-ui/download/) и [Яндекс Метрики](https://metrika.yandex.ru/).

Сайт опубликован по адресу: https://mazinden.github.io/mkdocs-api-course/

## Структура проекта

```
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
```

## Подключение счетчика

1. **Создайте счётчик Яндекс Метрики**

    Перейдите по ссылке [metrika.yandex.ru](https://metrika.yandex.ru/) и создайте новый счётчик.

2. **Подключите счетчик к Swagger UI**

    Добавьте код счётчика в `docs/dist/index.html` перед закрывающим тегом `</head>` или `</body>`:

   ```html
    <!-- Yandex.Metrika counter -->
    <script type="text/javascript" >
      (function(m,e,t,r,i,k,a){m[i]=m[i]||function(){(m[i].a=m[i].a||[]).push(arguments)};
      m[i].l=1*new Date();
      for (var j = 0; j < document.scripts.length; j++) {if (document.scripts[j].src === r) { return; }}
      k=e.createElement(t),a=e.getElementsByTagName(t)[0],k.async=1,k.src=r,a.parentNode.insertBefore(k,a)})
      (window, document, "script", "https://mc.yandex.ru/metrika/tag.js", "ym");

      ym(XXXXXX, "init", {
           clickmap:true,
           trackLinks:true,
           accurateTrackBounce:true,
           webvisor:true
      });
    </script>
    <noscript><div><img src="https://mc.yandex.ru/watch/XXXXXX" style="position:absolute; left:-9999px;" alt="" /></div></noscript>
    <!-- /Yandex.Metrika counter -->
   ```

   Замените `XXXXXXX` на ID вашего счётчика.

3. **Подключите счетчик к MkDocs**

   Создайте шаблон `overrides/main.html` и вставьте туда код счетчика:

    ```html
    {% extends "base.html" %}
    {% block extrahead %}
    {{ super() }}
    <!-- Yandex.Metrika counter -->
    <script type="text/javascript" >
      (function(m,e,t,r,i,k,a){m[i]=m[i]||function(){(m[i].a=m[i].a||[]).push(arguments)};
      m[i].l=1*new Date();
      for (var j = 0; j < document.scripts.length; j++) {if (document.scripts[j].src === r) { return; }}
      k=e.createElement(t),a=e.getElementsByTagName(t)[0],k.async=1,k.src=r,a.parentNode.insertBefore(k,a)})
      (window, document, "script", "https://mc.yandex.ru/metrika/tag.js", "ym");

      ym(XXXXXX, "init", {
           clickmap:true,
           trackLinks:true,
           accurateTrackBounce:true,
           webvisor:true
      });
    </script>
    <noscript><div><img src="https://mc.yandex.ru/watch/XXXXXX" style="position:absolute; left:-9999px;" alt="" /></div></noscript>
    <!-- /Yandex.Metrika counter -->
    {% endblock %}
    ```

   Замените `XXXXXXX` на ID вашего счётчика.

4. **Добавьте в `mkdocs.yml` путь к пользовательскому шаблону**:

   ```yaml
   theme:
     custom_dir: 'overrides'
   ```

5. **Проверьте работу счётчика**  

    Откройте сайт и убедитесь, что данные о посещениях отображаются в интерфейсе Яндекс Метрики.
