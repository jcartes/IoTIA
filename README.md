# IoTIA
Inteligencia Artificial, aprendiendo de pensamientos.

Tras varios meses de muuuucha lectura, mucho estudio, investigación y algo de práctica, doy inicio a este proyecto como idea (Quizás vaya madurando y generando una magnífica comunidad :) )
La gente que estudia medicina me ha comentado, que lo mas dificil de comprender en su mayoría de ámbitos es el Cerebro Humano (Por varios motivos que los iremos revelando) Donde me pondré a
práctica sensorizando mi cabeza (Nada de androides y esas cosas). Simplemente quiero decodificar las ondas cerebrales al borde, con el propósito de crear una interfaz Brain-Computing, utilizando
dispositivos de bajo costo (GPU's, Sensores Electrodos, Convertidor analógico a digital de bajo ruido, 8 canales y 24 bits para mediciones de biopotencial ------> en términos simples: Electroencefalografía).

![Alt text](https://hackster.imgix.net/uploads/attachments/1064985/_5jBZzuJXWT.blob?auto=compress%2Cformat&w=900&h=675&fit=min "IoTIA")

# Cosas a usar en este proyecto:
Componentes de hardware
- Kit de desarrollador de NVIDIA Jetson Nano ×	1
- Dispositivo EEG Open Source OpenBCI V3, 8 o 16 canales ×	1
- TPLINK TLWN823N Wifi stick ×	1
- Resistencia 10k ohm ×	2
- Resistencia de 330 ohmios	×	2
- Transistor de propósito general NPN 2N2222 ×	2
- Protoboard (genérico) ×	1
- Cables de puente macho / hembra ×	1

Aplicaciones de software y servicios en línea.
- Imagen NVIDIA Jetson Nano
- Python 3
- Jupyter Notebook
- Docker
- IBM Watson


# Historia

# __¿Qué?__
Este proyecto ayudará a guiarnos en la creación de un dispositivo impulsado por inteligencia artificial que le permita interactuar directamente su cerebro con sus propios proyectos de hardware y software. Sí, ¡una verdadera interfaz Brain-Computing impulsada por IA!
En el camino, aprenderemos un poco sobre electrofisiología cerebral; [oscilaciones neurales](https://en.wikipedia.org/wiki/Neural_oscillation) ; procesamiento de señal, interfaz con [dispositivos USB de bajo nivel](https://libusb.info/) ; enhebrar con Python; construyendo redes neuronales con [PyTorch](https://pytorch.org/) ; haciendo GUI increíbles en Python con OpenGL usando [Pyglet](http://pyglet.org/) , y por supuesto técnicas increíbles en [aprendizaje no supervisado](https://en.wikipedia.org/wiki/Unsupervised_learning) , [agrupamiento](https://en.wikipedia.org/wiki/Cluster_analysis) y [detección de anomalías](https://en.wikipedia.org/wiki/Anomaly_detection) usando inteligencia artificial.
No solo vamos a reutilizar una arquitectura de visión por computadora (no es que haya nada de malo en eso), sino que también construiremos una red neuronal desde cero, para que pueda aprender cómo funcionan desde el Molido.

# __¿Por qué?__
El aprendizaje profundo está revolucionando muchos campos de la ciencia y la tecnología. Al utilizar el aprendizaje automático, podemos predecir y clasificar los procesos naturales sin construir modelos explícitos, ¡algo vital cuando los datos son difíciles de interpretar!
El objeto más complejo en el universo conocido es algo que todos llevamos con nosotros todos los días, no, no nuestros teléfonos inteligentes, es nuestro cerebro. Pero entender lo que está sucediendo allí es difícil, ya que nuestras reflexiones subjetivas no pueden describir lo que sucede dentro de nuestros propios cráneos.
Aquí hay tecnologías no intrusivas que podemos usar (porque quién realmente quiere perforar agujeros en sus cráneos antes de que se complete el [Neuralink de Elon Musk](https://en.wikipedia.org/wiki/Neuralink), como [MRI](https://en.wikipedia.org/wiki/Magnetic_resonance_imaging), [EEG](https://en.wikipedia.org/wiki/Electroencephalography) y [FNIR](https://en.wikipedia.org/wiki/Functional_near-infrared_spectroscopy). Pero de estos, personas que participen en comunidades OpenSource de IoT pueden acceder a EEG, a través de productos como [NeuroSky](https://store.neurosky.com/) MindWave o Star Wars [Force Trainer](https://en.wikipedia.org/wiki/Force_Trainer). Pero el poder de procesamiento de tales dispositivos es tan bajo, que tienen que conectarse a una PC o solo pueden extraer frecuencias de ondas cerebrales únicas, e ignorar la gran mayoría de las señales complejas que genera el cerebro.
Con el poder del [Jetson Nano](https://developer.nvidia.com/embedded/jetson-nano-developer-kit) , finalmente podemos hacer un análisis profundo y complejo de los datos de EEG, directamente en un dispositivo portátil conectado a Internet. Este proyecto nos llevará a la vanguardia de lo que actualmente es posible en el análisis EEG.

# __¿Cómo?__
__Electrofisiologia__

Los cerebros funcionan con señales eléctricas, pero no de la misma manera que funcionan nuestros dispositivos electrónicos. Hay muchas más cosas en el cerebro que la señalización eléctrica, pero concentrémonos en ese aspecto. El cerebro humano contiene 86 mil millones de neuronas, y cada una de esas neuronas recibe información de varias otras neuronas en una red.

![Alt text](https://hackster.imgix.net/uploads/attachments/1066867/image_YbSseeZIXn.png?auto=compress%2Cformat&w=740&h=555&fit=max "IoTIA")

_El progreso de un potencial de acción_


Cada neurona actúa como un procesador de señal en estas entradas; cuando una neurona ha recibido suficientes entradas dentro de un cierto marco de tiempo, 'dispara' un pulso eléctrico a las neuronas más abajo de la red. Esta es una respuesta de todo o nada: las neuronas posteriores solo saben que una neurona ha disparado, no obtienen ninguna otra información. El potencial de acción también es bastante rápido; el pulso de voltaje pico termina en aproximadamente un milisegundo.

![Alt text](https://hackster.imgix.net/uploads/attachments/1066862/image_Z4LYpjLvjB.png?auto=compress%2Cformat&w=740&h=555&fit=max "IoTIA")

_El camino del potencial de acción en una neurona_


# __Ondas cerebrales__
El cerebro no tiene un 'núcleo' centralizado como la CPU de una computadora. Las neuronas del cerebro operan en paralelo, lo que le da un gran cálculo y ancho de banda. Pero cada neurona necesita procesar la señal en múltiples entradas simultáneamente, por lo que sería mejor coordinar las entradas. El cerebro organiza esto operando en ciclos, con todas las neuronas disparando en ráfagas para mantener la sincronización (si es necesario que disparen).

![Alt text](https://hackster.imgix.net/uploads/attachments/1066871/image_YRoLqCd56u.png?auto=compress%2Cformat&w=740&h=555&fit=max "IoTIA")

_Potenciales de acción en ondas cerebrales_

No podemos detectar estos potenciales de acción rápidos y diminutos a través del cráneo, la carne y la piel, pero en conjunto, podemos medir el potencial de campo local que refleja su actividad sumada. Por supuesto, los campos están humedecidos y manchados por toda la carne y el hueso entre nuestros electrodos sensores y el cerebro, por lo que es difícil obtener una señal localizada o incluso muy precisa, pero, sorprendentemente, ¡aún podemos medir nuestra actividad cerebral!
Durante los estados de alerta, el cerebro opera a frecuencias más altas que cuando está relajado o varias fases del sueño. No puede detectar directamente estos estados internos conscientemente, pero al grabarlos y procesarlos, tenemos un bucle de 'retroalimentación biológica' que le permite aprender activamente a controlar su estado cerebral.
__Electroencefalografía__

![Alt text](https://hackster.imgix.net/uploads/attachments/1069286/eeg_km1wqohTAy.jpg?auto=compress%2Cformat&w=740&h=555&fit=max "IoTIA")

El dispositivo necesario para registrar la actividad eléctrica del cerebro es realmente bastante simple. ¡La actividad eléctrica de los cerebros animales se [registró por primera vez](https://en.wikipedia.org/wiki/Electroencephalography#History) hace casi 150 años! Hoy en día, la grabación se obtiene colocando electrodos en el cuero cabelludo, y la señal se [amplifica mediante circuitos integrados de aduanas](http://www.ti.com/product/ADS1299). Debería ser posible construir un buen dispositivo EEG basado en un Texas Instrument ADS1299 y leerlo directamente a través de SPI desde el Jetson Nano, pero para este proyecto, ¡No tengo suficiente tiempo para el desarrollo de circuitos cuando hay que hacer ingeniería de inteligencia artificial!

Para este proyecto, usaré un nuevo [actuador de impulso neuronal OCZ (NIA)](https://en.wikipedia.org/wiki/Neural_Impulse_Actuator). Lo interno ha sido bien documentado [aquí](https://docs.openbci.com/docs/Welcome.html) . Este dispositivo se puede comprar a bajo precio en ciertos sitios de ventas en Internet y actúa como un [dispositivo USB HID](https://en.wikipedia.org/wiki/USB_human_interface_device_class) ; Los datos se pueden leer fácilmente como una secuencia de datos en serie. Los dispositivos EEG más nuevos podrán usar la misma increíble plataforma Jetson Nano con el código que presentaré aquí: solo necesita una forma de recibir datos EEG de transmisión. El mayor beneficio con los dispositivos más nuevos está en la cantidad de canales concurrentes que proporciona el dispositivo EEG.

![Alt text](https://ae01.alicdn.com/kf/H2fd11631dca74dd8bc941a43f80d32383.jpg "IoTIA")

# A la espera que me lleguen los Electrodo Cerebrales EEG OpenBCI/ThinkGear
