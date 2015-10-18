## Установка

В этом уроке используется [Docker](https://www.docker.com/) и [Docker Compose](https://docs.docker.com/compose/), поэтому чтобы начать вам не нужно беспокоится о специальной установке на вашем компьютере. 

Если вы ещё не знакомы с Docker, то не страшно, после того, как вы установите Docker и Docker Compose просто проверяйте, что каждый раз при смайлике ":whale:" возле команды вы находитесь в контейнере.

### Установка Docker и Docker Compose

Если вы работаете с Mac или Windows, то можете загрузить и установить [Docker Toolbox](https://www.docker.com/toolbox).
На Windows вам также понадобится установить ручную Docker Compose начав с пункта **4** здесь: http://docs.docker.com/compose/install/

Если вы работаете с Ubuntu Linux, то для вас есть урок [Ubuntu установка](ubuntu-setup.md).


Если на каком-то этапе в этом уроке вы не уверены, находитесь в контейнере или нет, то выполните команду:

```
whereami
```

и после нажатия enter получите ответ "You are in a container!" или что-то вроде "Command not found". Если вы не в контейнере и команда **not found**, то перейдите в необходимую директорию через команду в вашем терминале (`cd`) и запустите следующую команду:

```
sudo docker-compose run shell
```

Если вы увидите "=> You are in a container!", то тогда у вас всё в порядке и вы можете запускать команды из этого урока. :)

Если хотите более подробно ознакомится с Docker, то можете почитать тут:

  * [Getting started with Docker - Servers for Hackers](https://serversforhackers.com/getting-started-with-docker)
  * [Docker Compose - Quick Start](https://docs.docker.com/compose/#quick-start)

Примите во внимание, что в этом уроке вы увидите команды отмеченные ":whale:" для индикации, что она выполняется в контейнере Docker.
