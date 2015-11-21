## Ubuntu-установка

### Установка Docker

Эта установка совпадает с [официальным руководством Docker](https://docs.docker.com/installation/ubuntulinux/) для Ubuntu

* Откройте терминал

* Необходимое требование - это 64 битная версия Ubuntu, узнайте какая ваша через команду

```
uname -a
```
Получите ответ наподобие

```
Linux aristoteles 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:08:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

x84_64 показывает, что мы используем 64 битную версию (старые ПК могут использовать 32 битную архитектуру и не поддерживаются)

* Какую версию Ubuntu вы установили?

```
cat /etc/issue
```

  * Ubuntu 15.10 -> Wily
  * Ubuntu 15.04 -> Vivid
  * Ubuntu 14.04 -> Trusty
  * Ubuntu 12.04 -> Precise

* добавьте GPG ключ для репозитория пакетов Docker

```apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D```

Если это не произойдёт успешно, не волнуйтесь, позже возможно возникнут некоторые сообщения при установке, но их можно спокойно игнорировать.

* Откройте файл /etc/apt/sources.list.d/docker.list в вашем редакторе или создайте его.

Можете попробовать Nano редактор:

```
sudo nano /etc/apt/sources.list.d/docker.list
```

Подсказки внизу экрана помогут при сохраниении ([STRG]+[O]) и выходе из редактора nano ([STRG]+[X])

* Удалите содержимое файла, если он не пустой.

* Добавьте ОДНУ опцию для вашей версии Ubuntu, которую вы узнали ранее:
  * Ubuntu Precise <br/>
    ```deb https://apt.dockerproject.org/repo ubuntu-precise main```
  * Ubuntu Trusty <br/>
    ```deb https://apt.dockerproject.org/repo ubuntu-trusty main```
  * Ubuntu Vivid <br/>
    ```deb https://apt.dockerproject.org/repo ubuntu-vivid main```
  * Ubuntu Wily <br/>
    ```deb https://apt.dockerproject.org/repo ubuntu-wily main```

* Обновите информацию о пакетах <br/>
  ```sudo apt-get update```

* Удалите любую старую версию Docker <br/>
  ```sudo apt-get purge lxc-docker*```

* Убедитесь, что apt берёт пакеты из правильного репозитория<br/>
  ```apt-cache policy docker-engine``` <br/>
  должен содержать строки с: ``` https://apt.dockerproject.org/repo/```

* Необходимо также установить:
  * для Ubuntu  Precise <br/>
    ```sudo apt-get install linux-image-generic-lts-precise linux-headers-generic-lts-precise xserver-xorg-lts-precise libgl1-mesa-glx-lts-precise```
  * для Ubuntu  Trusty, Vivid или Wily <br/>
    ```sudo apt-get install linux-image-generic linux-headers-generic xserver-xorg libgl1-mesa-glx```

* Если произошла установка новых пакетов, то нужно перезагрузится.

* Установите Docker <br/>
  ```sudo apt-get install docker-engine```

* Убедитесь, что он работает: <br/>
  ```sudo docker run hello-world``` <br/>
  Вы должны увидеть строки, в одной из которых будет сообщение по типу: This message shows that your installation appears to be working correctly. <br/>
  Всякие другие сообщения - можете не обращать внимание.

* Иногда бывает, что докер не запускается в таком случае иногда помогает перезагрузка.

### Установка Docker Compose

* Получите права рута: <br/>
  ```sudo su```

* Загрузите Docker Compose: <br/>
  ```curl -L https://github.com/docker/compose/releases/download/1.4.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose```

* Вернитесь в свою учётную запись: ```exit```

* Дайте права для docker-compose на выполнение задач <br/>
  ```sudo chmod +x /usr/local/bin/docker-compose```

* Проверьте установку: <br/>
  ```docker-compose -v``` <br/>
  В приведенном примере: ```docker-compose version: 1.4.2``` показывает, что установка произошла успешно.
