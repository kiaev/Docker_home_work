для выполнения задания №2 распишу то что сделал по шагам:
1. создал Dockerfile
2. docker build -t backend .    #Собрал образ
3. docker run --rm --detach -e POSTGRES_USER=django -e POSTGRES_PASSWORD=django -e POSTGRES_DB=django -p 5432:5432 --name postgresDB -h database -v /var/test-volume:/var/lib/postgresql/data postgres 		# собрал и запустил бд
4. docker run --rm -P -it --name backendApp --link postgresDB:db backend 	# запустил контейнер с бекэндом
5. docker exec -ti backendApp /bin/bash		# зашел внутрь контейнера можно
6. python manage.py runserver 0.0.0.0:8000	# запустил django - это можно было сделать иначе прописал в Dockerfile, но тогда я бы мне пришлось несколько раз пересоздавать контейнеры, чтобы разные команды выполнить
7. http://192.168.31.63:49153/admin/login/?next=/admin/ 	# проверил стартовую страницу что всех работает см Снимок 1
8. python manage.py migrate		# выполнил миграцию приложения в базу чтобы проверить что связка работает
9. docker exec -it postgresDB psql -U django	# зашел в контейнер с бд и выполнил \с django, \dt см Снимок 2

