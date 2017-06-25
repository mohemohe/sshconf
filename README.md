# sshconf
~/.ssh/conf.d/**/*.sshconf into ~/.ssh/config

## これ is なに

sshのconfigにincludeが追加されてやったー！って喜んでたら、zshのpreztoでサジェストされなくて死んだ  
結局がんばって結合するしかないじゃん

## つかいかた

`sshconf -i`で`~/.ssh/conf.d`と`~/.ssh/conf.d/10-original`を作成する  
使用中の`~/.ssh/config`を`~/.ssh/conf.d/10-original/config.sshconf`に待避する

`sshconf -g`で`~/.ssh/conf.d`以下の`.sshconf`拡張子のファイルを結合して`~/.ssh/config`に書き出す
