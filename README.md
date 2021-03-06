jquery.lifeForm
============================

Плагин для работы с формами
-----------

  * Показывает/скрывает блоки при клике на 
    радиобатоны и чекбоксы

  * Умеет фокусировать в инпут(текстарею) при клике на радиобатон(чекбокс)

  * Умеет кликать радиобатон(чекбокс) при фокусе в инпут(текстарею)

  * При этом имеет интуитивно понятный интерфейс (в духе JSON)

  * Всего 3 метода: show/hide/focus.

  * Всего 3 поля: if/than/else


Установка
---------
```html
        <style>
          /* класс который присваивается блоку 
             когда тот скрывается */
          .lifeFormHide {
              display: none;
          }
        </style>
        <script type="text/javascript" src="js/jquery-2.0.3.min.js"></script>
        <script type="text/javascript" src="releases/jquery.lifeForm-1.0.js"></script>
        <script type="text/javascript">
        $(document).ready(function () {

            $('#form').lifeForm(
                  // JSON-данные
                );
            });
        </script>
```

Примеры
---------
```html
        <style>
          .lifeFormHide {    display: none;   }
        </style>
        <script type="text/javascript" src="js/jquery-2.0.3.min.js"></script>
        <script type="text/javascript" src="releases/jquery.lifeForm-1.0.js"></script>
        <script type="text/javascript">
        $(document).ready(function () {

            $('#form').lifeForm({
                "show": [
                    {   // если кликнут #ex1_books
                        // то показываем (show) блок #ex1_books_box
                        // иначе показываем блок #ex1_games_box
                        // а #ex1_books_box, очевидно, скрываем
                        "if":   "#ex1_books",
                        "than": "#ex1_books_box",
                        "else": "#ex1_games_box"
                    }
                  ],
                "hide": [
                    {   // если кликнут #ex2_checkbox
                        // то скрываем (hide) блок #ex2_box
                        "if":   "#ex2_checkbox",
                        "than": "#ex2_box"
                    }
                  ],
                "focus": [
                    {   // если кликнут #ex3_radio
                        // то указатель сфокусируется в #ex3_textarea
                        "if":   "#ex3_radio",
                        "than": "#ex3_textarea"
                    }
                  ]
                });
            });
        </script>
```

Можно посмотреть [работу примера на jsfiddle][1] и [поиграться с примером на jsfiddle][2]

Документация
------------

 Существует 3 метода:

  * show - при выполнении события, подчиненные блоки становятся видимыми
  * hide - при выполнении события, подчиненные блоки становятся скрытыми
  * focus - при выполнении события, подчиненный input/textarea становится в фокусе (в него ставится курсор).

Для этих методов есть поля:

  * if - селектор, при нажатии которого выполняется событие (обязательное поле)
  * than - селектор, над которым совершается событие (обязательное поле)
  * else - только для методов show/hide необязательное поле. Там указывается селектор, над которым совершается событие, если условие в if ложно. То есть, чекбокс/радио НЕ checked.

В методах show и hide допустима связь многие-ко-многим. То есть возможен выбор нескольких селекторов (jQuery-синтаксис). Например "if": "#books1, #books2". Несколько селекторов обрабатываются по условию ИЛИ. То есть: если кликнут радиобатон #books1 ИЛИ кликнут #books2 ТО выполняется условие than. При этом в than можно также указать несколько блоков - над всеми ими будет выполнено действие (скрытие/показ)

Внимание! Для метода focus допустима связь один-к-одному. Связь многие-ко-многим не поддерживается, при попытке её использовать вылетит ошибка.

Примечание. Когда блок становится скрытым, к нему просто добавляется класс .lifeFormHide. Значит, в css-стилях нужно прописать
```css
.lifeFormHide { display: none; }.
 ```
 См. установку плагина.

[1]: https://jsfiddle.net/fattan/8vb9pLkd/6/embedded/result/
[2]: https://jsfiddle.net/fattan/8vb9pLkd/6/