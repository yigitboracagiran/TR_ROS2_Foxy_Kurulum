# GEREKLİLİKLER

1- Ubuntu 20.04


# LOKAL AYARLAMA

UTF-8'i destekleyen bir yerel ayarınız olduğundan emin olun. Minimum bir ortamdaysanız (docker konteyneri gibi), yerel ayar; POSIX gibi minimal bir şey olabilir. 

Aşağıdaki ayarlarla bunu test ediyoruz. Ancak, farklı bir UTF-8 destekli yerel ayar kullanıyorsanız da sorun olmamalı.

1- “locale”  komutu ile UTF-8 kontrol ediliyor.

2- “sudo apt update && sudo apt install locales” komutları ile lokal kuruluyor.

3- sudo locale-gen en_US en_US.UTF-8

4- sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

5- export LANG=en_US.UTF-8

6- “locale” komutu ile ayarlar kontrol ediliyor.


# KURULUM KAYNAKLARI

ROS2’yi apt deposunu sistemimize ekliyoruz.

1- sudo apt install software-properties-common

2- sudo add-apt-repository universe

Şimdi de ROS2 GPG anahtarını ekliyoruz.

3- sudo apt update && sudo apt install curl

4- sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

En sonda da depomuzu kaynak listemize ekliyoruz.

5- echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null


# ROS2 PAKETLERİNİN KURULUMU

Depoları kurduktan sonra apt depolarımızın önbelleklerini güncelliyoruz.

1- sudo apt update

ROS2 paketleri, sık sık güncellenen Ubuntu sistemleri üzerine kuruludur. Yeni paketleri kurmadan önce sisteminizin güncel olduğundan emin olmanız her zaman önerilir.

2- sudo apt upgrade

ROS2 masaüstü (ROS-RVIZ-Demos-Tutorials) kurulumu yapılacaktır.

3- sudo apt install ros-foxy-desktop python3-argcomplete


# ORTAMIN KURULUMU

1- Eğer bilgisayarınıza daha önceden kurulu ROS1 varsa .bashrc dosyasını “nano ~/.bashrc” komutu ile açıp “source /opt/ros/noetic/setup.bash” satırının başına “#” ekleyerek yorum satırına almalısınız.

2- Eğer bilgisayarınızda daha önceden kurulu workspace varsa .bashrc dosyasını “nano ~/.bashrc” komutu ile açıp “source /opt/ros/catkin_ws/setup.bash” satırının başına “#” ekleyerek yorum satırına almalısınız.

3- .bashrc dosyasını “nano ~/.bashrc” komutu ile açıp “source /opt/ros/foxy/setup.bash” satırını eklemelisiniz.

4- Ardından terminali kapatıp yeniden açmalısınız, .bashrc dosyası yenilenir.


# DENEMELER

1- “ros2 run demo_nodes_py talker” komutunu yazınız.

2- Diğer komut çalışırken yeni bir terminalde “ros2 run demo_nodes_py listener” komutunu yazdığınızda 1. terminalde talker düğümünün yayınladığı mesajları, 2. terminalde listener düğümü sayesinde görüyor olmalısınız.
