# Notas de reproducibilidad de UNI + GAT

## Modelo final

El notebook UNI+GAT.ipynb contiene la construcción de la firma transcriptómica, la extracción de embeddings UNI, la construcción de grafos espaciales y el entrenamiento de la GAT.

Se utilizó una WSI tumoral por paciente. La cohorte comprendió 140 pacientes, distribuidos en 98 para entrenamiento, 21 para validación y 21 para prueba.

## Sección 3.1 y filtrado exploratorio

La sección 3.1 calcula el índice de separación molecular como la diferencia absoluta entre los puntajes Basal-like y Classical.

También conserva marcas de un filtrado exploratorio mediante la columna use_for_training. El script 5 del modelo final no utiliza esa columna para excluir pacientes y conserva los 98 pacientes de entrenamiento.

Los nombres de archivo y variables que contienen purity corresponden a la denominación utilizada originalmente en el código. El índice representa separación entre firmas transcriptómicas, no proporción de células tumorales.

## Ponderación de la pérdida

El índice se normaliza utilizando exclusivamente el mínimo y el máximo del conjunto de entrenamiento, limitando el resultado al intervalo [0, 1].

El peso de muestra se calcula como:

sample_weight = 0.5 + 0.5 * indice_normalizado

En validación y prueba, el peso de muestra se fija en 1.

Los perfiles transcriptómicos proporcionan las etiquetas de referencia y los pesos de entrenamiento. La predicción utiliza embeddings histológicos UNI y conexiones espaciales, sin incorporar los perfiles transcriptómicos como vectores de entrada.

## Selección del modelo

El checkpoint se selecciona mediante la mayor Balanced Accuracy de validación, con parada temprana tras 15 épocas consecutivas sin mejora.

## Extracción con UNI

La revisión de pesos verificada y las observaciones de compatibilidad se documentan en:

[Notas de UNI y Macenko](../UNI_Attencion_MIL_Tumor_NAT/REPRODUCIBILIDAD.md)

Las rutas locales deben adaptarse antes de ejecutar el notebook.
