# work_node_exporter

## Роль в Ansible для разворачивания node_exporter с нужными параметрами, как systemd-unit. 
## Необходимо исправить переменные, чтобы система разворачивалась под теми названиями, как требуется, и в необходимых папках.

Файл с переменными лежит по стандартному пути переменных для роли `roles/node_exporter/defaults/main.yml`

Список переменных
 -  `description_node_exporter`: описание будущей службы, которое будет отображаться в `systemctl` 
 -  `netns_unit`: наименование главного `systemd-юнита` в системе, который поднимает `netns(lbrt)` и `bird`
 -  `path_to_node_exporter_scripts`: путь где создастся папка, в которой сгенерируются необходимые скрипты для службы `node-exporter`'а. Прописана `/usr/sbin/node_exp`
 -  `node_exp_script`: наименование, как будет называться скрипт запускающий сам `node_exporter` с нужными параметрами порта и `pid-ID` нужного процесса. Прописано наименование `node_exporter_script`
 -  `node_exp_port`: адрес порта на который будет вещать `node_exporter`. Прописан `9101`
 -  `node_exporter_name_unit`: наименование systemd-юнита для node_exporter. Прописан `my-node-exp `
 -  `path_to_systemd_system`: путь до `/etc/systemd/system`, откуда система берёт `systemd` файлы
 -  `pid_name`: название файла `Bird` процесса или полный путь до него, чтобы по нему выполнять поиск `pid-ID`. Прописан `echo.sh`
 -  `pid_find_script`: наименование скрипта, который будет выполнять поиск `pid-ID` и записывать его в файл в папку `path_to_node_exporter_scripts`, чтобы из него брал инфу `node_exp_script`. Прописан `pid_find`
