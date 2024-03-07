Репозиторий для создания образа в Vagrant для Fedora 38 c ядром 6.7.7
Образ generic/fedora38 взят из официального репозитория, обход блокировки через proxy

Настройки proxy через переменные окружения

export https_proxy='http://login:password@ip:port/'
export VAGRANT_HTTP_PROXY=${http_proxy}
export VAGRANT_NO_PROXY="127.0.0.1"

Установлен плагин для интеграции VMBoxGuestTools
vagrant plugin install vagrant-vbguest

Установка ядра

Включаем основной репозиторий с ядрами
sudo dnf copr enable @kernel-vanilla/mainline-wo-mergew

Обновляем пакеты, перегружаемся
sudo dnf upgrade 'kernel*'

Проверяем
cat /proc/version

Для управления конфигурацией ядра можно использовать утилиту grubby
Список установленных ядер
sudo grubby --info=ALL | grep -E "^kernel|^index”

Выбираем нужное ядро, перегружаемся
sudo grubby --set-default-index=0
