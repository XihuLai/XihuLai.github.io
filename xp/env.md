# 环境配置

### python3 依赖

- apt install python3-pip
- pip3 install PyYAML
- pip3 install oss2

missing git? 

- pip3 install gitpython

missing pg_config ?

- sudo apt-get install libpq-dev
- pip3 install psycopg2

### display issue on local host

export DISPLAY=:0.0

### display issue in container

xhost +si:localuser:root

