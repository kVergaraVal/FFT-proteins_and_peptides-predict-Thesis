# Tesis FFT proteins and peptides predict

Esta tesis tiene como objetivo la validación del uso de la digitalización de las propiedades fisicoquímicas (transformada rápida de Fourier) de las secuencias los péptidos y proteínas para poder implementar modelos predictivos en problemas de regresión y clasificación, de manera generalizada.

## Conjuntos de datos

Se emplearon 19 conjuntos de datos en este trabajo, los cuales están disponibles en la carpeta [Datasets CSV](https://github.com/kVergaraVal/FFT-proteins_and_peptides-predict-Thesis/tree/main/Datasets%20CSV) y documentados en el excel [Datasets_characterization.xlsx](https://github.com/kVergaraVal/FFT-proteins_and_peptides-predict-Thesis/blob/main/Datasets_caracterization.xlsx?raw=true). En particular, se tomaron 5 casos de estudio para un análisis y discusión más profunda:
* Enantioselectivity
* T50
* VaxinPad
* DBP
* iAMP-2L_multiclass

## Caracterización de las secuencias aminoacídicas y de las respuestas

Para poder visualizar preliminarmente los datos y poder estandarizarlos/normalizarlos, eliminar outliers, efectuar oversampling/undersampling e indagar en los posibles sesgos, se procesaron y transformaron. Se exploraron 4 formas distintas de codificación de la información bioquímica/secuencial para poder contrastarlos con la digitalización:
* Onehot encoder
* Ordinal encoder
* Amino Acid Composition (AAC)
* Dipeptide Composition.

El código que transforma los datos en distintas formas de codificación está en el archivo encodings_process.ipynb. El código que visualiza los datos corresponde al archivo Characterization.ipynb. Las carpetas asociadas son [Encodings](https://github.com/kVergaraVal/FFT-proteins_and_peptides-predict-Thesis/tree/main/Encodings) y [Data Visualization - Sequence and Response](https://github.com/kVergaraVal/FFT-proteins_and_peptides-predict-Thesis/tree/main/Data%20Visualization%20-%20Sequence%20and%20Response), respectivamente.

## Alineamiento de secuencias

Además de comparar con distintas formas de codificación, se decidió contrastar con un método completamente diferente y puramente biológico: alineamiento múltiple. Aquí, se utilizó el software bioinformático MEGA, con el objetivo final de obtener las matrices de distancias de cada conjunto. Para ello, se requirió tener las secuencias en formato .fasta. Los archivos e imágenes de esta etapa se encuentran en la carpeta "Alineamiento"

## Caracterización de los Espectros de Fourier

La forma de codificación central del presente trabajo es la digitalización de propiedades fisicoquímicas. Es decir, la transformación del perfil fisicoquímico de las secuencias aminoacídicas en el dominio temporal (posición de residuo) a espectros de Fourier en dominio de frecuencias. Para ello, es necesario determinar qué propiedades fisicoquímicas de las 565 existentes se evaluarán. A base de un trabajo del Centro de Biotecnología y Bioingeniería (CeBiB), se redujo la selección a 8 propiedades:
* PRAM900102
* PRAM900103
* COSI940101
* HOPT810101
* JOND750101
* GRAR740103
* RADA880106

El archivo que detalla las 565 propiedades y la codificación de cada uno de los 20 aminoácidos es AAindex.csv. La codificación de los conjuntos en cada uno de las propiedades se encuentra en la carpeta "Encodings" y fue realizado por el código encodings_process.ipynb.

Posteriormente, se visualizaron los espectros para poder interpretar fenomenológicamente algunas características de los conjuntos. Esto se muestra en la carpeta "Data - Visualization - Spectrums". El código que genera las imágenes es Characterization.ipynb.

## Construcción e Implementación de los modelos

Se trabajaron con los siguientes algoritmos de aprendizaje supervisado, tanto para los problemas de regresión como los de clasificación:
* Support Vector Machine
* K-Nearest Neighbor
* Random Forest
* Neural Network
* Convolutional Neural Network

Se exploró los mejores desempeños logrados para cada conjunto de dato, determinando:
* Mejor forma de codificación
* Mejor algoritmo
* Propiedad Fisicoquímica más informativa

El código que logra esto es Models.ipynb.

## Indicadores de desempeño

Finalmente, se grafican las matrices de confusión y ROC para los problemas de clasificación (los de regresión están detallados en el informe de tesis). Esto se encuentra en la carpeta "Evaluation Metrics".

## Más información

Para el informe, consultar en Informe.pdf.
Para ver la presentación de la defensa de tesis, consultar en Presentación.pdf
