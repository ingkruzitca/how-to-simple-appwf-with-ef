# Cómo crear un CRUD básico sobre una app Window Form integrando Entity Framework

Seguir los pasos en este orden: 

## Crear el proyecto
Como uno de Windows Form pero NO de .NET Framework, sino como de .NET solamente. 
![[Pasted image 20251001153609.png]]


Instalar 
![[Pasted image 20251001130650.png]]

![[Pasted image 20251001130730.png]]

![[Pasted image 20251001130822.png]]


Otra forma en la "Consola de Administrador de paquetes"
![[Pasted image 20251001131124.png]]

Pegar y correr los siguientes comandos en la terminal:
>install-package EntityFramework
>install-package Microsoft.EntityFrameworkCore.SqlServer
>install-Package Microsoft.EntityFrameworkCore.Tools

Ojo: comando a considerar;
La fuente de datos: nuestro servidor o ver en el SSMS
Catalogo inicial: nuestra base de datos que nos conectaremos
Seguridad integrada: si nos logueamos con Autenticación de Windows
Encrypt: No va encriptada la conexión.
Luego la herramienta con la cual crearemos nuestro contexto.
Y finalmente la carpeta DAE donde enviaremos toda la salida.

Scaffold-DbContext "Data Source=localhost\SQLEXPRESS;Initial Catalog=dae;Integrated Security=True;Encrypt=False" Microsoft.EntityFrameworkCore.SqlServer -OutputDir DAE

Nota: DAE es el nombre de la carpeta creada dentro del proyecto para que ahi sea el destino de los archivos que se crearán.


Se crea las entidades o clases de las tablas en nuestra BD:
![[Pasted image 20251001155124.png]]

Y el DaeContext.cs
![[Pasted image 20251001155205.png]]
Ahí tenemos la cadena de conexión donde podemos modificar según sea nuestro caso, o si cambiamos de servidor la BD.

En el código del Form agregamos  la carpeta DAE para poder hacer referencia a ella, primera línea:
![[Pasted image 20251001155323.png]]

Luego, dentro de la class Form1:Form, instanciamos a la clase DaeContext():

```C#
DaeContext context = new DaeContext();
```

![[Pasted image 20251002220131.png]]

Creamos una nueva función cargarTabla();
para cargar con los datos del context el dataGridView

![[Pasted image 20251002220440.png]]

Al evento click del botón Agregar le adicionamos el código siguiente:
![[Pasted image 20251002220759.png]]

Al evento click del DataGridView:
![[Pasted image 20251002222001.png]]

Agregamos el siguiente código, para que al dar click a una tupla o row de la tabla se cargue la info en los textBox:

![[Pasted image 20251002221856.png]]

Modificar algunas propiedades del dataGridView:
![[Pasted image 20251002222526.png]]

![[Pasted image 20251002222615.png]]

![[Pasted image 20251002222730.png]]

![[Pasted image 20251002222802.png]]





Agregamos el botón Eliminar, y al evento Click el siguiente código:
![[Pasted image 20251002221722.png]]

Agregamos el botón Modificar, y al evento click el siguiente código:
![[Pasted image 20251002225051.png]]


Listo, continuar mejorando la vista, aplicar una búsqueda al grid...











