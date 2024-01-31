# ssh
ssh 접근시 id/pwd 방식이 일반적이지만 보안상의 이유로 key를 사용하여 접근할 수 있도록 한다.

## The Authorized Keys File
### 저장위치
.ssh/authorized_keys 파일에 *.pub의 데이터가 저장되어 있으며 이 파일에 pubkey를 추가하여 authorized keys file인 pem을 추가할 수 있다.

### SSH key pairs
상세한 사용법은 ssh-keygen을 검토한다. 중간에 passphrase를 추가하면 보안상에 이점은 있으나 사용이 불편할 수 있으니 보안레벨에 따라 선택적으로 적용하면 된다.
#### Ed25519
```
ssh-keygen -t ed25519 -C "user@domain.tld"
```
#### RSA
```
ssh-keygen -t rsa -b 4096 -C "user@domain.tld"
```

### Add Manually
인스턴스에 접근하여 아래와 같이 파일을 생성하고 pubkey를 추가하고 저장한다.
```
$ ssh [user]@[ip-address]
$ mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys
$ chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys
$ nano ~/.ssh/authorized_keys
```

### Addd ssh-copy-id
```
$ ssh-copy-id [user]@[ip-address]
```
