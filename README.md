# louzhixian.github.io

1. to make use of [hexo-all-minifier](https://github.com/chenzhutian/hexo-all-minifier), in mac we should first run

``` bash
$ brew install libtool automake autoconf nasm
```

2. cd into repo root and install node_modules

``` bash
/* repo root dir */

npm i
```

3. everything is ready, we can run it with hexo now

``` bash
/* repo root dir */

hexo s // to run dev server and preview site at localhost:4000

hexo g // to generate static files for deployment

hexo d // deploy to remote git storage
```
