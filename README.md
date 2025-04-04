# IvantsovaNastyaGit


![image](https://github.com/user-attachments/assets/e4d00a81-3fae-4a9c-ab5c-0d7a62f3b89d)



Отчет по виртуалке Перед началой установки, нужно установить Linux Oracle на VirtualBox, для этого нужно: Иметь образ Linux Выделить 2+ ядер. Выделать 4096+ МБ оперативы, и обязательно при установки мы выбираем английский язык. Мы переходим к установке docker с использованием grafana. Вводим следующий код: Устанавливаем утилиту Wget
Устанавливает утилиту wget на вашу систему
sudo yum install wget

1.Скачиваем пакет wget, с помощью команды.

sudo yum install wget

![image](https://github.com/user-attachments/assets/af01e319-20a5-4bef-8bb1-eb2e13810d41)

Скачиваем пакет curl

sudo yum install curl

![image](https://github.com/user-attachments/assets/43265fea-784a-4614-b91d-07303ac8ac51)

Скачиваем файл репозитория

sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo

![image](https://github.com/user-attachments/assets/265946fb-1adb-405d-b5a5-6f5a33c48ef6)

Устанавливаем docker

sudo yum install docker-ce docker-ce-cli containerd.io

![image](https://github.com/user-attachments/assets/9c6de58c-ed14-4697-85bf-b1e30458be57)

Мы разрешаем автозапуск и запускаем 

sudo systemctl enable docker --now

![image](https://github.com/user-attachments/assets/e48b4776-e074-47a8-bf88-8f7f60e64ebd)

Получаем последнюю версию docker с помощью api github с помощью команды: COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)

![image](https://github.com/user-attachments/assets/ef930ebf-2bdc-4ee6-af75-fd399de0bf2e)

Загружаем и устанавливаем последнюю версию dosker sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose

![image](https://github.com/user-attachments/assets/f6f2ac62-46c9-4b89-a4e9-3b3c40e9595f)

Данная команда вводится для того чтобы файл docker стал исполняемым sudo chmod +x /usr/bin/docker-compose

![image](https://github.com/user-attachments/assets/940afa7e-6f33-4c52-a27d-e7ef0831851a)

Делаем проверку с помощью ls -l /usr/bin/docker-compose и видим что файл исполняемый -rwxr-xr-x это значит что файл имеет права на чтение, запись и исполнения

![image](https://github.com/user-attachments/assets/e43797a4-3643-4b77-b014-1621aa309618)

Смотрим данной командой какая версия у нас установлена dosker docker-compose --version

![image](https://github.com/user-attachments/assets/e8509858-4fbc-4685-b993-695b60ee8658)

Эта команда использует утилиту git для клонирования (копирования) удаленного репозитория на ваш локальный компьютер.

![image](https://github.com/user-attachments/assets/bc35dc20-679e-4272-8e48-48f3b0496333)

Данная команда используется для смены текущей директрии на указанную папку, то есть в нашем случае она переходит в директорию с именем grafana_stack_for_docker cd grafana_stack_for_docker

![image](https://github.com/user-attachments/assets/d2990928-00f0-4bb0-bcde-5e73e4012235)

Выполняем создание директории (папки) с указанным путем, создаёт полный путь, включая все необходимые промежуточные каталоги sudo mkdir -p /mnt/common_volume/swarm/grafana/config

![image](https://github.com/user-attachments/assets/59515d2c-304e-4002-8ff5-552cd1f6bc11)

Создает несколько директорий внутри указанного пути sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}

![image](https://github.com/user-attachments/assets/3b6744b3-b8ee-4315-bcc8-bb85963b79eb)

Все файлы и каталоги в указанных директориях будут переданы в собственность текущему пользователю. sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}

![image](https://github.com/user-attachments/assets/571ee390-d97e-4d82-b70c-5cf8b5204cbf)

Файл grafana.ini уже существует, команда обновит его временные метки.Если файл не существует, команда создаст новый пустой файл с указанным именем по указанному пути. touch /mnt/common_volume/grafana/grafana-config/grafana.ini

![image](https://github.com/user-attachments/assets/c6a77f4c-c3a5-4da4-96ed-5187a9405d22)

Команда копирует все файлы и подкаталоги из директории config в директорию /mnt/common_volume/swarm/grafana/config/. cp config/* /mnt/common_volume/swarm/grafana/config/

![image](https://github.com/user-attachments/assets/588bbf26-b57b-4168-9743-c0844a278861)

Команда переименовывает файл grafana.yaml в docker-compose.yaml. Можно проверить с помощью команды ls mv grafana.yaml docker-compose.yaml

![image](https://github.com/user-attachments/assets/458ff849-9905-42a4-8d0f-c40b52fac9b7)

Команда создает и запускает контейнеры в фоновом режиме, используя конфигурацию из файла docker-compose.yaml, с правами суперпользователя. sudo docker compose up -d

![image](https://github.com/user-attachments/assets/59e46ec1-d0b9-49cd-9ce7-297e18eb044c)

Получается зайти в Grafana. Ссылка: http//localhost:3000/ Пароль и логин: admin

![image](https://github.com/user-attachments/assets/c2bf37e3-078e-4dbd-8478-c0ae418bc37e)






