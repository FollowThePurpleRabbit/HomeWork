*So. what do i know about git...*

---
---

1. Git и GitHub - не от одного и того же создателя. Гит - с открытым кодом, а гитхаб вроде бы создает майкрософт. Есть и другие штуки, как гитхаб, но он просто самый популярный.

---

2. Проверить, установлен ли гит - ```git version```

---

3. Настройки хранятся в файле .gitconfig

Чтобы задать имя пользователя и мыло: 

```$ git config --global user.name "User Namovich"```

(имя или ник нужно написать латиницей и в кавычках)

```$ git config --global user.email username@yandex.ru```

(здесь нужно указать свой настоящий email) 

---

4. Чтобы сделать папку гит репозиторием - перейти в нужную папку и вызвать ```git init```.

Это создаст папку .git, в которой гит будет хранить то, что ему нужно для работы

Гит можно так же спокойно удалить - надо просто удалить папку .git и все файлы внутри нее

---

5. Главная ветка по умолчанию называется master или main

---

6. Проверить статус - ```git status``` или ```git status oneline``` - будет кратко

---

7. Подготовить файлы к сохранению - ```git add```

Можно использовать как git add cat.txt

Или как добавить все: git add -all или git add .  (Точка в баше означает текущую папку)

---

8. Закоммитить файлы, то есть сохранить ранее добавленые на сохранение - ```git commit -m "Message"```

Message должен быть осознанным, то есть кратко объяснять, что было изменено в новой версии

---

9. Посмотреть историю коммитов - ```git log```


---

10. Чтобы безопасно связать гит и гитхаб используем SSH, для этого надо сгенерировать ключи (паблик и прайвет)

Ключи в винде по умолчанию хранятся в корневой директории пользователя в папке .ssh

Сгенерировать ключи - ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 

Потом там будут настройки, типа имени файла и пароля, можно установить, а если не хочется, то оно пропускается нажатием на Enter

После того, как сгенерировали ключи, копируем публичный и впихиваем его на гитхаб (настройки -> SSH -> добавить ключ)

Потом проверяем подлинность ключа командой ssh -T git@github.com 

И связываем акки - копируем в гитхабе ссылку на созданный репозиторий, к которому хотим привяхать локальный, и вводим

```git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git``` (тут типа ссылка)

Убедиться, что репозитории связаны, — ```git remote -v```

---

11. В репозитории может существовать сразу несколько веток — параллельных историй изменений. Также они могут соединяться друг с другом.

---

12. Отправить изменения на удалённый репозиторий — ```git push```

Но в первый раз ее нужно юзать: ```git push -u origin main``` (вместо main может бьть master)

---

13. README.md - кратко описывает всякие штуки

Маркда́ун — это специальный язык разметки. Он позволяет красиво отформатировать текстовый документ.

- заголовки - кол-во звезд от 1 до 6 (первый заголовок самый большой), напр ***Заголовок 3-го уровня

- добавление черточки - 3 раза "-", напр: сверху --- снизу

- разрыв строки - 2 пробела или br в <>

- новый параграф - Enter дважды 

- выделить курсивом - * с каждой стороны, жирным - 2 звезды с каждой, зачернуть - две ~ с каждой стороны

- нумерованый список - просто цифры и точка, ненумерованный - звездочка или дефис с пробелом

- код окружаем тройкой косых кавычек (`)

---

14. Хэш - типа номера коммита, его можно юзать для получения инфы про коммит.

HEAD - файл в .git, где хранится ссылка на хэш **последнего** коммита, можно использовать HEAD вместо его хэша

---

15. Сообщения к коммитам должны быть информативными 

Есть разные системы оформления, напр FEAT или FIX вначале

---

16. Состояния файлов - untracked, tracked, modifed, staged

Если ни разу не делали add - то типа не отслеживается, во всех остальных отслеживается

Если был изменен, но не add, то будет modifed, а если был add, но без коммита, то staged

```mermaid
graph LR;
  untracked -- "git add" --> staged;
  staged    -- "???"     --> tracked/comitted;

%% стрелка без текста для примера: 
  A --> B;
``` 

---

17. ```git commit --amend --no-edit``` - сделает коммит, но не новый, а дополнит последний

**Работает только с последним коммитом!!!**

Но хэш коммита изменится, так как изменились файлы в коммите

no-edit гооврит, что сообщение должно остаться прежним 

Чтобы изменить сообщение - ```git commit --amend -m "New message"```

---

18. Из vim надо убегать... Алгоритм такой:

Вот как выйти из Vim:

    * Нажмите клавишу Esc.
    * Наберите последовательность символов :qa!.
    * Нажмите Enter.

---

19. Выполнить unstage изменений — ```git restore --staged <file>```

