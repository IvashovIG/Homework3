1. В Vagrantfile добавлена конфигурация 5го диска.
2. Добавлен скрипт (raid.sh) для создания RAID 5 уровня из 5 дисков.
3. Далее ломаем один из дисков, входящих в состав рейда (mdadm /dev/md0 --fail /dev/sde), удаляем его из рейда (mdadm /dev/md0 --remove /dev/sde) и имитируем замену на исправный диск (mdadm /dev/md0 --add /dev/sde).
4. Дожидаемся окончания перестроения рейда, проверяем работоспособность (mdadm -D /dev/md0).
5. Добавлен скрип (gpt.sh) для создания и монтирования разделов.
В итоге имеем ВМ с RAID5 и 5 смотрированными разделами EXT4.
