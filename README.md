# sshconf
~/.ssh/conf.d/**/*.sshconf into ~/.ssh/config

## これ is なに

sshのconfigにincludeが追加されてやったー！って喜んでたら、zshのpreztoでサジェストされなくて死んだ  
結局がんばって結合するしかないじゃん

## つかいかた

`sshconf -i`で`~/.ssh/conf.d`と`~/.ssh/conf.d/10-original`を作成する  
使用中の`~/.ssh/config`を`~/.ssh/conf.d/10-original/config.sshconf`に待避する

`sshconf -g`で`~/.ssh/conf.d`以下の`.sshconf`拡張子のファイルを結合して`~/.ssh/config`に書き出す  
`sshconf -g --with-root`で`/root/.ssh/config`にも同じように書き出す

`sshconf --docker-pregenerate`で起動中のdockerコンテナーを、`sshconf --lxc-pregenerate`で起動中のlxcコンテナーをsshconf形式で自動生成する  
生成後に`sshconf -g`で`~/.ssh/config`に書き出して反映させる

`sshconf -e`で`${EDITOR} ~/.ssh/conf.d`をする  
`sshconf -e code`とかするとVSCodeで開くのでべんりify

### man

```
sshconf (-i|-g|-e|-v|-h) [OPTIONS]
  -i, --init, --initialize         : initialize ~/.ssh/conf.d
  -g, --gen,  --generate           : generate ~/.ssh/config
              --docker-pregenerate : pre-generate container of lxc to 88-docker/10-docker-running.sshconf
              --lxc-pregenerate    : pre-generate container of lxc to 89-lxc/10-lxc-running.sshconf
  -e,         --edit [editor]      : open ~/.ssh/conf.d in your favorite editor <3
              --update             : update sshconf
  -v,         --version            : show version
  -h,         --help               : show help

OPTIONS:
              --with-root          : copy ~/.ssh/config to /root/.ssh/config when generate ssh config
```
