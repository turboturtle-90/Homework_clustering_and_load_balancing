# Домашнее задание к занятию "«Кластеризация и балансировка нагрузки» - `Смирнов Максим`

### Задание 1

`Ссылка на .cfg`

https://github.com/turboturtle-90/Homework_clustering_and_load_balancing/blob/593b469a59cef8dcb0deedeb24426b0453281f6e/haproxy.cfg-assignment1 

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

### Задание 2

`Ссылка на .cfg`

https://github.com/turboturtle-90/Homework_clustering_and_load_balancing/blob/593b469a59cef8dcb0deedeb24426b0453281f6e/haproxy.cfg-assignment2 

`Балансировка на 7 уровне по roubdrobin с весовыми множителями и обработкой только при адресации к домену example.com`
![2-weighted-level7.jpg](https://github.com/turboturtle-90/Homework_clustering_and_load_balancing/blob/593b469a59cef8dcb0deedeb24426b0453281f6e/2-weighted-level7.jpg)


`Текст конфига /etc/haproxy/haproxy.cfg в части балансировки roundronib на 7 уровне приведен ниже :`

```                                                         
frontend example  # секция фронтенд
        mode http
        bind :8088
        #default_backend web_servers
        acl ACL_example.com hdr(host) -i example.com
        use_backend web_servers if ACL_example.com

backend web_servers    # секция бэкенд
        mode http
        balance roundrobin
        option httpchk
        http-check send meth GET uri /index.html
        server s1 127.0.0.1:8888 check weight 2
        server s2 127.0.0.1:9999 check weight 3
        server s3 127.0.0.1:9999 check weight 4
```
---
