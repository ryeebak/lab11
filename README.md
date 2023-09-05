# lab11
Вначале создадим папки install и tmp, скачаем необходимые архивы, распакуем и установим содержимое.
```
$ cd ~
$ mkdir install
$ mkdir tmp
$ export HOME_PREFIX=`pwd`/install
$ echo $HOME_PREFIX
$ export USERNAME=`whoami`
cd tmp
$ wget https://github.com/libevent/libevent/releases/download/release-2.1.8-stable/libevent-2.1.8-stable.tar.gz
$ tar -xvzf libevent-2.1.8-stable.tar.gz
$ cd libevent-2.1.8-stable
$ ./configure --prefix=${HOME_PREFIX}
$ make && make install
$ cd ..
$ wget http://invisible-island.net/datafiles/release/ncurses.tar.gz
$ tar -xvzf ncurses.tar.gz
$ cd ncurses-5.9
$ ./configure --prefix=${HOME_PREFIX}
$ make && make install
$ cd ..
$ wget https://github.com/tmux/tmux/releases/download/2.5/tmux-2.5.tar.gz
$ tar -xvzf tmux-2.5.tar.gz
$ cd tmux-2.5
$ ./configure --prefix=${HOME_PREFIX} CFLAGS="-I${HOME_PREFIX}/include -I${HOME_PREFIX}/include/ncurses" LDFLAGS="-L${HOME_PREFIX}/lib"
$ make && make install
$ cd ..
```
После этого установим ngrok согласно туториалу на официальном сайте и создадим аккаунт и ключ.
![изображение](https://github.com/ryeebak/lab11/assets/124439291/eac61a10-7a86-448f-a190-49deafbf1c32)
Поднимем свой сервер с помощью команды ```ngrok tcp 22```
![изображение](https://github.com/ryeebak/lab11/assets/124439291/cac7ea70-9e88-4d12-af35-a6a3db935b48)
После этого попробуем подключиться к серверу с другого устройства.
Воспользуемся командой ```ssh admin@0.tcp.eu.ngrok.io -p 17692``` (порт отличается от предыдущего, поскольку он обновляется после каждого перезапуска сервера, которых было достаточное количество в попытках разобраться, как всё работает)
admin - username пользователя системы, на которой запущен сервер.
![изображение](https://github.com/ryeebak/lab11/assets/124439291/ca41b6b9-46b9-4af4-98b6-bcad86667cd7)
Мы успешно подключились к нашему серверу с другого устройства, что видно по последнему скриншоту (столбец opn).




