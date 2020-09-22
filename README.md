# docker-django

## 手順

1: イメージをビルドする
```
docker-compose build
```

2: プロジェクトを作成する
```
docker-compose run web django-admin startproject config .
```

3: データベースの設定を行う
``` 
  DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'ユーザー名',
        'PASSWORD': 'パスワード',
        'HOST': 'db',
        'PORT': 5432,
    }
  }
  ```
  
  4: ホストの接続状態を更新する
  ```
  ALLOWED_HOSTS = ['localhost','0.0.0.0']
  ```
  5: マイグレーションする
  ```
  docker-compose run web python manage.py makemigrations
  docker-compose run web python manage.py migrate
  ```
  6: 起動する
  ```
  docker-compose up
  ```
