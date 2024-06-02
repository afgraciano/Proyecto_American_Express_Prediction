

=======
# `Proyecto_American_Express_Prediction`

---------
## Miembros de grupo

  - Andres Felipe Graciano Monsalve CC71375739 Ingeniería de Sistemas 

  - Jose Carlos Ortiz Padilla CC 1003059949 Ingeniería de sistemas 

  - Sulay Gisela Martínez Barreto CC 1038137981 Ingeniería de sistemas


## Clonar en local este repositorio
-Se debe tener instalado git en el equipo local

-Se descarga en la pagina del repositorio desde code al lado derecho arriba, download zip. Si quiere clonarlo entonces copia el url en code y en git bash escribes git clone y la url y enter

# Fase 1
## Como usar
## Instrucciones:
Ejecuta el cuaderno llamado `01 - Análisis de datos, modelos e interacciones.ipynb` incluido en este repositorio donde esta explicado en cada linea del cuaderno lo que se esta ejecutando, empezando por la ejecucion de las librerias necesarias para el modelamiento, continuando con la extraccion y carga de los datos previamente extraidos del dataset de kaggle convertidos a formato txt para alivianar carga en colab (hay que logearse en la pagina de kaggle, luego suscribirse a la competicion en la parte inferior del "data description" debe darle click en "Subject to Competition Rules" para suscribirse a la competicion con el fin de poder acceder al archivo train_data.csv el cual trae todo el dataset al que se le va a aplicar el modelamiento, por ultimo se realiza un tratamiento de conversion al archivo del dataset para transformarlo a .txt para que este quede mas liviano y cargarlo mas facilmente en el servidor de google colab) y ejecutando todo el resto del cuaderno para obtener los resultados del modelo predictivo.

-------------

# Fase 2 
## instrucciones para docker
Debe entrar con el cmd a la carpeta donde esta descargado o clonado este repositorio y verifique que este el archivo dockerfile en dicha carpeta para realizar las ejecuciones siguientes:

docker build -t american . --> crear la imagen

docker run -p 3000:3000 -it --name american american --> hacer un docker con la iamgen creada y ver el cmd del docker en tiempo real

docker exec -it 489ec5ab41c /bin/bash --> entrar a los archivos del docker

docker ps ---> ver docker creados

docker images --> ver imagenes creadas

docker cp nombre_contenedor:ruta_del_archivo_dentro_del_contenedor directorio_destino_en_mi_computadora docker cp american:/app/data/prediction_file.csv "C:\Users\andres\Downloads\modelos\American Express-Entrenamiento-prediccion-Api"

python .\predict.py --input_file=data/test_data.csv --predictions_file=data/prediction_file.csv --model_file=modelo_final.pkl

---------
-------------
# Fase 3
## Instrucciones Api Rest con Docker

# API REST con Flask

Esta aplicación expone dos endpoints para el entrenamiento y predicción de un modelo de regresión logística.

## Instrucciones para Docker

### Crear la imagen

```sh
docker build -t american .
```

### Ejecutar un contenedor con la imagen creada

```sh
docker run -it -p 3000:3000 api
```

### Entrar al contenedor

```sh
docker exec -it [container_id] /bin/bash
```

### Ver contenedores creados

```sh
docker ps
```

### Ver imágenes creadas

```sh
docker images
```

## Enviar una solicitud de entrenamiento

### Para enviar una solicitud al endpoint `/train`, sigue estos pasos:

1. **Crear una nueva solicitud**:
    - Haz clic en el botón "New" y selecciona "Request".

2. **Configurar la solicitud**:
    - Asigna un nombre a la solicitud, por ejemplo, "Train Model".
    - Selecciona una colección o crea una nueva para guardar la solicitud.
    - Haz clic en "Save to [Collection Name]".

3. **Configurar los detalles de la solicitud**:
    - Método: Selecciona `POST`.
    - URL: Introduce la URL del endpoint `/train`. Si estás ejecutando Flask localmente en el puerto 3000, la URL será `http://127.0.0.1:3000/train`.

4. **Enviar la solicitud**:
    - Haz clic en "Send".

## Para enviar un archivo a la API REST que acabamos de crear utilizando Postman, sigue estos pasos:

### Enviar un archivo para predecir

1. **Abrir Postman**:
    - Inicia Postman en tu máquina.

2. **Crear una nueva solicitud**:
    - Haz clic en el botón "New" y selecciona "Request".

3. **Configurar la solicitud**:
    - Asigna un nombre a la solicitud, por ejemplo, "Predict File".
    - Selecciona una colección o crea una nueva para guardar la solicitud.
    - Haz clic en "Save to [Collection Name]".

4. **Configurar los detalles de la solicitud**:
    - Método: Selecciona `POST`.
    - URL: Introduce la URL del endpoint `/predict`. Si estás ejecutando Flask localmente en el puerto 3000, la URL será `http://127.0.0.1:3000/predict`.

5. **Añadir el archivo**:
    - Ve a la pestaña "Body".
    - Selecciona "form-data".
    - En la clave, escribe `file`.
    - En el valor, selecciona el tipo "File" desde el menú desplegable.
    - Haz clic en "Choose Files" y selecciona el archivo que deseas enviar.

6. **Enviar la solicitud**:
    - Haz clic en "Send".


-------------

## Enlace de la competencia de Kaggle https://www.kaggle.com/competitions/amex-default-prediction/data
En esta competencia se busca predecir la probabilidad de que un cliente no pague el saldo de su tarjeta de crédito en el futuro en función de su perfil de cliente mensual.

---------


