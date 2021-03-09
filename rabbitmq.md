- [How To Install RabbitMQ on Ubuntu 16.04](https://www.vultr.com/docs/how-to-install-rabbitmq-on-ubuntu-16-04-47)
- [Установка RabbitMq на Debian / Ubuntu](https://www.saqot.com/working/rabbitmq-queue-bundle/setup-rabbitmq-ubuntu.html)


## Rabbitmq users

        # Добавить юзера
        sudo rabbitmqctl add_user cinder CINDER_PASS
        # Изменить пароль юзеру
        sudo rabbitmqctl change_password cinder NEW_PASS
        # Сделать юзера админом
        sudo rabbitmqctl set_user_tags cinder administrator
        # Выставить привелегии юзеру
        sudo rabbitmqctl set_permissions cinder ".*" ".*" ".*"
        # Просмотреть список привелегий
        sudo rabbitmqctl list_permissions
        # Удаление пользователя
        sudo rabbitmqctl delete_user guest
management

## Workers Queues

- [Implementing Worker Applications with RabbitMQ + Node](https://medium.com/@otavioguastamacchia/implementing-worker-applications-with-rabbitmq-node-1a8b7ab98e47)
- [Work Queues (using the Pika Python client)](https://www.rabbitmq.com/tutorials/tutorial-two-python.html)
        