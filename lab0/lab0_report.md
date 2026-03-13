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
Генерация и добавление нового SSH-ключа в учетную запись производилось при помощи следующих команд:  
```
eval "$(ssh-agent -s)"  
touch ~/.ssh/config
open ~/.ssh/config
ssh-add --apple-use-keychain ~/.ssh/id_ed25519  
```
> Добавление нового SSH ключа в учетную запись

![SSH-ключ](https://github.com/sharapova07/devops-lab-sharapova/blob/2e2f89f7240038bc3dd3b248aebfc688f894078c/lab0/screenshots/SSH-%D0%BA%D0%BB%D1%8E%D1%87.png)  
**2. Создание репозитория с названием `devops-lab-sharapova`:**  
**3. Клонирование созданного репозитория себе на компьютер при помощи команды `git clone`:**  
**4. Создание файлов `README.md` и `.gitignor`e:**  
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
**6. Создание файла `CONTRIBUTING.md` с правилами участия в проекте:**  
**7. Коммит с сообщением "Initial project setup" и отправьте изменения в удаленный репозиторий:**  
Выполнен при помощи следующей команды:  
```
git commit -m "Initial project setup"   
git push     
```
**8. Создание Pull Request из ветки `develop` в `main`:**  
**9.Смержила и удалила ветку develop:**  
