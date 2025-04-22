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

Добавляю к себе в GitHub папку с файлами. Файл prometeus.yaml называю сразу правильно prometheus.yaml

![image](https://github.com/user-attachments/assets/7256b9ca-57f6-47c5-94ca-51232e262c36)

Данная команда открывает файл docker-compose.yaml в текстовом редакторе vi с правами суперпользователя, что позволит редактировать его содержимое. sudo vi docker-compose.yaml

![image](https://github.com/user-attachments/assets/b458c44f-73e8-4abe-b1e0-2be4ce8625e6)

Запускаем и создаем контейнеры если те не запущенны sudo docker compose up -d

![image](https://github.com/user-attachments/assets/11339948-ee06-4049-a348-e064149b0167)

Отсанавливаем запущенные контейнеры без удаления sudo docker compose stop

![image](https://github.com/user-attachments/assets/472ad363-ae1f-47e9-9a3c-af882b28d63d)

Данная команда используется для оставновки и удаления контейнеров, сетей, томов если они созданы с помощью Docker Compose sudo docker compose down

![image](https://github.com/user-attachments/assets/40dfa6cd-e2bf-4a18-9d94-399b7ef3fb99)

Работа с репозиторием, клонируем репозироторий sudo git clone https://github.com/nivxxo/IvantsovaNastyaGit.git

![image](https://github.com/user-attachments/assets/5138eed4-0a0f-4ffe-bdb0-133563e4a9df)

Переходим в каталог IvantsovaNastyaGit и смотрим файл

cd IvantsovaNastyaGit, а после ls

sudo rm README.md открваем файл README.md с правами sudo

Перехожу в каталог 1 и смотрим его содержимое cd 1 и ls

Смотрим полный путь pwd

![image](https://github.com/user-attachments/assets/a9266b7d-9872-47b7-9ad5-4d2193d6a469)

Копирование всех файлов GitHub с помощью sudo cp -r /home/ivantsova/grafana_stack_for_docker/IvantsovaNastyaGit/1* /home/ivantsova/grafana_stack_for_docker

![image](https://github.com/user-attachments/assets/9ef27a32-1b20-4d89-8600-38006aab6822)

Перехожу в config cd /mnt/common_volume/swarm/grafana/config

![image](https://github.com/user-attachments/assets/741dedcf-fd7f-4feb-bdbb-17551285ce0c)

Cоздаем копию файла prometheus.yaml с именем prometheus.yaml1. `cp prometheus.yaml prometheus.yaml1

![image](https://github.com/user-attachments/assets/44cb767c-9d9d-49ff-8b38-c81026e890b8)

sudo cp prometheus.yaml /mnt/common_volume/swarm/grafana/config выполняет копирование файла prometheus.yaml в указанную директорию с использованием sudo Смотрим с помощью команды ls

![image](https://github.com/user-attachments/assets/56a904dd-8f03-4e55-b0f4-30dba7f6df64)

Открываем файл docker-compose.yaml для проверки и редоктирования содержимого

![image](https://github.com/user-attachments/assets/323101ca-47db-4d5e-8cd7-69a92e1f824e)

Открываем файл prometheus.yaml для исправления и проверки
Переходим на grafana_stack_for_docker и запускаем Grafana с помощбю команды sudo docker compose up -d

![image](https://github.com/user-attachments/assets/75ea4c8d-cf82-4679-99ef-bac3d791a778)

Работа с графаной

Переходим по ссылке http://localhost:3000/

Вводим и в логин и в пароль admin

выбираем вкладку Dashboards и создаем Dashboard

жмем кнопку +Add visualization, а после "Configure a new data source"

выбираем Prometheus

Код Prometheus http://prometheus:9090

![image](https://github.com/user-attachments/assets/5544903d-0bff-4bda-9eb8-a7c54a27368b)

Жму на save test и проверяю что все идет отлично

![image](https://github.com/user-attachments/assets/561945b4-dec8-4072-bdd0-c405d9e9ea1c)

Импортирую 1860 dashboard

![image](https://github.com/user-attachments/assets/04c245f1-eef4-489f-b092-45bfea66b4fb)

Выбираю prometheus и импортирую

![image](https://github.com/user-attachments/assets/19541de2-291a-4efa-9291-849f154742ec)

Результат:
![image](https://github.com/user-attachments/assets/5d674364-5c64-4960-88a4-124c5fa3fb56)

Victoria

Вводим команду echo -e "# TYPE light_metric1 gauge\nlight_metric1 0" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus которая, отправляет бинарные данные (например, метрики в формате Prometheus) на локальный сервер, который слушает на порту 8428.

![image](https://github.com/user-attachments/assets/93a43d7c-c7d8-4d61-bc5e-91fae0f01118)

Переходим в браузере по ссылке http://localhost:8428/, открывается такое меню в нём нужно выбрать vmui

![image](https://github.com/user-attachments/assets/ced6e2ae-e659-4243-89b8-bf977024e683)

Вписываем light_metric1 и нажимаем Execute Query

![image](https://github.com/user-attachments/assets/68bc218b-7a4d-4a26-9c8f-cd2c1ec46b37)

Переходим на http://localhost:3000 выбираем Dashboard и нажимаем New Dashboard, далее Add Visualization

Вписываем:

Name: VikMetrics

Connection: http://victoriametrics:8428

Нажимаем Save & Test

Вписываем light_metric1, выходит панель с графиком, где есть активность light_metric1

![image](https://github.com/user-attachments/assets/2dee46d3-b757-451b-8976-5cf4c073fa20)

Устанавливаем по аналогии с первой виртуальной машиной вторую. Устанавливаем гостевые дополнения. 

Устанавливаем утилиту curl, она используется для передачи данных с использованием различных сетевых потоков.

sudo yum install curl

![image](https://github.com/user-attachments/assets/4d4950c1-ab80-4de3-b3b4-109b98a4155a)

Устанавливаем утилиту Wget

sudo yum install wget

![image](https://github.com/user-attachments/assets/82f1f0dd-f27d-4e1f-9db2-34844b4c09c3)

Выполняем клонирование удаленного репозитория git, расположенного по указанному url с помощью команды

git clone https://github.com/skl256/grafana_stack_for_docker.git

![image](https://github.com/user-attachments/assets/32d979d4-950a-45e1-913b-567b323eeae9)

Выполняем команду sudo yum install wget tar. Устанавливает пакеты wget (для загрузки файлов) и tar (для распаковки архивов)

![image](https://github.com/user-attachments/assets/68d8937d-fa28-483c-ad0e-b68ba76400a2)

Устанавливаем Chrony. Chrony — это реализация протокола NTP (Network Time Protocol), которая позволяет синхронизировать системное время с серверами времени в сети. Она особенно полезна в системах, где важно точное время (например, серверы, кластеры, базы данных).

sudo yum install chrony

![image](https://github.com/user-attachments/assets/801ce911-5421-458a-9204-de365428a001)

Включаем Chrony systemctl enable chronyd

![image](https://github.com/user-attachments/assets/78f794c9-6dc5-4af6-8edd-0320d2144ecd)

Запускаем Chrony systemctl start chronyd

![image](https://github.com/user-attachments/assets/7d75fd3f-c541-4a07-ba60-e0fbd614a2e4)

Проверяем включен ли getenforce, в данном случае он включен

![image](https://github.com/user-attachments/assets/07e00a6b-2108-4202-9cb0-6001c401eac2)

Отключаем с помощью двух команд setenforce 0 и sed -i 's/^SELINUX=.*/SELINUX=disabled/g' /etc/selinux/config

![image](https://github.com/user-attachments/assets/23c36caf-28d1-4208-87d0-346459e36142)

![image](https://github.com/user-attachments/assets/2a8933ac-3a58-4eca-b9ab-efdb80441f39)

Скачакиваем Prometheus. 3.3.0 / 2025-04-15 версия. https://prometheus.io/download/ wget https://github.com/prometheus/prometheus/releases/download/v3.3.0/prometheus-3.3.0.linux-amd64.tar.gz

![image](https://github.com/user-attachments/assets/227fde44-2051-46cb-872c-647b4f32c825)

Создание каталогов для Prometheus 

sudo mkdir /etc/prometheus /var/lib/prometheus

![image](https://github.com/user-attachments/assets/f65c526c-c3f7-44a0-90bb-ce86a9d1e111)

Распаковываю архив Prometheus tar -zxf prometheus-*.linux-amd64.tar.gz

![image](https://github.com/user-attachments/assets/a830e3f5-e57e-4cc0-b424-052e869a2958)

Перехожу в распакованную папку cd prometheus-*.linux-amd64

![image](https://github.com/user-attachments/assets/629542f4-efb9-4690-a53d-379e0170233c)

Проверим текущию директорию pwd

![image](https://github.com/user-attachments/assets/7ebc28ec-3c30-4aff-8e3c-e6f23afa64b7)

Раскидаем по папкам системы файлы Prometheus с помощбю команд: sudo cp prometheus promtool /usr/local/bin/ cp prometheus.yml /etc/prometheus/

![image](https://github.com/user-attachments/assets/23f3c724-1056-44d0-88a1-b7b890bbde0f)

Очищаем временные файлы с помощью команды cd .. && rm -rf prometheus-*.linux-amd64/ && rm -f prometheus-*.linux-amd64.tar.gz

![image](https://github.com/user-attachments/assets/8500181f-a984-4a3f-93b2-5f9678ca9b88)

Снова выполняем pwd для повторной проверки директории

![image](https://github.com/user-attachments/assets/8ee3f40c-b71e-43fb-bc21-2f70feaa7c92)

Выполняем ls -l для проверки содержимого в директории

![image](https://github.com/user-attachments/assets/a5450d12-b5e6-4136-bc6f-8b6bbb889805)

