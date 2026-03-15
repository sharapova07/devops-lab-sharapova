University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)  
Year: 2025/2026  
Group: U4125    
Author: Sharapova Elizaveta Igorevna  
Lab: Lab2  
Date of create: 15.03.2026  
Date of finished:   

# Лабораторная работа №2
## "CI/CD для Docker приложения"
**Описание:**  
вторая лабораторная работа по настройке CI/CD пайплайна для автоматической сборки, публикации и деплоя Docker образа из первой лабораторной работы.      
**Цель работы:**  
научиться настраивать автоматизированные пайплайны для сборки Docker образов, их публикации в registry и автоматического деплоя при изменении кода.

### Ход работы
**1. Подготовка проекта:**  
1.1 Создание нового [репозитория](https://github.com/sharapova07/devops-lab-sharapova-lab2-.git) и файлов `app.py`, `requirements.txt`, `Dockerfile` с содержимым и условиями из первой лабораторной работы со звездочкой  
  
![Скрин 1](https://github.com/sharapova07/devops-lab-sharapova/blob/f95d3e1c59a93c228d5034ed57d89cfb190ff755/lab2/screenshots_lab2/1%20-%20(%D0%BD%D0%BE%D0%B2%D1%8B%D0%B8%CC%86%20%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B8%CC%86%20lab2).png) 
1.2 Создание аккаунта и нового репозитория для образа на Docker Hub  
  
![Скрин 2](https://github.com/sharapova07/devops-lab-sharapova/blob/f95d3e1c59a93c228d5034ed57d89cfb190ff755/lab2/screenshots_lab2/2%20-%20(%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B8%CC%86%20%D0%BD%D0%B0%20Docker%20Hub)%202.png) 


**2. Настройка секретов:**  
2.1 Добавление в настройках GitHub репозитория секретов:  
`DOCKER_USERNAME` - логин на Docker Hub  
`DOCKER_PASSWORD` - пароль для Docker Hub  
![Скрин 3](https://github.com/sharapova07/devops-lab-sharapova/blob/f95d3e1c59a93c228d5034ed57d89cfb190ff755/lab2/screenshots_lab2/3%20-%20(%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%CC%86%D0%BA%D0%B0%20%D1%81%D0%B5%D0%BA%D1%80%D0%B5%D1%82%D0%BE%D0%B2)%202.png)

**3. Настройка GitHub Actions:**  
3.1 Создание папки `.github/workflows/` в корне проекта: 
```
mkdir -p .github/workflows
```
3.2 Создание файла `docker-build.yml` с пайплайном, который должен:
- запускаться при пуше в main ветку
- использовать Ubuntu как runner
- выполнять checkout кода
- настраивать Docker Buildx
- логиниться в Docker Hub используя секреты
- собирать и пушить образ с тегом username/my-flask-app:latest
- добавлять шаг деплоя (можно просто echo сообщение)
![Скрин 4](https://github.com/sharapova07/devops-lab-sharapova/blob/f95d3e1c59a93c228d5034ed57d89cfb190ff755/lab2/screenshots_lab2/4%20-%20(docker-build).png)
  
> Весь этап в одном скрине
   
![Скрин 5](https://github.com/sharapova07/devops-lab-sharapova/blob/f95d3e1c59a93c228d5034ed57d89cfb190ff755/lab2/screenshots_lab2/5%20-%20(%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%CC%86%D0%BA%D0%B0%20GitHub%20Actions).png)


**4. Тестирование пайплайна:**  
4.1 Коммит и пуш в main ветку через команды:
```
git commit -m "Creating docker-build.yml"  
git push 
```
4.2 Проверка выполнения пайплайна в разделе Actions
![Скрин 6](https://github.com/sharapova07/devops-lab-sharapova/blob/f95d3e1c59a93c228d5034ed57d89cfb190ff755/lab2/screenshots_lab2/6%20-%20(%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0%20%D0%B2%20Actions).png)  
  
4.3 Проверка, что образ появился в Docker Hub
![Скрин 7](https://github.com/sharapova07/devops-lab-sharapova/blob/f95d3e1c59a93c228d5034ed57d89cfb190ff755/lab2/screenshots_lab2/7%20-%20(%D0%BE%D0%B1%D1%80%D0%B0%D0%B7%20%D0%B2%20Docker%20Hub).png) 

4.4 Проверка логов выполнения каждого шага  
![Скрин 8](https://github.com/sharapova07/devops-lab-sharapova/blob/f95d3e1c59a93c228d5034ed57d89cfb190ff755/lab2/screenshots_lab2/8%20-%20(%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0%20%D0%BB%D0%BE%D0%B3%D0%BE%D0%B2).png) 

  
### Результаты лабораторной работы
В результате данной работы:  
- создан аккаунт на Docker Hub
- настроены секреты для безопасной работы с registry
- настроены CI/CD пайплайн с GitHub Actions
- изучена автоматическая сборка и публикация Docker образа в Docker Hub
- написан отчет по проделанной работе с описанием выполненных задач и скриншотами
