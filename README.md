##Intro


Este es un proyecto y una guia de como se creo un invernadero hidroponico vertical con tecnologias asociadas a la nuve , control matematico PID , circuitos , iot , y sistemas de control.

Para el control climático en los invernaderos, se ha implementado un sistema controlado por PID (potencial integral derivativo). Este sistema se ejecuta en un servicio de AWS Lambda, que recopila los datos de los sensores instalados en el invernadero y calcula los ajustes necesarios para mantener un clima estable y favorable para el crecimiento de las plantas.

Integrar tecnología de vanguardia, como la hidroponía y la iluminación LED, junto con un sistema de control climático basado en PID y alojado en AWS Lambda, ofrece numerosas ventajas en la agricultura urbana. Además de superar las dificultades asociadas con el espacio, el suelo y las condiciones ambientales, esta solución tecnológica promueve una producción más eficiente, sostenible y de mayor calidad en el cultivo de fresas y tomates en invernaderos urbanos. El uso de GitHub para compartir y colaborar en el desarrollo de este tipo de tecnologías permite que la comunidad agrícola y científica continúe impulsando la innovación en el sector y asegure un futuro más próspero para la agricultura urbana.





#Agricultura vertical
La agricultura vertical es una forma de aprovechar el entorno controlado de un edificio comercial moderno y convertirlo en una instalación apta para invernaderos. Al apilar las plantas verticalmente en estanterías o pilares altos, la agricultura vertical permite un mayor rendimiento para una superficie de terreno determinada.

#Controlador PID
Los sistemas de control son omnipresentes en aplicaciones industriales, médicas, militares, de automoción, de servicios públicos y muchas otras, y a veces aparecen en nuestra vida cotidiana. Sin embargo, los hay de muchos tipos, de los cuales el control PID es sólo uno, aunque el más sofisticado.
La nube de AWS
Amazon Web Services (AWS) es la plataforma en la nube más completa y ampliamente adoptada del mundo, que ofrece más de 200 servicios con todas las funciones desde centros de datos de todo el mundo. Millones de clientes, entre los que se incluyen las startups de más rápido crecimiento, las empresas más grandes y las principales agencias gubernamentales, utilizan AWS para reducir costes, ser más ágiles e innovar con mayor rapidez.
Implementación


##Caracterización del sistema

#Matlab

Con la ayuda de la herramienta Ident, se llevó a cabo la caracterización del sistema, utilizando la temperatura del sistema y la tensión aplicada a la resistencia como variables para ajustar la temperatura al punto de consigna deseado.


Además, utilizando la herramienta de sintonización Simulink, fue posible encontrar los coeficientes para el control PID.

#Circuito electrónico

El circuito consta de control de temperatura, la variable temperatura es leída por un sensor DHT11 debido a su alta resolución, Es leída por el Microcontrolador ESP32,. Como actuador, vamos a utilizar una bombilla que nos permite controlar la intensidad en un intento de gestionar la temperatura en el interior de un jardín vertical.

En el circuito se utiliza un amplificador operacional que detecta el cruce con cero, con la finalidad de sincronizar el PWM con la frecuencia de la red eléctrica. Para la alimentación se utiliza un optoacoplador que envía la señal al Triac para controlar la tensión sobre la resistencia.

La siguiente imagen muestra el circuito del esquema electrónico.


#Control en Python

Se desarrolló un programa en python que se configura con los coeficientes PID, la idea del programa es poder conectarse con los datos que se envían a la nube, de esta manera python se suscribe al tema que se genera cada vez que se envía un dato, y así mismo, el control en python ajusta el ancho de pulso que el microcontrolador(ESP32) enviará al circuito, para controlar la temperatura de la resistencia.

 En la siguiente imagen se muestra el código desarrollado.




En la siguiente imagen se muestra la respuesta.



#Resultados

Como resultado, el objetivo principal fue completado, y es posible enviar los datos a la nube en AWS, en la siguiente imagen es posible ver como los datos son subidos a la nube.



En la siguiente imagen es posible ver el control de PWM en la señal AC, y la sincronización con la señal de red.




En la última imagen, es posible ver el modelo que se realizó, que consta de dos plantas del cultivo vertical de fresas.

Traducción realizada con la versión gratuita del traductor www.DeepL.com/Translator