University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)  
Year: 2025/2026  
Group: U4125    
Author: Sharapova Elizaveta Igorevna  
Lab: Lab3  
Date of create: 15.03.2026  
Date of finished:   

# Лабораторная работа №3
## "Мониторинг с Prometheus и Grafana"
**Описание:**  
третья лабораторная работа по настройке системы мониторинга с использованием Prometheus для сбора метрик и Grafana для визуализации данных.  
**Цель работы:**  
научиться настраивать локальную систему мониторинга, собирать метрики с помощью Prometheus и создавать дашборды в Grafana для визуализации данных.  

### Ход работы
**1. Создание конфигурации Prometheus:**  
1.1 Создание папки `prometheus` для конфигурации:
```
mkdir -p lab3/prometheus
```
1.2 Создание файла `prometheus.yml` со следующим содержимым:   
```
nano prometheus.yml
mv prometheus.yml lab3/prometheus
```  
![Скрин 1](https://github.com/sharapova07/devops-lab-sharapova/blob/2d11b0d9d8ee527eaf7461ca5c799584ab711307/lab3/screenshots_lab3/1%20-(%D1%84%D0%B0%D0%B8%CC%86%D0%BB%20prometheus).png)

**2. Запуск Node Exporter:**  
2.1 Запуск контейнера Node Exporter для сбора системных метрик:  
  
![Скрин 2](https://github.com/sharapova07/devops-lab-sharapova/blob/2d11b0d9d8ee527eaf7461ca5c799584ab711307/lab3/screenshots_lab3/2%20-%20(%D0%B7%D0%B0%D0%BF%D1%83%D1%81%D0%BA%20Node%20Exporter).png)
  
2.2 Проверка работы Node Exporter с помощью `curl http://localhost:9100/metrics`  
  
![Скрин 3](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/3%20-%20(%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B%20NE).png)

**3. Запуск Prometheus:**  
3.1 Создание тома для данных Prometheus и общей сети для контейнеров:
```
docker volume create prometheus-data  
docker network create monitoring
```  
Prometheus - приложение, которое отвечает за сбор метрик. Для их визуализации используется другое приложение - Grafana. Создание общей сети необходимо как раз для того, чтобы они могли работать вместе.  
  
3.2 Запуск контейнера Prometheus из корня репозитория:  
``` 
docker run -d \
      --name prometheus \
      --network monitoring \
      --restart=unless-stopped \
      -p 9090:9090 \
      -v prometheus-data:/prometheus \
      -v $(pwd)/prometheus:/etc/prometheus \
      prom/prometheus \
      --config.file=/etc/prometheus/prometheus.yml \
      --storage.tsdb.path=/prometheus \
      --web.console.libraries=/etc/prometheus/console_libraries \
      --web.console.templates=/etc/prometheus/consoles \
      --storage.tsdb.retention.time=200h \
      --web.enable-lifecycle
``` 
3.3 Проверка работы через открытие `http://localhost:9090` в браузере:  
  
![Скрин 4](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/4%20-%20(%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0%20Prometheus).png)
  
Таким образом, оба источника данных подключены со статусом UP:  
![Скрин 5](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/5%20-(%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0%20%D0%BF%D0%BE%D0%B4%D0%BA%D0%BB%D1%8E%D1%87%D0%B5%D0%BD%D0%B8%D1%8F%20%D0%B8%D1%81%D1%82%D0%BE%D1%87%D0%BD%D0%B8%D0%BA%D0%BE%D0%B2).png)

**4. Запуск Grafana:**  
4.1 Создание тома для данных Grafana:  
```
 docker volume create grafana-data
``` 
4.2 Запуск контейнера Grafana:  
  ![Скрин 6](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/6%20-(%D0%B7%D0%B0%D0%BF%D1%83%D1%81%D0%BA%20%D0%BA%D0%BE%D0%BD%D1%82%D0%B5%D0%B8%CC%86%D0%BD%D0%B5%D1%80%D0%B0%20Grafana)%202.png)

4.3 Проверка работы и вход в Grafana через открытие в браузере: `http://localhost:3000`  
`admin/admin` - логин и пароль
  
![Скрин 7](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/7%20-%20(%D0%B2%D1%85%D0%BE%D0%B4%20%D0%B2%20grafana).png)


**5. Настройка Grafana:**  
5.1 Добавление источника данных Prometheus:  
- Connections → Data Sources → Add data source → Prometheus
- URL: `http://prometheus:9090`
- Save & Test
  
![Скрин 8](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/8%20-%20(%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5%20%D0%B8%D1%81%D1%82%D0%BE%D1%87%D0%BD%D0%B8%D0%BA%D0%B0%20%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85%20Prometheus).png)  

5.2 Создание дашборда:  
- Create → Dashboard → Add visualization → Prometheus
- Добавление метрики: `node_cpu_seconds_total`
- Сохранение дашборда
  
![Скрин 9](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/9%20-%20(%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5%20%D0%B4%D0%B0%D1%88%D0%B1%D0%BE%D1%80%D0%B4%D0%B0).png)
  
Метрика node_cpu_seconds_total - показывает общее время работы процессора в разных режимах (например, ожидание, бездействие, пользовательский и системный).

**6. Тестирование системы:**  
6.1 Проверка всех контейнеров через команду `docker ps`:
![Скрин 10](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/10%20-%20(%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0%20%D0%B2%D1%81%D0%B5%D1%85%20%D0%BA%D0%BE%D0%BD%D1%82%D0%B5%D0%B8%CC%86%D0%BD%D0%B5%D1%80%D0%BE%D0%B2).png)

6.2 Успешный сбор метрик в Prometheus:  
![Скрин 11](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/11%20-%20(%D1%81%D0%B1%D0%BE%D1%80%20%D0%BC%D0%B5%D1%82%D1%80%D0%B8%D0%BA%20%D0%B2%20Prometheus).png)

6.3 Создание нескольких графиков для разных метрик (CPU, память, диск) и проверка их отображения в Grafana:    
`node_cpu_seconds_total` - загрузка процессора: сколько времени процессор работал в разных режимах, например, пользовательском или системном  
`node_memory_MemFree_bytes` - свободная оперативная память в байтах  
`node_network_receive_bytes_total` - сколько данных было получено по сети    
`node_filesystem_free_bytes` - свободное место на диске в байтах  
  
![Скрин 12](https://github.com/sharapova07/devops-lab-sharapova/blob/65e7a65a04c79c7a9b36bd32b2a52ae22c57431a/lab3/screenshots_lab3/12%20-%20(%D0%B5%D1%89%D0%B5%20%D0%B3%D1%80%D0%B0%D1%84%D0%B8%D0%BA%D0%B8).png)

  
### Результаты лабораторной работы
В результате данной работы:  
- настроена система мониторинга на базе Docker: Node Exporter собирает метрики, Prometheus их хранит, Grafana визуализирует
- создан дашборд с различными графиками
- все компоненты работают и взаимодействуют через общую сеть
- написан отчет по проделанной работе с описанием выполненных задач и скриншотами

