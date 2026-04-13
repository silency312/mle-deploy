FROM python:3.11-slim

LABEL author=${AUTHOR}
# ${AUTHOR} - это переменная среды

# директория simple_fast_api скопирована в Docker
COPY . ./simple_fast_api
WORKDIR simple_fast_api

# устанавливаем библиотеки из файла requirements.txt
RUN pip3 install -r requirements.txt

# указываем, что директория speeches внутри контейнера будет являться томом
# на этапе сборки docker создаст необходимые файлы на самой виртуальной машине
# в директории /var/lib/docker/volumes/
VOLUME /speeches

# эта инструкция указывает образу, 
# что порт APP_PORT должен быть открыт 'снаружи'
EXPOSE ${APP_PORT}


CMD uvicorn app.main:app --host  0.0.0.0 --port ${APP_PORT}