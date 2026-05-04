# Homework_«Кластеризация и балансировка нагрузки»

# Домашнее задание к занятию "«Кластеризация и балансировка нагрузки» - `Смирнов Максим`

### Задание 1

`Балансировка на 4 уровне по roubdrobin`
![1-level4.jpg](https://github.com/turboturtle-90/Homework_clustering_and_load_balancing/blob/7705286e7aea06eb754ecf0cc6f2510aa3f7173f/1-level4.jpg)

`Текст конфига /etc/haproxy/haproxy.cfg в части балансировки roundronib на 4 уровне приведен ниже :`

```                                                         
listen web_tcp

        bind :1325
        balance roundrobin
        server s1 127.0.0.1:8888 check inter 3s
        server s2 127.0.0.1:9999 check inter 3s
```
---
