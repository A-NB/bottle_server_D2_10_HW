## <center> Простейший веб-сервер на Python с использованием библиотеки *bottle* и интеграцией с *sentry* для "отлова" и логирования возможных ошибок приложения

Приложение использует дополнительные библиотеки, которые устанавливаются в общем случае командой `pip install имя_библиотеки`. Необходимые для работы приложения библиотеки перечислены в файле *<b>requirements.txt</b>* этого проекта, поэтому самый простой способ их установить (или обновить до актуальной версии, если они уже установлены в системе) - выполнить команду `pip install -r requirements.txt` из директории, где этот файл расположен.

Для правильной работы приложения необходимо зарегистрироваться на платформах [sentry.io](https://sentry.io) и [heroku.com](https://heroku.com). Для размещения сервера на [heroku.com](https://heroku.com) полезно ознакомиться с [этой](https://github.com/chucknado/bottle_heroku_tutorial) инструкцией, [этой](https://devcenter.heroku.com/articles/git#http-git-authentication) (обе на английском) и по этому адресу: `https://github.com/ancatmara/learnpython2018/blob/master/Lessons/Heroku и командная строка/13a. Heroku.md`(на русском). Сервер также можно развернуть локально (без регистрации на [heroku.com](https://heroku.com)), тогда он будет доступен в браузере по адресу: http://localhost:8080

Приложение использует Ваши учётные данные, полученные при регистрации на sentry.io. Для того, чтобы сохранить конфиденциальность Ваших данных, используется следующий метод (немного об этом [здесь](https://devcenter.heroku.com/articles/sentry#integrating-with-python-or-django)). Необходимо создать системную переменную *SENTRY_DSN*, которая будет содержать путь доступа к Вашему проекту на sentry.io, включающий Ваш ключ авторизации и id проекта:
#### <center><span style="color:blue">https://<span style="color:red"><b>Ваш_ключ</b></span>@sentry.io/<span style="color:red"><b>id_проекта</b></span></span></center>
  
Это можно сделать, запустив следующий код:
  
```
import os
os.environ['SENTRY_DSN'] = 'https://Ваш_ключ@sentry.io/id_проекта'
```

Не забудьте заменить **Ваш_ключ** и **id_проекта** на реальные значения!
  
После этого желательно перезагрузить компьютер.

Чтобы добавить такую же переменную среды в приложение на [heroku.com](https://heroku.com), нужно зайти на страницу `https://dashboard.heroku.com/apps/имя_Вашего_приложения/settings` и кликнуть по кнопке <span style="color:white;background:#79589f;">&nbsp;Reveal Config Vars </span>, после чего в левом текстовом поле ввести имя переменной, а в правом - её значение.

Это приложение можно протестировать по адресу: https://floating-atoll-33455.herokuapp.com/ (главная страница). Кроме того, доступны ещё страницы:
https://floating-atoll-33455.herokuapp.com/success (текст "This is a success! Status 200") и https://floating-atoll-33455.herokuapp.com/fail (при переходе по этому адресу сервер генерирует исключение RuntimeError и возвращает код ошибки 500).
