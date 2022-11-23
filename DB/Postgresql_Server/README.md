### 목표
- 도커를 이용해 postgres 서버를 띄웁니다.
- `psql` 을 이용해 생성된 username과 그 역할을 확인합니다.

### 요구사항
1. Postgresql User Requirements
    - Username: `postgres`
    - Role: `Superuser`
    - Password: `mypassword`
2. Docker Run Option
    - port forwarding: 5432:5432
3. psql cli tool 을 통해 생성한 데이터 베이스에 접속합니다.
    - 다음 option을 사용해 접속합니다.
        `-h, --host=HOSTNAME database server host or socket directory (default: "local socket")`
        `-U, --username=USERNAME database user name (default: "...")`
4. psql 내부에서 다음 내용을 확인합니다.
    - 생성한 Role name 과 role

### 과정
- docker run
    ```docker run --name postgres -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=mypassword -d -p 5432:5432 postgres```
    - POSTGRES_USER=postgres superuser이다.
- psql 접속
    ```psql -h localhost -U postgres -p 5432```
    Password for user postgres: 
    postgres=#
- Role name과 role 확인
    ```SELECT rolname, rolsuper FROM pg_roles;```
