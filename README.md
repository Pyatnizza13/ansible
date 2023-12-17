Есть сервер с ОС Linux, с системой управления пакетами RPM.
На нём установлена Oracle JDK 1.8 из RPM-пакета.
Необходимо:
1) С помощью Ansible обновить (т.е. удалить старую версию и установить новую) JDK до openjdk-17, взятую с https://openjdk.java.net/projects/jdk/17/ (с прописыванием системных путей к бинарникам в PATH).
2) Установить nginx текущей стабильной версии.
3) Создать файл index.html, в котором содержится IP-адрес сервера, на котором он находится. Для выяснения IP-адреса желательно использовать штатные средства Ansible.
4) Раздать данный файл через nginx.
 
Артефакты необходимо оформить в виде Git-репозитория и выложить его на любой публичный Git-хостинг, либо прислать его в архиве.
 
После ознакомления с результатами тестового задания предлагаю созвониться по Zoom/Telegram/Skype и с расшаренным экраном обсудить результат (что сделано, как именно и почему).

1. Удален 1.8.0 и установлен из роли java 17.0.2. Указан путь до папки через alternatives.
2. Создана ролль nginx. в tasks: Добавлен репозиторий nginx. Прописан полный путь так как РедОС подставляла не ту версию в путь. Установлена стабильная версия 1.24.0. Скопирован файл nginx.conf
3. создан файл в папке /etc/ansible/roles/nginx/templates/index.html.j2 с добавлением параметра ansible_facts
4. Скопирован файл index.html в /usr/share/nginx/
