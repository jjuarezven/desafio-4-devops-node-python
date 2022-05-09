# Solución desafio 4-devops-node-python

Para solucionar este desafio, fué necesario seguir los siguientes pasos:

1. En el archivo hello-node/app.js se completó el valor por defecto de la variable password para conectarse a la base de datos mysql.

![image](https://user-images.githubusercontent.com/79205538/167321412-b9e0ccc4-16e1-4e2d-9c1b-1c26083ee175.png)

2. En el archivo docker-compose.yaml, dentro de la sección db, se corrigió la ruta al archivo **create_database.sql**.

![image](https://user-images.githubusercontent.com/79205538/167321444-4bf8f077-e6be-4e22-8d2a-0497c867fa6d.png)

3. En el archivo docker-compose.yaml, dentro de la sección mq, se agregó una sección volume para que se alamacenen los datos de la cola y se corrigió el puerto del container.

![image](https://user-images.githubusercontent.com/79205538/167321470-98f6dab3-5e5b-48d9-8a15-f58931f11959.png)

4. En el archivo docker-compose.yaml, dentro de la sección hello-node, se agregó la sección **depends_on** para hacer que se inicie el container de la aplicación node después de que se hayan inciiado los containers de la base de datos y de la cola respectivamente.

![image](https://user-images.githubusercontent.com/79205538/167321484-fd8954f4-51ba-471f-95ac-fc81e31bac7e.png)

5. Ejecutar el comando **docker-compose up -d**.

6. Ir a la url localhost:808 para indicar un sabor:

![image](https://user-images.githubusercontent.com/79205538/167321501-38377504-1876-458f-9667-5f3108d02045.png)

7. Verificar que el mesanje haya sido procesado por la aplicación de node, puesto en la cola de rabbitmq y almacenado en la tabla Messages de la base de datos hello.

- Entrar al container de la base de datos ejecutando el comando **docker exec -it db bash**.

- Indicar el password (password): **mysql -u root -p**

- Seleccionar la base de datos **hello**: **use hello,**

- Consultar la tabla **Messages**: **select \* from Messages;**

![image](https://user-images.githubusercontent.com/79205538/167321579-4511c9d8-a7e6-403a-b0c2-54dc1f30be3c.png)

