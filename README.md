# django-dockerの起動方法

まずはdockerをbuild

```bash
    docker-compose build
```
初回起動時に実行
```bash
	docker-compose run --rm app django-admin startproject config .
```

dockerを常に起動するコマンド
```bash
	docker-compose -d
```
DBをmysqlで接続できるように設定を修正
```bash
	DATABASES = {
		'default': {
			'ENGINE': 'django.db.backends.mysql',
			'NAME': 'django-db',
			'USER': 'django',
			'PASSWORD': 'django000',
			'HOST': 'db',
			'PORT': 3306,
		}
	}		
```

コンテナに入りDBのマイグレーションの変更を行う
```bash
	docker exec -it app bash
```
```bash
	python manage.py migrate
```

管理画面にアクセスするための新規ユーザの作成
```bash
	python manage.py createsuperuser
```

vscodeでデバックする方法
https://daeudaeu.com/vscode-django/


