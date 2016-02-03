# example munin

Vagrant で仮想環境の作成。

```sh
vagrant up
```

munin master にログイン。

```sh
vagrant ssh munin
```

munin から web へ公開鍵認証でログインできるようにする。

```sh
ssh-copy-id 192.168.33.10
# enter "vagrant"
```

Ansible でプロビジョニング。

```sh
cd /vagrant
ansible all -m ping
ansible-playbook all.yml
```

ローカルで http://localhost:1234/ を開く。

```sh
open http://localhost:1234/
```

`munin:pass` でログインする。

----

See: [Munin を触ってみた - Qiita](http://qiita.com/ngyuki/items/9ceac312d9dadc52d659)

----

- nginx と fcgi で実行するようにしてみました（nginx ブランチ）
- Ansible のプレイブックは上手く動かないかもしれません
