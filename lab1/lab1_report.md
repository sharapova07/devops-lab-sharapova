University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)  
Year: 2025/2026  
Group: U4125    
Author: Sharapova Elizaveta Igorevna  
Lab: Lab1  
Date of create: 13.03.2026  
Date of finished:   

# Лабораторная работа №1
## "Основы работы с Docker"
**Описание:**  
первая лабораторная работа по изучению основ контейнеризации с использованием Docker. В ходе работы будут изучены базовые концепции Docker, создание образов, запуск контейнеров и управление ими.    
**Цель работы:**  
научиться работать с Docker: устанавливать Docker, создавать Dockerfile, собирать образы, запускать контейнеры и управлять ими.  

### Ход работы
**1. Установка Docker:**  
1.1 Установка Docker Desktop для macOS через официальный сайт  
1.2 Проверка установки командой `docker --version` и запуск тестового контейнера `docker run hello-world`  
    
![Скрин 1](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/1%20(docker%20--version).png)    
1.3 Изучение базовых команд:  
`docker images` — показывает список скачанных образов  
`docker ps` — показывает список запущенных контейнеров  
`docker ps -a` — показывает список всех контейнеров (и запущенных, и остановленных) 
  
![Скрин 2](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/2%20(%D0%B8%D0%B7%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D0%B5%20%D0%B1%D0%B0%D0%B7%D0%BE%D0%B2%D1%8B%D1%85%20%D0%BA%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4).png)    
  
**2. Работа с готовыми образами:**  
2.1 Cкачивание образа Ubuntu через команду `docker pull ubuntu:latest` и запуск интерактивного контейнера: `docker run -it ubuntu bash`
  
![Скрин 3](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/3%20(%D1%81%D0%BA%D0%B0%D1%87%D0%B8%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5%20%D0%BE%D0%B1%D1%80%D0%B0%D0%B7%D0%B0%20Ubuntu).png)    
2.2 Установка внутри контейнера пакета `curl`
```
apt update && apt install -y curl 
```
![Скрин 4](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/4%20(%D1%83%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0%20%D0%BF%D0%B0%D0%BA%D0%B5%D1%82%D0%B0%20'curl').png)    
2.3 Проверка установки через команду `curl --version` и выход из контейнера `exit`
  
![Скрин 5](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/5%20(%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0%20%D1%83%D1%81%D1%82%D0%B0%D0%B2%D0%BD%D0%BE%D0%B2%D0%BA%D0%B8).png)    
  
**3. Запуск веб-сервера:**  
3.1 Запуск контейнера с nginx  
```  
docker run -d -p 8080:80 --name web-server nginx:alpine  
```  
![Скрин 6](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/6%20(%D0%B7%D0%B0%D0%BF%D1%83%D1%81%D0%BA%20%D0%BA%D0%BE%D0%BD%D1%82%D0%B5%D0%B8%CC%86%D0%BD%D0%B5%D1%80%D0%B0%20%D1%81%20nginx).png)    
Запускается веб-сервер nginx в контейнере, который доступен на локальном компьютере через порт 8080  
  
3.2 Поверка работы в браузере: http://localhost:8080
  
![Скрин 7](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/7%20(%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B%20%D0%B2%20%D0%B1%D1%80%D0%B0%D1%83%D0%B7%D0%B5%D1%80%D0%B5).png)    
3.3 Посмотр логов контейнера `docker logs web-server`
  
![Скрин 8](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/8%20(docker%20logs%20web-server).png)    
3.4 Пдключение к контейнеру `docker exec -it web-server sh`
  
![Скрин 9](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/9%20(docker%20exec%20-it%20web-server%20sh).png)    
Позволяет войти внутрь работающего контейнера для выполнения команд, не останавливая его.
  
**4. Изучение команд по управлению контейнерами:**  
`docker ps` — просмотр всех контейнеров  
`docker stop web-server` — остановка контейнера  
`docker start web-server` — запуск остановленного контейнера  
`docker rm web-server` — удаление контейнера (перед удалением необходимо его остановить)  
`docker rmi nginx:alpine` — удаление образа  
  
![Скрин 10](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/10%20(%D1%83%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5%20%D0%BA%D0%BE%D0%BD%D1%82%D0%B5%D0%B8%CC%86%D0%BD%D0%B5%D1%80%D0%B0%D0%BC%D0%B8).png)

**5. Работа с томами (volumes):**  
5.1 Создание тома, запуск контейнера с томом, подключение к нему, а также создание файла в томе: `echo "Hello from volume" > /data/test.txt`:
```  
docker volume create my-volume   
docker run -it --name volume-test -d -v my-volume:/data ubuntu bash   
docker exec -it volume-test bash  
echo "Hello from volume" > /data/test.txt 
```   
![Скрин 11](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/11%20(%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%D1%81%20%D1%82%D0%BE%D0%BC%D0%B0%D0%BC%D0%B81).png)
5.2 Удаление контейнера, создание нового с тем же томом и проверка факта, что файл сохранился:
```  
docker stop volume-test  
docker rm volume-test  
docker run -it --name volume-test2 -v my-volume:/data ubuntu bash 
cat /data/test.txt  
```   
![Скрин 12](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/12%20(%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%D1%81%20%D1%82%D0%BE%D0%BC%D0%B0%D0%BC%D0%B82).png)  
![Скрин 13](https://github.com/sharapova07/devops-lab-sharapova/blob/09fbbcd221444fbfd160a0c9c4b082421c95cef4/lab1/screenshots_lab1/13%20(%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%D1%81%20%D1%82%D0%BE%D0%BC%D0%B0%D0%BC%D0%B83).png)  
  
Таким образом, том (volume) - это специальное хранилище, которое Docker создает на компьютере, чтобы сохранять данные даже после удаления контейнера.  
  
### Результаты лабораторной работы
В результате данной работы:  
- установлен и настроен Docker  
- изучены основные команды Docker  
- приобретен опыт по работе с готовыми образами  
- изучен процесс запуска и управления контейнерами  
- написан отчет по проделанной работе с описанием выполненных задач и скриншотами  
