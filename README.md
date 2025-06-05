# Parcial-III-IA

*Cuestionario Evaluativo: Redes Neuronales e IA Aplicada*

Pregunta 1 - Fundamentos de CNN
Explique qué son las redes neuronales convolucionales (CNN) y por qué son especialmente efectivas para el reconocimiento de imágenes. Mencione al menos tres características distintivas de las CNN que las hacen superiores a las redes neuronales tradicionales para tareas de visión por computadora.

*R//*
Las redes neuronales convolucionales son modelos de deep learning diseñados para procesar las imagenes. Son buenas y eficaces ya que pueden detectar de manera automatica los patrones visuales como lo son: Bordes, formas y texturas.

Las caracteristicas principales a las de las redes tradicionales son:

*1. Capas de convolución* Estas tienen como objetivo extraer caracteristicas relevantes directamente de la imagen.
*2. Compartición de pesos* Reduce el numero de los parámetros y esto ayuda a que sea más eficaz
*3. Pooling* Ayuda a simplificar la información reduciendo el tamayo sin afectar nada importante.


Esto da ventajas al modelo CNN para reconocer imagenes con alta precision y eficacia.


Pregunta 2 - Arquitectura y Componentes

Describa las capas principales que componen una CNN típica (Conv2D, MaxPooling2D, Flatten, Dense) y explique la función específica de cada una en el proceso de reconocimiento de imágenes. ¿Por qué es importante el orden de estas capas?

*R//*

Las CNN tipicas incluyen varias capas, la cual cada una tiene un rol especifico:

*1. Conv2D* Este aplica filtros sobre la imagen, para reconocer caracteristicas como los son los bordes o texturas de la imagen.
*2. MaxPooling2D* Como anteriormente se mencionaba esto reduce la imagen manteniendo la información sin alterar, lo que esto ayuda a tener una mejor eficacia y evita un sobre ajuste.
*3. Flatten: Ayuda con la formulación y convierte los datos en un vector plano para que sea más eficiente conectarlos con las capas finales.
*4. Dense:* Son un conjunto de capas conectadas que ayuda con el procesamiento de las caracteristicas extraidas y generan la salida, como una clasificación.

Esto sobresalta el orden y su importancia por que en cada capa prepara los datos para la siguiente. Si alguna de estas se encuentra alterada, el modelo no podría aprender correctamente ni hacer buenas predicciones.


*Pregunta 3 - Preprocesamiento de Datos

En el contexto del dataset CIFAR-10:
a) ¿Por qué es necesario normalizar los valores de píxeles al rango [0, 1]? (4 puntos) 

*R//*

Es primordial normalizar los valores de los pixeles en los rangos (0,1) esto facilita y ayuda a que el modelo se entrene de manera eficiente. Los valores de los pixeles originales (0 A 255) pueden causar problemas a nivel de la escala en el entrenamiento. Ya que las redes neuronales tienden a converger más rápido, cuando los valores de entrada están en un rango pequeño.

b) ¿Qué significa convertir las etiquetas a formato "one-hot" y por qué es necesario? (4 puntos)

*R//* Esto ayuda a convertir etiquetas a formato "One-hot" lo que representa cada clase como un vector con 1 en la posición correspondiente a la clase y 0 a las demas. 

Por ejemplo, para 10 clases, la etiqueta "3" se convierte en [0, 0, 0, 1, 0, 0, 0, 0, 0, 0]. 

Las redes requieren que las etiquetas estén en un formato numerico y binario, lo que ayuda con la comparación entre la predicción del modelo y la etiqueta verdadera durante el entrenamiento.

c) Mencione dos técnicas de data augmentation que podrían mejorar el rendimiento del modelo y explique cómo funcionan. (4 puntos)

*R//*

*1. Rotación de imagenes* Consta de girar la imagen por un cierto ángulo. Esto ayuda a que el modelo reconozca objetos independientemente de la orientación, evolucionando la capacidad de generalización.

*2. Desplazamiento (Translation)* Cosnta en realizar una serie de movimientos a las imagenes ligeramente en cualquier dirección. Lo cual ayuda al modelo tenga una compostura robuta y no dependa de la posición exacta de los objetos que hay dentro de la imagen.

Pregunta 4 - Optimización y Entrenamiento

Analice los siguientes aspectos del entrenamiento de una CNN:

¿Qué función de pérdida se utiliza para clasificación multiclase y por qué?

*R//*

Para esta funcción y clasificación multiclase "categorical cross-entropy" Es una de las cuales mide la diferencia entre las probabilidades predichas por el modelo y las que cuentan con etiquetas reales. Esto es primordial para tareas de clasificación multiclase por que sanciona la manera más efectiva de las predicciones incorrectas. Priorizando en ayudar a que el modelo aprenda a predecir la clase correcta con mayor precisión.

¿Cuál es la diferencia entre usar 'adam' y 'sgd' como optimizadores?

*R//*

Una de las diferencias principales entre Adam y SGD es que el primero, adam es un optimizador adaptativo. Adam ajusta automaticamente las tasas de aprendizaje para cada parámetro durante el entrenamiento, lo que ayuda a que sea mas eficiente y rápido, especificamente en problemas complejos. Lo contrario a SGD. Este utiliza una tasa de aprendizaje fija y actualiza los parametros en función de una muestra al azar del conjunto de datos, lo cual requiere más tiempo para encontrar el minimo global.

¿Cómo se puede detectar y prevenir el overfitting durante el entrenamiento?

*R//*

Esto ocurre cuando el modelo es ajustado demasiado a los datos de entrenamiento, perdiendo la capacidad para generalizar a nuevos datos. Esto ayuda a detectarlo, se puede observar una diferencia entre los rendimientos en el conjunto de entrenamientos, que tiene un conjunto de validación para prevenir esto se puede usar las siguientes estrategias:


*Regularización (L2, Dropout):*Añadir penalizaciones al modelo para evitar que se ajuste demasiado a los datos de entrenamiento.

*Aumento de datos (data augmentation):* Generar variaciones de los datos de entrenamiento para hacer el modelo más robusto.

*Early stopping:* Detener el entrenamiento cuando el rendimiento en el conjunto de validación comienza a disminuir, evitando que el modelo siga aprendiendo patrones irrelevantes.


Pregunta 5 - Transfer Learning
El taller menciona el uso de MobileNetV2 pre-entrenado. Explique:

¿Qué es transfer learning y cuáles son sus ventajas?

*R//*

Es una técnica donde un modelo previamente entrenado en un gran conjunto de datos se adapta para resolver un problema diferente pero relacionado. Sus ventajas incluyen un entrenamiento más rápido y una mejor generalización, ya que el modelo ya ha aprendido características útiles de un conjunto de datos grande, como ImageNet, que se pueden transferir a una tarea específica con menos datos.

¿Por qué se eligió MobileNetV2 para este proyecto específico?

Porque es un modelo eficiente y ligero, diseñado específicamente para dispositivos móviles. Tiene un buen rendimiento en tareas de visión por computadora, manteniendo un bajo costo computacional, lo que lo hace ideal para aplicaciones con restricciones de hardware.


¿En qué situaciones sería preferible entrenar un modelo desde cero versus usar transfer learning?

Cuando se dispone de un gran conjunto de datos específico para la tarea y se necesita un modelo completamente adaptado. En cambio, transfer learning es más útil cuando los datos disponibles son limitados o cuando se requiere un modelo rápido y eficiente, como en aplicaciones móviles o con pocos recursos.


Pregunta 6 - Procesamiento de Lenguaje Natural


a) Explique qué es la lemmatización y por qué es importante en el procesamiento de texto.

*R//*

La lemmatización es el proceso de reducir las palabras a su forma base o lema, eliminando variaciones gramaticales. Por ejemplo, "corriendo" se convierte en "correr". Es importante porque ayuda a que el modelo entienda que diferentes formas de una palabra tienen el mismo significado, lo que mejora la precisión del análisis semántico y facilita la comprensión del texto.

b) ¿Cómo funcionan los patrones de conversación definidos en el código para identificar intenciones del usuario?

*R//* 

Los patrones de conversación son reglas predefinidas que analizan las entradas del usuario para identificar ciertas palabras clave o frases. Estas se asignan a intenciones específicas (como una consulta o una solicitud) y el sistema responde de manera apropiada. Utilizan técnicas de coincidencia exacta o aproximada para reconocer las intenciones según las entradas dadas.

c) Mencione tres técnicas que podrían mejorar la capacidad de comprensión del chatbot.

*R//*

*Modelos de embeddings (Word2Vec, GloVe):* Representan palabras en vectores densos, capturando relaciones semánticas y mejorando la comprensión del contexto.

*Redes neuronales recurrentes (RNN):* Permiten al chatbot recordar el contexto de la conversación a lo largo de múltiples interacciones.

*Análisis de sentimientos:* Ayuda al chatbot a detectar emociones del usuario y responder de manera más empática.


Pregunta 7 - Integración de Sistemas

*R//*

¿Cuáles son los principales desafíos técnicos de esta integración?
Los principales desafíos incluyen la sincronización entre los módulos de visión y NLP, ya que ambos sistemas procesan información diferente (imágenes y texto). Además, se debe gestionar el flujo de datos para asegurar que la información de la imagen se integre correctamente con el contexto de la conversación.

¿Cómo se mantiene el contexto entre el análisis de imágenes y la conversación?
El contexto se puede mantener mediante el uso de memorias de contexto que vinculen las imágenes procesadas con las intenciones del usuario. Se puede almacenar la información relevante de la imagen y combinarla con las respuestas previas del chatbot para garantizar una interacción fluida y coherente.

Proponga una mejora específica para hacer más fluida esta integración.
Una mejora sería implementar un módulo de atención, que permita al sistema identificar y priorizar la información más relevante tanto en las imágenes como en las conversaciones, facilitando una integración más natural y eficiente de ambos componentes.

Pregunta 8 (8 puntos) - Análisis de Rendimiento

a) ¿Qué información proporciona una matriz de confusión?

*R//*

Una matriz de confusión muestra las predicciones del modelo comparadas con las etiquetas reales. Proporciona información sobre los verdaderos positivos, falsos positivos, verdaderos negativos y falsos negativos, lo que permite evaluar el rendimiento del modelo, especialmente en clasificación multiclase.

b) ¿Cuál es la diferencia entre accuracy, precision y recall? ¿Cuándo es más importante cada métrica?

*R//*

Accuracy: mide la proporción de predicciones correctas sobre el total de predicciones. Es útil cuando las clases están balanceadas.

Precision: indica cuántas de las predicciones positivas son correctas. Es crucial cuando las falsos positivos tienen un alto costo (por ejemplo, en diagnósticos médicos).

Recall: mide cuántos de los casos positivos reales fueron correctamente identificados. Es importante cuando se necesita identificar la mayor cantidad posible de casos positivos, como en la detección de fraude.

Pregunta 9 - Casos de Uso Específicos

*R//*

¿Qué consideraciones éticas y de privacidad se deben tener en cuenta?
Es crucial garantizar la privacidad de los usuarios, especialmente al manejar datos sensibles como información académica o psicológica. Se deben implementar medidas de seguridad como cifrado de datos y cumplir con regulaciones como el RGPD. También, el sistema debe ser transparente respecto al uso de los datos.

¿Cómo se podría adaptar el sistema para detectar situaciones que requieran intervención humana?
El sistema podría ser entrenado para detectar señales de alerta, como respuestas que indiquen angustia o riesgo. Si se identifica una situación crítica, el sistema puede notificar a un profesional para que intervenga de manera adecuada.

Proponga una funcionalidad adicional que agregue valor al sistema.
Una funcionalidad adicional sería la capacidad de análisis emocional, que permita al sistema detectar emociones en las respuestas del usuario y adaptar sus respuestas en consecuencia, proporcionando una interacción más personalizada y empática.

Pregunta 10 - Visión Futura

*R//*

¿Cuál de las extensiones mencionadas considera más importante implementar primero y por qué?
La integración de modelos de lenguaje avanzados como GPT o BERT sería la más importante, ya que mejoraría la capacidad del sistema para comprender el contexto y generar respuestas más naturales, mejorando la experiencia del usuario.

¿Cómo impactarían los avances en modelos de lenguaje como GPT o BERT en este tipo de sistemas?
Los avances en modelos como GPT o BERT permitirían una comprensión más profunda del lenguaje natural, mejorando la precisión en la interpretación de las intenciones del usuario, así como la fluidez y coherencia de las respuestas generadas, lo que haría a los sistemas más efectivos y adaptativos en diversas situaciones.



