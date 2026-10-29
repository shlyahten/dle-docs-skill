# ЧПУ и настройка

- **Категория:** Начало работы и шаблоны
- **ID темы:** 13
- **Источник:** [https://dle-news.ru/extras/online/?topic=13](https://dle-news.ru/extras/online/?topic=13)

---

**DataLife Engine** использует в своей работе для вывода новостей ЧПУ (человеко-понятный URL), что позволяет тему статьи или любой другой текст добавить в URL браузера, благодаря этому индексация сайта в поисковых системах будет более качественной, что приведет больше посетителей на ваш сайт с поисковых систем. Для работы ЧПУ необходимо чтобы на вашем сервере был установлен модуль mod_rewrite если используется Apache как основной сервер для PHP. Если Ваш сервер не поддерживает этого, то вы можете отключить эту функцию настройках скрипта.

**Для Apache:**

В случае если вы используете Apache как сервер для PHP, то в корне вашего сайта должен присутствовать файл .htaccess со следующим содержанием (он идет вместе с дистрибутивом DLE):

DirectoryIndex index.php

```text
DirectoryIndex index.php

<IfModule mod_rewrite.c>
	RewriteEngine On

	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteRule \.(php|jpg|jpeg|gif|ico|png|svg|webp|avif|js|css|mp3|ogg|mp4|mkv|avi|zip|rar|woff|woff2)(\?|$) - [L,NC,R=404]

	RewriteRule ^sitemap.xml$ uploads/sitemap.xml [L]
	RewriteRule ^google_news.xml$ uploads/google_news.xml [L]
	RewriteRule ^static_pages.xml$ uploads/static_pages.xml [L]
	RewriteRule ^category_pages.xml$ uploads/category_pages.xml [L]
	RewriteRule ^tags_pages.xml$ uploads/tags_pages.xml [L]
	RewriteRule ^news_pages(\d*?).xml$ uploads/news_pages$1.xml [L]

	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d
	RewriteRule . index.php [L]
</IfModule>
```

**Для Nginx:**

В случае если вы используете Nginx как сервер для PHP, то в конфигурации вашего домена в секции location должны присутствовать следующие строчки:

```text
location / {

   location ~ ^/backup/ {
       deny all;
       return 403;
   }

   location ~ ^/engine/ {
       deny all;
       return 403;
   }

   location ~ ^/public/.*\.ph(p\d*|tml)$ {
       deny all;
       return 403;
   }

   location ~ ^/language/ {
       deny all;
       return 403;
   }

   location ~ ^/templates/.*\.(ph(p\d*|tml)|tpl)$ {
      deny all;
      return 403;
   }

   location ~ ^/uploads/.*\.ph(p\d*|tml)$ {
       deny all;
       return 403;
   }

   location ~ ^/uploads/files/.*\.(avi|divx|mp3|ogg|flac|aac|mp4|wmv|m4v|m4a|mov|mkv|webm|m3u8)$ {
       allow all;
   }

   location ~ ^/uploads/files/ {
       deny all;
       return 403;
   }

   rewrite "^/sitemap.xml$" /uploads/sitemap.xml last;
   rewrite "^/google_news.xml$" /uploads/google_news.xml last;
   rewrite "^/static_pages.xml$" /uploads/static_pages.xml last;
   rewrite "^/category_pages.xml$" /uploads/category_pages.xml last;
   rewrite "^/tags_pages.xml$" /uploads/tags_pages.xml last;
   rewrite "^/news_pages(\d*?).xml$" /uploads/news_pages$1.xml last;

# ваш остальной код конфигурации домена

   try_files $uri $uri/ /index.php?$args;
}
```

Где вместо точек ваши дополнительные параметры для работы вашего домена, обработчики PHP и прочие настройки. Для настройки nginx мы рекондуем обратиться к вашему системному администратору или в службу поддержки вашего хостинга.

**Пользовательское изменение вида ссылок и правил:**

Вы можете менять и настраивать вид ссылок ЧПУ в соответствующем разделе в панели управления. Однако мы не рекомендуем менять вид ссылок для неопытных пользователей. Для них мы рекомендуем выбрать один из трех предустановленных видов в настройках скрипта.

В случае если вы решили самостоятельно менять вид ссылок, или добавлять свои, то вам необходимо придерживаться нескольких правил. По умолчанию в паттерне поиска используется синтаксис, в котором например `{foo}` указывает на поиск совпадения которому назначить имя foo, а сам поиск соответствует регулярному выражению `[^/]+`. То есть искать любой набор символов до первого слеша Чтобы настроить шаблон, которому соответствует искомое выражение, вы можете указать пользовательский шаблон, написав например `{bar:[0-9]+}`. Несколько примеров:

`/user/{id:\d+}/` под это условие попадает /user/42, но не попадает /user/xyz

`/user/{name}/` под это условие попадает /user/foobar/, но не попадает /user/foo/bar

`/user/{name:.+}/` под это условие попадает /user/foo/bar целиком как есть.

Значения из шаблона поиска назначаются указанным именам. В данных примерах найденные значения вы можете передать в реальную ссылку под тегами `{id}` и `{name}`. Соответственно скрипту будут переданы значения `$_GET['id']` и `$_GET['name']`.

Пользовательские параметры для шаблона поиска в ссылке ЧПУ не могут использовать группы для захвата, потому как сами уже являются группами. Например `{lang:(en|de)}` не может быть использовано, поскольку () это группа для поиска. Вместо этого вам нужно использовать шаблон поиска `{lang:en|de}` или `{lang:(?:en|de)}`.

Внимание в реальную ссылку ЧПУ если вы меняете стандартные правила DLE необходимо передавать только те переменные, с которыми работает и понимает DLE. например для показа полной новости DLE понимает ссылку /index.php?newsid=123 где переменной newsid передается числовое значение, то как бы вы не поменяли шаблон для ссылки ЧПУ вы должны в любом случае для реальной ссылки передать переменную newsid с числовым значением.
