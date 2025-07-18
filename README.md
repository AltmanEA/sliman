Набор скриптов для создания курса из нескольких лекций с Slidev

# Установка

- Установите NodeJS [https://nodejs.org/](https://nodejs.org/).
- Установите Visual Studio Code [https://code.visualstudio.com/](https://code.visualstudio.com/).
- Установите Git [https://git-scm.com/](https://git-scm.com/).
- Установите pnpm [https://pnpm.io/](https://pnpm.io/).
- Скопируйте текущий проект (```Code - Download ZIP```) и распакуйте его (в папку с именем курса). Не стоит клонировать проект, поскольку далее в этой папке будет располагаться проект с учебным курсом. Откройте проект в Visual Studio Code.

Далее команды выполняются в терминале (```Терминал - Создать терминал```).

- Установите зависимости: ```pnpm install```.
- Инициализируйте проект: ```pnpm s:init <имя курса>```.

При инициализации будут созданы две папки: 

- ```slides``` - для создания папок отдельных лекций, в которых будут исходные файлы лекции и скрипты ```sli.dev``` для сборки;
- ```<имя курса>``` - для собранной версии курса лекции - готовый сайт для выкладывания на хостинг.

# Работа

Для создания отдельной лекции используется следующая команда:

```pnpm s:add <имя лекции>```

После создания лекции ее нужно отредактировать:

```pnpm s:dev <имя лекции>```

Эта команда откроет исходный файл (```slides.md```)  в Visual Studio Code, запустить отладочный сервер и откроет презентацию к лекции в браузере (это может занять некоторое время). После сохранения изменений в исходном файле презентация в лекции автоматически обновится. При создании презентации используйте документацию (руководство) Slidev [https://sli.dev/guide/syntax](https://sli.dev/guide/syntax). 

После редактирования лекции нужно собрать ее:

```pnpm s:build <имя лекции>```

Эта команда соберет лекцию в папку ```<имя курса>\<имя лекции>```, а также обновит служебный файл (```slides.json```) с информацией о лекциях и элемент ```<div id="slide_list">``` в файле ```index.html```.  Этот элемент будет содержать список лекций, остальную часть файла ```index.html``` можно отредактировать, чтобы создать заглавную страницу курса. Порядок лекций можно изменить в файле ```slides.json```.

Посмотреть сайт курса можно с помощью команды:

```pnpm s:view```.

# Публикация

Для публикации курса можно просто переписать папку ```<имя_курса>``` на любой статичный хостинг. Поскольку slidev не очень удобно работает с относительными ссылками адрес сайта должне иметь формат ```https://<домен>/<имя_курса>/```. 

Проще опубликовать, а затем обновлять курс, при помощью GitHub Pages. Для этого нужно выложить весь проект в репозиторий на ```Gihub```, при этом имя репозитория должно быть ```<имя_курса>```. На самом ```Github``` перейти в репозитории в ```settings```, в разделе ```Pages``` и в поле ```Source``` указать ```Github Actions```. Скрипт для автоматической публикации вашего сайта уже настроен в проекте. Ваш сайт должен появится по адресу ```https://<github_username>.github.io/<имя_курса>/```.

