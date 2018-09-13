# mysite
Python Django 


### 根据Django内模型生成对应的数据库表结构
```
➜  mysite git:(master) ✗ python3 manage.py makemigrations
Migrations for 'blog':
  blog/migrations/0001_initial.py
    - Create model BlogArticles
```

### 查看生成表的源码SQL语句
```
➜  mysite git:(master) ✗ python3 manage.py sqlmigrate blog 0001
BEGIN;
--
-- Create model BlogArticles
--
CREATE TABLE "blog_blogarticles" ("id" integer NOT NULL PRIMARY KEY AUTOINCREMENT, "title" varchar(300) NOT NULL, "body" text NOT NULL, "publish" datetime NOT NULL, "author_id" integer NOT NULL REFERENCES "auth_user" ("id") DEFERRABLE INITIALLY DEFERRED);
CREATE INDEX "blog_blogarticles_author_id_ed798e23" ON "blog_blogarticles" ("author_id");
COMMIT;
```


### 真正创建数据库
```
➜  mysite git:(master) ✗ python3 manage.py migrate             
Operations to perform:
  Apply all migrations: admin, auth, blog, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying blog.0001_initial... OK
  Applying sessions.0001_initial... OK
  ```


  ### 创建超级管理员
  ```
  ➜  mysite git:(master) ✗ python3 manage.py createsuperuser
Username (leave blank to use 'dp'): admin
Email address: 542413041@qq.com
Password: 
Password (again): 
The password is too similar to the email address.
Bypass password validation and create user anyway? [y/N]: y
Superuser created successfully.
  ```