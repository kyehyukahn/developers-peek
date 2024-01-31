
# MariaDB
MariaDB 관련 설정에 필요한 정보를 추가한다.

## User Management
### root 계정 
```
MariaDB [(none)]> use mysql
MariaDB [(none)]> set password=password('stgRootNftruth*1026');
```
### 원격접속
접근권한 확인
```
select Host,User,plugin,authentication_string FROM mysql.user;
```

모든 IP 허용
```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'stgRootNftruth*1026';
```
IP 대역 허용
```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.0.%' IDENTIFIED BY '패스워드';
```


### Users
user 계정 생성
create user '계정'@'접속위치' identified by '패스워드';
```

create user 'stg-nftruth'@'%' identified by 'stgUserNftruth*1027';
```
user 권한 주기
grant all privileges on DB이름.테이블 to '계정'@'접속위치';
```
grant all privileges on *.* to 'stg-nftruth'@'%';
```

권한 적용
```
flush privileges;
```
권한 확인
```
show grants for '계정'@'접속위치';
```

계정, 권한 삭제
```
drop user '계정아이디'@'접속위치';

reboke all on DB이름.테이블 from '계정아이디'@'접속위치';
```


