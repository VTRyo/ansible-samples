# HOW TO ansible-vault

* syntax

```
Usage：ansible-vault [create|decrypt|edit|encrypt|encrypt_string|rekey|view] [options] [vaultfile.yml]
```

* 

```
ansible-playbook -i hosts site.yml --ask-vault-pass
```

## Detail Usage

* 新規ファイルの暗号化

```
ansible-vault create hoge
New Vault password:
Confirm New Vault password:
```

* 既存ファイルの暗号化

```
ansible-vault encrypt group_vars/all
New Vault password:
Confirm New Vault password:
Encryption successful
```

* 暗号化したファイルを閲覧する

```
ansible-vault view group_vars/all
Vault password:
```

* 暗号化したままファイルを編集する

```
ansible-vault edit group_vars/all
Vault password:
```

* 設定したパスワードを変更する

```
ansible-vault rekey group_vars/all
Vault password:
New Vault password:
```

* 暗号化したファイルを復号化する

```
ansible-vault decrypt group_vars/all
Vault password:
```
