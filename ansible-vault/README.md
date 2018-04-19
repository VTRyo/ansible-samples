# Let's play DEMO

## 1. Fork

```
https://github.com/VTRyo/ansible-samples.git
```

## 2. 暗号化なしで実行してみる

```
cd ansible-sample/ansible-vault
```

```
ansible-playbook -i hosts vault-playbook.yml --check
```

実行結果にはメッセージが表示されたでしょうか？

## 3. 変数を暗号化する

```
ansible-vault encrypt group_vars/all
New Vault password: <input your password>
```

```
cat group_vars/all
```

暗号化されたか確認する。

## 4. 2.の作業を再度実行してみる

```
ansible-playbook -i hosts vault-playbook.yml --check
```

実行できないことを確認する。

## 5. 暗号化されたファイルを読み込んで実行する

```
ansible-playbook -i hosts vault-playbook.yml --check --ask-vault-pass
Vault password: <inpiut your password>
```

2.と同様の結果が得られたか確認する。

## 6. 暗号化をかけたファイルの中身を確認する

```
ansible-vault view group_vars/all
Vault password: <input your password>
```

中身が確認できたか確認する。

## 7. 暗号化ファイルを複合化する

```
ansible-vault decrypt group_vars/all 
Vault password: <input your password>
Decryption successful
```

```
cat group_vars/all
```

ファイルが平文になっていることを確認する。


# HOW TO ansible-vault

* syntax

```
Usage：ansible-vault [create|decrypt|edit|encrypt|encrypt_string|rekey|view] [options] [vaultfile.yml]
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
