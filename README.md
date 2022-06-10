# ExamenFinalDocker

INTRODUCCION:

En este examen explicare como desarrollar, iniciar y finalmente subir a docker hub, un proyecto utilizando docker-compose, para que este pueda ser visualizado mediante en localhost. En este examen utilizaremos la aplicacion creada por Maximo como ejemplo, ya que no se ha podido desplegar nuestro propio proyecto de forma eficiente.

CONFIGURACION PRINCIPAL Y DOCKER-COMPOSE:YML:

Empezaremos creado un repositorio donde donde almacenaremos toda nuestra informacion i en el añadiremos el proyecto que queramos desplegar. En mi caso, he creado una carpeta llamada Examen final, y otra llamada target, donde he introducido el proyecto en formato ".war"


![1](https://user-images.githubusercontent.com/91748429/173106002-ca6f6e39-5080-4817-8426-743b3d959c79.PNG)


A continuacion añadiremos la base de datos, en una carpeta aparte llamada mysql-dump.


![2](https://user-images.githubusercontent.com/91748429/173106613-6c5fbd58-0fc9-405a-9634-7a565e1290ef.PNG)


A continuacion crearemos un fichero docker-compose.yml. Este archivo estara dividido en tres partes:

·La parte de "db" (database) que se encargara de crear el contenedor de la base de datos. Esta se conectara mediante las credenciales que nosotros le proporcionemos a nuestra base de datos (en este caso alojada en la carpeta target), y se situara en el pueto 3306 del localhost. El nombre de la base de datos tendra que ser definida igual que dentro de la base, en este caso testdb1, para que la conexion funcione correctamente.


![3](https://user-images.githubusercontent.com/91748429/173107926-a77ff8d2-f18b-4b8f-a201-e5062bb30dbb.PNG)


·La parte de phpmyadmin podra ser accedida en este caso mediante el puerto 8081:80 del localhost, con las credenciales que nosotros le proporcionesmos, esta vez entraremos con el usuario testuser y la contraseña root (creado en bd). En la parte de environment añadiremos el nombre del HOST, en este caso sera db, y la contraseña, que sera root. 


![4](https://user-images.githubusercontent.com/91748429/173108956-ac7abd14-ca76-410d-98e8-198ec3dddca6.PNG)


·Por ultimo acabaremos este documento con la parte web, que utilizara la imagen de Tomcat. En esta parte llamaremos al archivo de nuestro proyecto, que estara guardado en la carpeta target como un .war, como hemos dicho con anterioridad. Seguiremos indicando en que puerto queremos que se despliegue nuestro proyecto y finalizaremos definiendo las credenciales, de la misma forma que hemos hecho arriba.


![5](https://user-images.githubusercontent.com/91748429/173110934-dc07e927-9259-4df2-abe5-e69b486ac2d6.PNG)


PASOS PARA EL DESPLIEGUE DE LA APLICACION:


Finalizaremos esta parte juntando todo de manera correcta y ejecutando este docker-compose con el comando "docker-compose up -d"


![6](https://user-images.githubusercontent.com/91748429/173111846-0b99a9d5-6805-4701-ada4-77739511db9e.PNG)


Al haber hecho esto comprobaremos que las partes funcionen entrando a los dos puertos anteriormente definidos del localhost (8081,8082 en este caso). 


![7](https://user-images.githubusercontent.com/91748429/173112790-c82e88e3-1dd1-4678-8b8a-b173d1141ca7.PNG)

![8](https://user-images.githubusercontent.com/91748429/173112807-fd93cdd6-4c1f-4a99-a0d6-bd3219843420.PNG)


Como podemos comprobar todo funciona perfectamente, hemos podido acceder a la parte de phpmyadmin con las credenciales proporcionadas y como podemos ver en desde alli podemos acceder a la base de datos USER, que tambien se ha creado correctamente. Si accedemos al puerto 8082/LoginWebApp nos mostrara la pagina de login que funcionara perfectamente, aunque al acceder nos mostrara un error de usuario incorrecto, que es completamente normal.


![9](https://user-images.githubusercontent.com/91748429/173113755-643b8627-f778-41ee-a9ba-e32c7100d2a6.PNG)


PREPARACION Y SUBIDA DE LA IMAGEN A DOCKER HUB:


A continuacion proseguiremos haciendo un push de nuestro proyecto a docker hub. Para esto necesitaremos primero logearnos en nuestra cuenta de docker, de esta manera:


![10](https://user-images.githubusercontent.com/91748429/173116180-7c41ed10-96d8-4b5e-ad6c-b0ff8bacc704.PNG)


Seguiremos creando un dockerfile en nuestra carpeta y en este podremos un seguido de instrucciones para la creacion de la imagen:


![11](https://user-images.githubusercontent.com/91748429/173117510-c055d27f-769c-464c-bdaf-ab4b13599cdc.PNG)


A continuacion ejecutaremos el comando docker build para crear la imagen: (Aunque la he tenido que crear dos veces con el nombre correcto)


![12](https://user-images.githubusercontent.com/91748429/173120979-d3184cce-68b2-4485-9b9a-aaffdd519866.PNG)

![12 1](https://user-images.githubusercontent.com/91748429/173120997-f058d3a6-dc0f-46c2-a80d-a57b5a7b8caf.PNG)


Y finalizariamos todo esto haciendo un docker oush de la imagen:


![13](https://user-images.githubusercontent.com/91748429/173121124-9ec1c3a4-5985-447f-9ed2-7b64e425c0e2.PNG)


Si queremos comprobarlo podemos acceder a nuestro docker hub y ver la imagen:
![14](https://user-images.githubusercontent.com/91748429/173121324-2abd57e9-2e10-40dd-a550-ff0281256ee6.PNG)






ANNEXOS:

Link al contenedor de docker hub:
https://hub.docker.com/r/bernatsistemas/examen





