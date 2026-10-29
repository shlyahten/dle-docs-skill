# RSS Экспорт

- **Категория:** RSS Экспорт
- **ID темы:** 76
- **Источник:** [https://dle-news.ru/extras/online/?topic=76](https://dle-news.ru/extras/online/?topic=76)

---

Движок DataLife Engine поддерживает также экспорт новостей в формате RSS для того чтобы посетители получили экспорт новостей с главной страницы вы должны использовать следующий путь.

С использованием ЧПУ:

`http://website.com/rss.xml`  - трансляция основного потока RSS

`http://website.com/rssdzen.xml`  - трансляция потока RSS для сервиса Дзен

Без использования ЧПУ:

`http://website.com/index.php?mod=rss` - трансляция основного потока RSS

`http://website.com/index.php?mod=rss&rssmode=dzen` - трансляция потока RSS для сервиса Дзен

**Для экспорта новостей из определенной категории используйте следующие ссылки**

С использованием ЧПУ:

`http://website.com/альтернативное имя категории/rss.xml` - трансляция основного потока RSS

`http://website.com/альтернативное имя категории/rssdzen.xml` - трансляция потока RSS для сервиса Дзен

Без использования ЧПУ:

`http://website.com/index.php?mod=rss&do=cat&category=альтернативное имя` - трансляция основного потока RSS

`http://website.com/index.php?mod=rss&do=cat&rssmode=dzen&category=альтернативное имя` - трансляция потока RSS для сервиса Дзен

**Для экспорта всех новостей определенного пользователя используйте следующие ссылки**

С использованием ЧПУ:

`http://website.com/user/имя пользователя/rss.xml` - трансляция основного потока RSS

`http://website.com/user/имя пользователя/rssdzen.xml` - трансляция потока RSS для сервиса Дзен

Без использования ЧПУ:

`http://website.com/index.php?mod=rss&subaction=allnews&user=имя пользователя` - трансляция основного потока RSS

`http://website.com/index.php?mod=rss&subaction=allnews&rssmode=dzen&user=имя пользователя` - трансляция потока RSS для сервиса Дзен

**Для экспорта новостей из определенного каталога используйте следующие ссылки**

С использованием ЧПУ:

`http://website.com/catalog/идентификатор/rss.xml` - трансляция основного потока RSS

`http://website.com/catalog/идентификатор/rssdzen.xml` - трансляция потока RSS для сервиса Дзен

Без использования ЧПУ:

`http://website.com/index.php?mod=rss&catalog=идентификатор`  - трансляция основного потока RSS

`http://website.com/index.php?mod=rss&rssmode=dzen&catalog=идентификатор`  - трансляция потока RSS для сервиса Дзен
