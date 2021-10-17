## laravel sailを使った環境構築のメモ
### 環境情報  
wslは規定としてUbuntu20.04を設定している状態
```
> wsl -l -v
  NAME                   STATE           VERSION
* Ubuntu-20.04           Running         2

> docker --version
Docker version 20.10.8, build 3967b7d

WindowsのバージョンはWindows 10 Home
DockerDesktopのバージョンは4.4.1
```

### laravel-sailのプロジェクト作成、Gitにコミット＆プッシュ
VSCodeのターミナル(cmd)で以下作業  
curl～～のコマンドの途中でwslで紐づくUbuntu環境のrootパスワードを入力
```
> wsl
$ cd /mnt/c/workspace_git/
$ curl -s https://laravel.build/laravel-sail-example | bash
$ cd laravel-sail-example
$ ./vendor/bin/sail up -d

> git init
> git add -A
> git commit -m "first commit"
> git branch -M master
> git remote add origin https://github.com/imo-tikuwa/laravel-sail-example.git
> git push -u origin master
```

### プロジェクト作成者以外（開発者）の環境構築手順
```
> cd /D c:/workspace_git
> git clone https://github.com/imo-tikuwa/laravel-sail-example.git
> cd laravel-sail-example
> composer install
> cp .env.example .env
> php artisan key:generate
> wsl
$ cd /mnt/c/workspace_git/laravel-sail-example
$ vendor/bin/sail up -d
```
