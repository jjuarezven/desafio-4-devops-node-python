# Solución desafio 4-devops-node-python

Para solucionar este desafio, fué necesario seguir los siguientes pasos:

1. En el archivo hello-node/app.js se completó el valor por defecto de la variable password para conectarse a la base de datos mysql.

2. En el archivo docker-compose.yaml, dentro de la sección db, se corrigió la ruta al archivo **create_database.sql**.

3. En el archivo docker-compose.yaml, dentro de la sección mq, se agregó una sección volume para que se alamacenen los datos de la cola y se corrigió el puerto del container.

4. En el archivo docker-compose.yaml, dentro de la sección hello-node, se agregó la sección **depends_on** para hacer que se inicie el container de la aplicación node después de que se hayan inciiado los containers de la base de datos y de la cola respectivamente.

5. Ejecutar el comando **docker-compose up -d**.

6. Ir a la url localhost:808 para indicar un sabor:

7. Verificar que el mesanje haya sido procesado por la aplicación de node, puesto en la cola de rabbitmq y almacenado en la tabla Messages de la base de datos hello.

- Entrar al container de la base de datos ejecutando el comando **docker exec -it db bash**.

- Indicar el password (password): **mysql -u root -p**

- Seleccionar la base de datos **hello**: **use hello,**

- Consultar la tabla **Messages**: **select \* from Messages;**
