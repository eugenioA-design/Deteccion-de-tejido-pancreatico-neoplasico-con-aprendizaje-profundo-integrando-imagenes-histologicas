# Detección de tejido pancreático neoplásico con aprendizaje profundo integrando imágenes histológicas y perfiles moleculares
Trabjo de Maestria
Eugenio Andrade

#Este repositorio contiene el código fuente desarrollado para la tesis de maestría, centrada en el desarrollo de un modelo de aprendizaje profundo multimodal débilmente supervisado para la detección del adenocarcinoma ductal pancreático (PDAC) y su caracterización molecular mediante la integración de imágenes WSI y datos transcriptómicos.

#Primer apartado: Modelo basado en UNI + Attention MIL para la identificación de adenocarcinoma pancreático ductal
  -Preprocesamiento de imágenes WSI
  -Segmentación de tejidos
  -Extracción de parches
  -Normalización de parches
  -Extracción de características mediante el modelo UNI
  -Aprendizaje de instancias múltiples basado en atención (Attention MIL)
  -Visualización de parches representativos

#Segundo apartado: Modelo basado en Graph Attention Network (GAT) para la clasificación de los subtipos moleculares Basal-like y Classical de los pacientes con PDAC.
  -Preprocesamiento transcriptómico
  -Construcción de firmas moleculares
  -Etiquetado y calculo de puereza molecular
  -Extracción de caracteristicas con UNI
  -Construcción de grafos espaciales
  -Modelo GAT ponderado por pureza molecular
  -Visualización de parches representativos y mapas de atención

#Fuentes de datos (publicas)
Imágenes histológicas 
Colección de adenocarcinomas pancreáticos ductales del TCIA CPTAC (https://www.cancerimagingarchive.net/collection/cptac-pda/)

Datos transcriptómicos
Consorcio de análisis proteómico clínico de tumores (CPTAC) (https://portal.gdc.cancer.gov/projects/CPTAC-3)

#Requerimientos del sistema 
Se recomienda minimo un almacenamieto de 1TB para replicar el proyecto. Una GPU con NVIDIA CUDA dismonible.
Las bases de datos, extraccion de parches, generacion de embeddings, estructuras de grafos y resultados intermedios requieren de una capacidad sustancial de almacenamiento.

#Complementos utilizados
Este framework se sesarrollo con:
-Python
-Jupyter Notebook
-PyTorch
-Torch Geometric
-timm
-OpenSlide
-NumPy
-Pandas
-Scikit-learn
-Scikit-image
-Pillow
-Matplotlib

#Aviso
Antes de ejecutar los notebooks o scripts, los usuarios deben modificar las rutas de todos los directorios locales según la organización de su sistema de archivos.
El proyecto original se desarrolló utilizando estructuras de directorios locales que difieren de las de otros usuarios.

#Para reproducir

  1. Descargar los conjuntos de datos originales de los repositorios oficiales
  2. Organizar los archivos según la estructura de directorios esperada
  3. Actualizar todas las rutas de entrada y salida en los cuadernos
  4. Instalar los paquetes de Python necesarios
  5. Ejecutar los cuadernos secuencialmente
