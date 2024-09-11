# Сборка ЯДРА Linux из исходников


Шаг 1. Загрузите исходный код 

	1. Посетите официальный сайт ядра www.kernel.org и загрузите последнюю версию.
	https://www.kernel.org/

	2. Откройте терминал и используйте команду wget для загрузки исходного кода ядра Linux:
	$ wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.10.9.tar.xz

Шаг 2: извлеките исходный код
	
	1. Разархивируйте архив
	$ tar xvf linux-6.10.9.tar.xz

Шаг 3: Установите необходимые пакеты
	
	1. Установка пакетов
	$ sudo apt-get install git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc flex libelf-dev bison

Шаг 4: Настройте ядро

	1. Перейдите к каталогу linux-6.10.9. с помощью команды cd:
	$ cd linux-6.10.9

	2. Скопируйте существующий файл конфигурации с помощью команды cp:
	$ cp -v /boot/config-$(uname -r) .config

	3. Чтобы внести изменения в файл конфигурации, выполните команду make:
	$ make defconfig

Шаг 5: Соберите ядро

	1. Начните сборку ядра, выполнив следующую команду:
	$ make

	2. Установите необходимые модули с помощью этой команды:
	$ sudo make modules_install

	3. Наконец, установите ядро, набрав:
	$ sudo make install

Шаг 6. Обновите загрузчик (необязательно)

	Загрузчик GRUB - это первая программа, которая запускается при включении системы.
	Команда make install выполняет этот процесс автоматически, но вы также можете сделать это вручную.

	1. Обновите initramfs до установленной версии ядра:
	$ sudo update-initramfs -c -k 6.10.9

	2. Обновите загрузчик GRUB с помощью этой команды:
	$ sudo update-grub

Шаг 7: Перезагрузите и проверьте версию ядра

	$ uname -mrs	


# Обновдение Ядра в базовой системе

Шаг 1: Руками добавил новую версию ядра. Для этого выполнил следующее:

	1. Загрузил пакеты

	wget -c https://kernel.ubuntu.com/mainline/v6.6.9/amd64/linux-headers-6.6.9-060609-generic_6.6.9-060609.202401011332_amd64.deb
 	wget -c https://kernel.ubuntu.com/mainline/v6.6.9/amd64/linux-headers-6.6.9-060609_6.6.9-060609.202401011332_all.deb
  	wget -c https://kernel.ubuntu.com/mainline/v6.6.9/amd64/linux-image-unsigned-6.6.9-060609-generic_6.6.9-060609.202401011332_amd64.deb
   	wget -c https://kernel.ubuntu.com/mainline/v6.6.9/amd64/linux-modules-6.6.9-060609-generic_6.6.9-060609.202401011332_amd64.deb

Шаг 2: Установил пакеты

	1. sudo dpkg -i *.deb
 
