# Predecir la rotación de clientes con Watson Machine Learning y Jupyter Notebooks en Cloud Pak for Data

En este patrón de código, utilizamos IBM Cloud Pak for Data para recorrer todo el proceso de ciencia de datos para resolver un problema comercial y predecir la rotación de clientes mediante un conjunto de datos de rotación de clientes de Telco. Cloud Pak for Data es un entorno interactivo, colaborativo y basado en la nube donde los científicos de datos, los desarrolladores y otras personas interesadas en la ciencia de datos pueden usar herramientas (por ejemplo, RStudio, Jupyter Notebooks, Spark, etc.) para colaborar, compartir y recopilar información. a partir de sus datos, así como crear e implementar modelos de aprendizaje automático y aprendizaje profundo.

Cuando el lector haya completado este patrón de código, comprenderá cómo:

* Utilice [Jupyter Notebooks](https://jupyter.org/) para cargar, visualizar y analizar datos
* Ejecute Notebooks en [IBM Cloud Pak for Data](https://www.ibm.com/analytics/cloud-pak-for-data)
* Cree, pruebe e implemente un modelo de aprendizaje automático con [Spark MLib](https://spark.apache.org/mllib/) en Cloud Pak for Data.
* Implementar un modelo de aprendizaje automático seleccionado en producción con Cloud Pak for Data
* Cree una aplicación front-end para interactuar con el cliente y comience a consumir su modelo implementado.

## Pre-requisitos
TO-DO: Checar enlaces y ver 
- Tener una cuenta de [IBM Cloud](https://cloud.ibm.com)
- Tener instalado [IBM Cloud Pak for Data as a Service](https://www.ibm.com/analytics/cloud-pak-for-data)

## Cupones para profesores y estudiantes:
- Acceder al portal de IBM Academic Initiative y seleccionar la opción "Register now" si aun no tienes cuenta.
- Realizar el registro correspondiente utilizando la cuenta de correo académica y confirma tu cuenta.
- Despues de confirmar tu cuenta, y con la sesion iniciada en IBM Academic Initiative, en la parte de "Most Popular Topics covered", encontraremos IBM Cloud y damos clic en "Learn more".
- Bajamos de la pagina hasta encontrar "Software". Le damos clic, nos dara un apartado que se llama "Request Feature Code".
- Nos dara nuestro codigo. Lo copiamos y lo llevamos a IBM Cloud.

## Cargar créditos en IBM Cloud:
- En la parte superior derecha, buscaremos la parte de "MANAGE"/"GESTIONAR", nos desplegara una lista y seleccionaremos "Account"/"Cuenta".
- De lado izquierdo, tendremos una opción "Account settings"/"Configuracion de cuenta".
- Bajamos un poco hasta encontrar "Subscription and feature codes"/"Codigos de suscripción y carateristicas".
- Da clic en "Apply code"/"Aplicar codigo".
- Ingresamos el codigo y clic en "Apply"/"Aplicar".

## Contenido 
1. [Crear una instancia de Object Storage](#1-Crear-una-instancia-object-storage)
2. [Crear una instancia de Machine Learning](#2-Crear-una-instancia-machine-learning)
3. [Crear una instancia de Watson Studio](#3-Crear-una-instancia-watson-studio)
4. [Crear un proyecto en watson studio](#4-Crear-proyecto-en-watson-studio)
5. [Agregar Notebook y CSV al proyecto](#5-Agregar-notebook-y-papeles-al-proyecto)
6. [Ejecutar el cuaderno](#6-Ejecutar-el-cuaderno)

### 1-Crear-una-instancia-object-storage
1. En el catálogo buscar "Object Storage" y seleccionarlo.
<p align="center">
  <img src='./img/1.png' alt="Object Storage" width="80%">
</p>
2. Crear el servicio. Seleccionar el plan gratuito "Lite". Dar scroll hacia abajo y elegir un nombre para el servicio. Dar click en "Crear".
<p align="center">
  <img src='./img/2.png' alt="Object Storage" width="80%">
  <img src='./img/3.png' alt="Object Storage" width="80%">
</p>

### 2-Crear-una-instancia-machine-learning
1. En el catálogo buscar "Machine Learning" y seleccionarlo.
<p align="center">
  <img src='./img/4.png' alt="Object Storage" width="80%">
</p>
2. Crear el servicio. Seleccionar el plan gratuito "Lite". Dar scroll hacia abajo y elegir un nombre para el servicio. Dar click en "Crear".
<p align="center">
  <img src='./img/5.png' alt="Object Storage" width="80%">
  <img src='./img/6.png' alt="Object Storage" width="80%">
</p>

### 3-Crear-una-instancia-watson-studio
1. En el catálogo buscar "Watson Studio" y seleccionarlo.
<p align="center">
  <img src='./img/7.png' alt="Object Storage" width="80%">
</p>
2. Crear el servicio. Seleccionar el plan gratuito "Lite". Dar scroll hacia abajo y elegir un nombre para el servicio. Dar click en "Crear".
<p align="center">
  <img src='./img/8.png' alt="Object Storage" width="80%">
  <img src='./img/9.png' alt="Object Storage" width="80%">
</p>

### 4-Crear-proyecto-en-watson-studio
1. Una vez creada la instancia, se abrirá el servicio creado. Dar click en "Iniciación"
<p align="center">
  <img src='./img/10.png' alt="Object Storage" width="80%">
</p>
2. Se abrirá una nueva pestaña. Dar click en "Crear proyecto".
<p align="center">
  <img src='./img/11.png' alt="Object Storage" width="80%">
</p>
3. Seleccionar "Crear un proyecto vacío".
<p align="center">
  <img src='./img/12.png' alt="Object Storage" width="80%">
</p>
4. Elegir el nombre del proyecto. En almacenamiento debe aparecer el nombre de la instancia que se creo de Object Storage (si es la única que se tiene en la cuenta), si no aparece, elegirla. Dar click en "Crear" 
<p align="center">
  <img src='./img/13.png' alt="Object Storage" width="80%">
</p>

### 5-Agregar-notebook-y-papeles-al-proyecto
1. En el proyecto abierto, dar click en "Añadir al proyecto" para agregar el notebook. Se abre un modal y dar click en "Notebook".
<p align="center">
  <img src='./img/14.png' alt="Object Storage" width="80%">
</p>
<p align="center">
  <img src='./img/15.png' alt="Object Storage" width="80%">
</p>            

2. Se abre la ventana de Nuevo Notebook. Seleccionar el tab "Desde URL". Elegir un nombre para el notebook e insertar la URL del notebook que esta en ese repositorio. Dar click en "Crear"
<p align="center">
  <img src='./img/16.png' alt="Object Storage" width="80%">
</p>
3. Automáticamente se abrirá el notebook pero se debe agregar otro archivo es por eso que hay que dar click derecho en "prediction-workshop" y seleccionar "Abrir nueva pestaña" para abrir otra tab y agregar un csv.
<p align="center">
  <img src='./img/17.png' alt="Object Storage" width="80%">
</p>
4. En la nueva pestaña del navegador. Dar click en "Activos"(1). Dar click en el botón del lado derecho de circulitos(2). Subir el csv "Telco-Customer-Churn.csv" que se podrá descargar desde este mismo repositorio en la carpeta "Data"(3).
<p align="center">
  <img src='./img/18.png' alt="Object Storage" width="80%">
</p>
5. Verificar que se ha cargado correctamente el archivo. Debe aparecer en la tabla de "Activos de Datos". 
<p align="center">
  <img src='./img/19.png' alt="Object Storage" width="80%">
</p>
6. En la misma ventana del proyecto dar scroll hacia abajo para llegar a la sección "Señales de Acceso". Dar click en "Nueva señal"(1). Se abrirá un modal. Asignar un nombre a la señar y elegir el rol de "Editor". Dar click en "Crear".
<p align="center">
  <img src='./img/20.png' alt="Object Storage" width="80%">
</p>
7. En la misma ventana ir a la tabla de "Notebooks". En la fila del notebook que agregamos dar click en el candado. Aparecerá un modal. Dar click en "Desbloquear".
<p align="center">
  <img src='./img/21.png' alt="Object Storage" width="80%">
</p>

### 6-Ejecutar-el-cuaderno

