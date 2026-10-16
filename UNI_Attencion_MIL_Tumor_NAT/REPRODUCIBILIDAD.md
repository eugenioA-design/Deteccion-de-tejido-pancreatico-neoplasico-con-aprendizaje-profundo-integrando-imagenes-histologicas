# Notas de reproducibilidad

## Notebook original

UNI+AttentionMIL.ipynb conserva el código utilizado para la clasificación de tejido tumoral frente a tejido normal adyacente (NAT).

La partición se realizó por paciente, manteniendo todas sus WSI en un mismo subconjunto. Las predicciones y las métricas se calcularon por WSI.

## Imagen de referencia para Macenko

El archivo imgreferencia.png, incluido en esta carpeta, corresponde a la imagen de referencia utilizada para la normalización de color.

Para utilizarla, debe ajustarse la variable REFERENCE_PATCH del notebook a la ubicación local de este archivo.

## Extractor UNI

- Repositorio: MahmoodLab/UNI en Hugging Face.
- Arquitectura: vit_large_patch16_224.
- Dimensión de salida: 1024 elementos.
- Archivo de pesos verificado: pytorch_model.bin.
- Revisión verificada: b55a5ec6cade1a39edfe6534189a9b8ca7a022f0.

La revisión indicada se identificó durante la revisión de reproducibilidad. Se comprobó su concordancia numérica con embeddings previamente almacenados mediante la comparación de tres parches. No se registró la revisión de Hugging Face durante la extracción original.

El acceso a los pesos requiere cumplir las condiciones de acceso del repositorio de UNI. Los pesos no se distribuyen en este repositorio.

## Compatibilidad de software

El notebook original contiene el argumento dynamic_img_size=True en la creación de UNI.

Durante la revisión con timm 0.9.2, este argumento produjo un error de compatibilidad. Para comprobar los embeddings se creó la arquitectura vit_large_patch16_224 sin ese argumento y se cargaron los pesos de la revisión indicada.

Las comprobaciones de compatibilidad no implicaron volver a entrenar el modelo Attention MIL ni sustituir los resultados originales.

## Configuración y limitaciones

Las rutas de Windows incluidas en el notebook corresponden al equipo utilizado y deben adaptarse antes de ejecutar el código.

Los valores exactos de los ajustes de filtrado empleados al reprocesar las WSI C3N-01719-22 y C3N-02940-23 no se conservaron. Esto limita la reproducción exacta de la selección de parches en esos dos casos.

Los análisis adicionales de evaluación se documentan por separado del notebook original.
