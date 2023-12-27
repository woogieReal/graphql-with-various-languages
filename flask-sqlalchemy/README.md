# Flask + Graphene-Python + SQLite + SQLAlchemy
- [코드베이스: graphql-python](https://github.com/graphql-python/graphene-sqlalchemy/tree/master/examples/flask_sqlalchemy)
- 위 코드를 도커 환경에서 실행되도록 하였음
- `graphql-http-request.postman_collection.json` 파일에 호출 예시를 만들어 두었음

<br>

# 실행
```
➜ docker-compose up -d
```

<br>

# 사용
- `http://localhost:5005/graphql` 접속하여 쿼리 작성 및 실행
- 포스트맨에서 GraphQL request 를 만들어 사용
- 포스트맨에서 예시로 준비된 http request 컬렉션을 import하여 사용

<br>

# 이외
## 데이터베이스 스키마
- `database.sqlite3` 파일을 열어서 확인 가능
- vscode를 이용시 *SQLite3 Editor* 혹은 *SQLite Viewer* 사용

```sql
CREATE TABLE roles (
	role_id INTEGER NOT NULL, 
	name VARCHAR, 
	PRIMARY KEY (role_id)
)

CREATE TABLE department (
	id INTEGER NOT NULL, 
	name VARCHAR, 
	PRIMARY KEY (id)
)

CREATE TABLE employee (
	id INTEGER NOT NULL, 
	name VARCHAR, 
	hired_on DATETIME, 
	department_id INTEGER, 
	role_id INTEGER, 
	PRIMARY KEY (id), 
	FOREIGN KEY(department_id) REFERENCES department (id), 
	FOREIGN KEY(role_id) REFERENCES roles (role_id)
)
```