# Cómo crear un CRUD básico sobre una app Window Form integrando Entity Framework

Seguir los pasos en este orden: 

## Crear el proyecto
Como uno de Windows Form pero NO de .NET Framework, sino como de .NET solamente. 

![img01](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251001153609.png)

Instalar estas librerias en el proyecto: 

![img02](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251001130650.png)


![img03](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251001130730.png)


![img04](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251001130822.png)



Otra forma es por medio de la "Consola de Administrador de paquetes"
![img05](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251001131124.png)


Pegar y correr los siguientes comandos en la terminal:
```shell
>install-package EntityFramework
>install-package Microsoft.EntityFrameworkCore.SqlServer
>install-Package Microsoft.EntityFrameworkCore.Tools
```


OJO: REVISEMOS Y COMPRENDAMOS BIEN LA Estructura del comando a EJECUTAAR;
La fuente de datos: nuestro servidor o ver en el SSMS
Catalogo inicial: nuestra base de datos que nos conectaremos
Seguridad integrada: si nos logueamos con Autenticación de Windows
Encrypt: No va encriptada la conexión.
Luego la herramienta con la cual crearemos nuestro contexto.
Y finalmente la carpeta DAE donde enviaremos toda la salida, SINO EXISTE DEBEMOS CREARLA ANTES DE LA CORRER EL COMANDO.
A CONTINUACION EL COMANDO, MODIFICAR SEGÚN SEA SU CASO
```shell
Scaffold-DbContext "Data Source=localhost\SQLEXPRESS;Initial Catalog=dae;Integrated Security=True;Encrypt=False" Microsoft.EntityFrameworkCore.SqlServer -OutputDir DAE
```

Nota: DAE es el nombre de la carpeta creada dentro del proyecto para que ahi sea el destino de los archivos que se crearán.


### Se crea las entidades o clases de las tablas en nuestra BD:

![img06](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251001155124.png)


### Y el DaeContext.cs

![img07](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251001155205.png)


Ahí tenemos la cadena de conexión donde podemos modificar según sea nuestro caso, o si cambiamos de servidor la BD.

### En el código del Form agregamos  la carpeta DAE para poder hacer referencia a ella, primera línea:
![img08](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251001155323.png)



### Luego, dentro de la class Form1:Form, instanciamos a la clase DaeContext():

```C#
DaeContext context = new DaeContext();
```


![img09](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002220131.png)


Creamos una nueva función cargarTabla();
para cargar con los datos del context el dataGridView

![img10](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002220440.png)


Al evento click del botón Agregar le adicionamos el código siguiente:

![img11](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002220759.png)


Al evento click del DataGridView:

![img12](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002222001.png)

Agregamos el siguiente código, para que al dar click a una tupla o row de la tabla se cargue la info en los textBox:

![img13](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002221856.png)


Modificar algunas propiedades del dataGridView:
1.- Propiedad

![img14](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002222526.png)

2.- Propiedad

![img15](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002222615.png)

3.- Propiedad

![img16](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002222730.png)

4.- Propiedad

![img17](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002222802.png)




Agregamos el botón Eliminar, y al evento Click el siguiente código:

![img18](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002221722.png)


Agregamos el botón Modificar, y al evento click el siguiente código:

![img19](https://github.com/ingkruzitca/how-to-simple-appwf-with-ef/blob/11cb95313e2610b2b58b9129299ba3f3394fbb40/Pasted%20image%2020251002225051.png)



Listo, continuar mejorando la interfaz gráfica,
-----------------
-- .. -- aplicar una búsqueda al grid, agregar un comboBox y llenar con DataSource (tabla desde la BD)...
--- NUNCA DEJEMOS DE PROBAR COSAS, IMAGINEN Y PRUEBEN, INVESTIGUEN COMO SE PODRIA REALIZAR...













