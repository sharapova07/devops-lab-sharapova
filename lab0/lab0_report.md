University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)  
Year: 2025/2026  
Group: U4125    
Author: Sharapova Elizaveta Igorevna  
Lab: Lab0  
Date of create: 13.03.2026  
Date of finished:   

# Лабораторная работа №0
## "Создание репозитория и настройка рабочего окружения"
**Описание:**  
вводная лабораторная работа по созданию репозитория и настройке рабочего окружения для изучения DevOps практик.    
**Цель работы:**  
научиться создавать репозитории, настраивать рабочее окружение и изучать основы работы с Git и GitHub.

### Ход работы
**1. Создание аккаунта на GitHub и настройка SSH-ключа для работы с репозиторием:**  
> Создание нового SSH-ключа
```
ssh-keygen -t ed25519 -C "sharapova.liza07@gmail.com"  
```
> Добавление ключа в SSH-агент  
```
eval "$(ssh-agent -s)"  
touch ~/.ssh/config
open ~/.ssh/config
ssh-add --apple-use-keychain ~/.ssh/id_ed25519  
```
> Добавление нового SSH-ключа в учетную запись
![SSH-ключ](https://github.com/sharapova07/devops-lab-sharapova/blob/2e2f89f7240038bc3dd3b248aebfc688f894078c/lab0/screenshots/SSH-%D0%BA%D0%BB%D1%8E%D1%87.png) 
  
**2. Создание репозитория с названием `devops-lab-sharapova`:**   
![Создание репозитория](https://github.com/sharapova07/devops-lab-sharapova/blob/92c2b6b9a0bec1588c8c9e927b6639be39879c6c/lab0/screenshots/C%D0%BE%D0%B7%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5%20%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D1%8F.png)  
  
**3. Клонирование созданного репозитория себе на компьютер при помощи команды `git clone`:**   
![git clone](https://github.com/sharapova07/devops-lab-sharapova/blob/92c2b6b9a0bec1588c8c9e927b6639be39879c6c/lab0/screenshots/Git%20clone%20.png)  
  
**4. Создание файлов `README.md` и `.gitignore`:**  
Для создания файлов использовались следующие команды:  
```
touch README.md
git add README.md
```
```
touch .gitignore  
git add .gitignore    
```
Стандартные исключения для моей операционной системы (macOS) были взяты здесь: [создание .gitignore](https://github.com/github/gitignore)  
  
**5. Создание и переключение на ветку `develop`:**  
Использовались следующие команды:  
```
git branch develop  
git checkout develop
```
  
**6. Создание файла `CONTRIBUTING.md` с правилами участия в проекте через такие же команды, как для создания `README.md` и `.gitignore`**
  
**7. Коммит с сообщением "Initial project setup" и отправка изменений в удаленный репозиторий:**  
Выполнен при помощи следующих команд:  
```
git commit -m "Initial project setup"   
git push     
```
  
**8. Создание Pull Request из ветки `develop` в `main` через веб-интерфейс GitHub**  
**9. Смержила и удалила ветку `develop`:**  
![смержила](https://github.com/sharapova07/devops-lab-sharapova/blob/1b272c6b79b4f637d2de6d7e52f8b1985eafe511/lab0/screenshots/%D0%A1%D0%BC%D0%B5%D1%80%D0%B6%D0%B8%D0%BB%D0%B0%20Pull%20Request%20.png) 
  
### Результаты лабораторной работы
В результате данной работы:  
- создан репозиторий на GitHub
- настроено рабочее окружение  
- изучены основы работы с Git и GitHub
