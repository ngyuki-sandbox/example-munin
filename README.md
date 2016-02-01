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
ansible-playbook all.yml
```

ローカルで http://localhost:1234/ を開く。

```sh
open http://localhost:1234/
```

`munin:pass` でログインする。
