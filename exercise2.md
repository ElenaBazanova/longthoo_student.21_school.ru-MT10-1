# Веб-хранилища №1
## 1. Что такое Local Storage и Session Storage? В чём заключается их различие?
Local Storage — это механизм хранения данных веб-браузера, который позволяет веб-приложениям сохранять данные локально на компьютере пользователя. Он предоставляет простой способ хранения и доступа к данным без необходимости отправки запросов на сервер.

Local Storage основан на паре ключ-значение и может хранить данные в формате строк. Он обладает некоторыми преимуществами, такими как:

1. Постоянство: данные, сохраненные в Local Storage, остаются доступными даже после перезапуска браузера или компьютера. Они не удаляются автоматически и могут быть использованы в последующих сеансах работы с приложением.

2. Объем хранения: Local Storage обычно предоставляет более значительный объем хранения по сравнению с другими механизмами хранения веб-браузера, такими как Cookies.

3. Простота использования: для записи и чтения данных из Local Storage используется JavaScript API, который довольно прост в освоении и использовании.

**Local Storage** может быть полезен для различных задач, таких как сохранение настроек пользователей, кэширование данных, хранение состояния приложений и т. д. Однако, следует помнить, что Local Storage является локальным для каждого браузера и не может быть использован для обмена данными между разными устройствами или пользователями.

**Session Storage** - это механизм хранения данных веб-браузера, который позволяет веб-приложениям сохранять данные на протяжении сеанса работы с браузером. Он подобен Local Storage, но имеет некоторые отличия.

Основные особенности Session Storage:

1. Жизненный цикл: данные, сохраненные в Session Storage, доступны только в рамках текущего сеанса работы с браузером. Когда пользователь закрывает вкладку или браузер, данные удаляются автоматически.

2. Объем хранения: объем хранения в Session Storage обычно такой же, как и в Local Storage. Однако, в отличие от Local Storage, Session Storage может быть ограничен размером кэша браузера.

3. Доступность: данные, сохраненные в Session Storage, доступны только в пределах одного окна или вкладки браузера. Они не могут быть общими между разными окнами или вкладками.

**Session Storage** может быть полезен для хранения временных данных, состояний сеанса, информации о текущем пользователе и других данных, которые нужны только в рамках текущего сеанса работы с браузером. Он обладает простым API, доступным через JavaScript, для записи и чтения данных.

Важно отметить, что как **Local Storage**, так и **Session Storage** являются локальными для каждого отдельного браузера и не могут быть использованы для обмена данными между разными устройствами или пользователями.

Отличие **Session Storage** от **Local Storage** в сроке жизни: данные в **Session Storage** удаляются после закрытия вкладки браузера, а в **Local Storage** они не удаляются "никогда";


## 2. Какие существуют основные методы взаимодействия с localStorage и sessionStorage через консоль в браузере? Как производить сохранение, получение, удаление данных, очистку хранилища?

Объекты хранилища sessionStorage и localStorage предоставляют одинаковые методы и свойства:

- setItem(key, value) – сохранить пару ключ/значение;
- getItem(key) – получить данные по ключу key;
- removeItem(key) – удалить данные с ключом key;
- clear() – удалить все;
- key(index) – получить ключ на заданной позиции;
- length – количество элементов в хранилище.  

1. **Функция setItem(key, value)** принимает ключ в качестве первого аргумента и значение в качестве второго аргумента. Как упоминалось ранее, все данные должны быть строками.   
Примеры установки:
```
sessionStorage.setItem("google", "Analytics"); // ключ "google", а значение "Analytics"
localStorage.setItem ("google", "Tag Manager"); // ключ "google", а значение "Tag Manager"

```
2. **Функция getItem(key)** берет ключ, который использовался при сохранении данных в качестве аргумента. Чтобы извлечь значение из ключей, которые мы сохранили, необходимо написать следующее:

```
sessionStorage.getItem("google"); // задается ключ "google",  а отобразится значение "Analytics"
localStorage.getItem ("google"); // задается ключ "google", а отобразится значение "Tag Manager"
```
3. Удаление данных из хранилища имеет всего один синтаксис **removeItem(key)**

```
localStorage.removeItem("key");
sessionStorage.revomeItem("key");
```
4. Удаление всех данных из хранилища  

В любой момент вы можете удалить все записи командой .clear():  

```
localStorage.clear();
sessionStorage.clear();
```
5. Количество записей в хранилище  

Для того, чтобы получить общее количество записей в хранилище, необходимо использовать стандартное свойство length:   

```
localStorage.length
sessionStorage.length
```
## 3. Что такое IndexedDB? Чем этот вид хранилища отличается от описанных выше?
IndexedDB — JavaScript-интерфейс прикладного программирования клиентского хранилища большого объема структурированных данных, в том числе файлы/blobs. Другими словами, это NoSQL-хранилище данных в формате JSON внутри браузера.

IndexedDB отличается от localStorage и sessionStorage в нескольких аспектах:

1. Тип данных: localStorage и sessionStorage предназначены для хранения простых значений (обычно строк или чисел) в формате ключ-значение. IndexedDB, с другой стороны, позволяет хранить структурированные данные, такие как объекты и коллекции данных.

2. Мощность и гибкость: IndexedDB предоставляет более мощный и гибкий механизм хранения и манипулирования данными. Он поддерживает индексирование данных, транзакции для гарантированной целостности данных, а также многопоточность для эффективной обработки больших объемов данных. localStorage и sessionStorage не предлагают таких возможностей.

3. Объем хранилища: localStorage и sessionStorage имеют ограничения на объем данных, который можно хранить. Обычно это составляет около 5 МБ. IndexedDB имеет более высокий предел, который зависит от браузера и настроек пользователя.

4. Синхронность и асинхронность: Операции с localStorage и sessionStorage выполняются синхронно, что означает, что выполнение кода останавливается до завершения операции. В IndexedDB операции обычно выполняются асинхронно, что позволяет приложению продолжать работу во время выполнения операций.

5. Поддержка оффлайн режима: IndexedDB может использоваться для создания веб-приложений, которые могут работать оффлайн и синхронизироваться с сервером по восстановлении соединения. localStorage и sessionStorage не предоставляют такой возможности

В целом, IndexedDB предоставляет более мощные возможности для работы с данными в веб-приложениях, особенно если вам нужно хранить и манипулировать большими объемами структурированных данных. Однако, из-за его сложности, использование localStorage и sessionStorage может быть предпочтительным для простых случаев хранения небольших объемов данных.

## 4. Как можно просмотреть содержимое всех веб-хранилищ в браузере?
В Google Chrome для этого необходимо открыть «DevTools" (F12), перейти на вкладку «Application». Здесь они находятся на левой панели в разделе «Storage». При выборе источника вы увидите какие данные содержатся соответственно в Session Storage, Local Storage, IndexedDB