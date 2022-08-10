# Dataset-imbalanceados
Este repositorio es para almacenar algunas técnicas de balanceo de datos. Este repositorio será realizado en español.

Gran parte de la información puesta en este documento fue extraída de: 
https://www.analyticsvidhya.com/blog/2020/07/10-techniques-to-deal-with-class-imbalance-in-machine-learning/

Se hablará de una clasificación binaria, aunque su utilidad puede ser expandida a una clasificación mayor.

# Clasificación
En muchos problemas de clasificación una de las clases se encuentra en mayor proporción que la otra. Esto genera un problema para los modelos pues de una manera muy génerica lo que busca cada modelo independientemente de cual sea, busca identificar patrones en las variables creadas para determinar a que clase puede pertencer cada registro y debido a que la clase minoritaria cuenta con pocos detalles genera problemas para los modelos.
Es por esto que es necesario realizar métodos de balanceo de clases.

# Métricas.
Antes de continuar con el detalle de los métodos, se necesario tener presente que métrica me permiten identificar el mal funcionamiento de un modelo. 
El típico ejemplo de problemas de imbalanceo son el reconocimiento de transacciones fraudulentas, en este caso interesa identificar la clase minoritaria que según la literatura puede ser cerca del 6%. Si se realiza un modelo con este desbalanceo es muy posible que el ** accuracy **  arroje excelente resultados, sin embargo, estos resultados son sesgados y en algunas ocasiones pueden ser utilizados para vender modelos con un supuesto alto rendimiento.
En este caso, asumiendo que la clase positiva resulta ser una transacción  FRAUDULENTA la métrica que indica un buen rendimiento es recall que en palabras se puede traducir como: ¿ Cuántas de las transacciones fraudulentas es capaz de identificar?

# Métodos.
Existen dos métodos principales para realizar este balanceo: Oversampling y Undersampling. En resumen el primero se utliza cuando la data no es de gran tamaño y actúa sobre la clase minoritaria, un problema para este es el sobre entrenamiento del modelo. En cuánto al segundo método actúa sobre la clase mayoritaria en el cual se elige de manera aleatoria sin repetir n registros de manera que se balancen los datos, un problema de este es la pérdida en la capacidad de generalización del modelo y se utiliza principalmente cuando la data es abundante.

### Oversampling.
Este método actúa sobre la clase minoritaria. Algunos métodos son:
 - Random over-sampling with imblearn: Repite algunos registros sobre los que ya tiene de la clase minoritaria.
 - Synthetic Minority Oversampling Technique (SMOTE): Crea datos ficitios con un comportamiento similar a los demás de la clase minoritaria. Es decir con una estrategia como KNN crea nuevos registros entre los espacios de dos registro de la misma clase.
 -  Penalize Algorithms (Cost-Sensitive Training): Penaliza los algoritmos incrementando el costo de los erróres en la clasificación de la clase minoritaria. El argumento : class_weight=’balanced’

### Undersampling.
Este método actúa sobre la clase mayoritaria. Algunos métodos son:
 - Random under-sampling with imblearn: Este método seleciona n registros sin reemplazo de la clase mayoritaria de forma que el dataset quede balanaceado. Una forma de aumentar el performance de este modelo es agrupar en varios cluster los datos de la clase mayoritaria y seleccionar una propoción de cada grupo según la cantidad de registros que haya en cada grupo.
 - Under-sampling Tomek links: Quizás un método un poco diferente a los métodos clásicos. Utiliza los registros más próximos de las clases diferentes eliminando aquellos de  la clase mayoritaria.
 - NearMiss: SU funcionamiento es similar al Under-sampling Tomek links.
 





