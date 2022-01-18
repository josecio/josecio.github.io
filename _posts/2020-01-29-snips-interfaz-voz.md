---
layout: post
title: Trasteando con Snips
subtitle: Cómo funciona una interfaz de voz
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [libros]
---


Mi TFG del grado de Ingeniería en Tecnologías Industriales se basó en el diseño y fabricación de un [robot asistencial para la tercera edad](https://www.laverdad.es/murcia/upct-crea-robot-20191002111213-nt.html). El objetivo principal era construir un asistente que pudiera hacer un seguimiento del estado anímico del paciente, le recordara la toma de pastillas y, principalmente, le hiciera compañía.

Desde el principio del proyecto, resultó evidente que la forma de comunicarse con el robot debía basarse en una interfaz de voz (VUI), ya que estas presentan una serie de **ventajas que las hacen perfectas para un robot asistencial**.

Al basarse la interacción en el lenguaje natural son más **sencillas de usar** que los botones o teclados en pantalla. Además, al **no necesitar contacto físico** son muy útiles en caso de caídas o pacientes con problemas motores. Y, lo más importante, el lenguaje natural permite que se establezca una **comunicación más cercana** entre el robot y la persona, más empática.

## Componentes de una interfaz de voz

Cuando comencé mi proyecto no tenía ni idea de cómo funciona una interfaz de voz. Uno de los libros que más me ayudó fue Designing Voice User Interfaces: Principles of Conversational Experiences, de Cathy Pearl. También obtuve mucha información de la documentación de Snips, Mycroft y de las API de Google.

Para implementar una interfaz de voz necesitamos, al menos, los siguientes componentes:

**Automated Speech Recognition (ASR).** El ASR transforma el audio que recoge el micrófono (nuestra voz) en un archivo de texto. Un buen ASR debe ser capaz de afrontar diferentes pronunciaciones, acentos, etc.

**Natural Language Understanding (NLU).** El NLU recibe el texto que ha generado el ASR y extrae la intención del usuario (intent) y los parámetros (slots) de la petición. Por ejemplo, del mensaje “¿Me puedes decir si va a llover el lunes en Cartagena?” el intent sería «consulta_meteorologica» y los slots «Cartagena» y «02-02-2020». Para entrenar de forma correcta un NLU hay que tener en cuenta el posible uso de sinónimos, contracciones o palabras intercambiadas.

**Text-to-Speech (TTS).** Convierte el texto de la repuesta en audio. Esta respuesta puede estar predefinida para cada intent u obtenerse mediante Natural Language Generation (NLG).

## Snips, la mejor alternativa offline

¿Qué opciones de ASR, NLU y TTS existen en el mercado? Tanto Microsoft (Azure Cognitive Services) como Google (Dialogflow, Google Cloud) y Amazon (Amazon Lex, Polly) ofrecen estas herramientas como parte de sus servicios de inteligencia artificial en la nube. Estas herramientas se basan en una API con un coste fijo por solicitud (llamada a la API). Son bastante atractivas para aprender y realizar experimentos, ya que están bien documentadas y no requieren engorrosas instalaciones ni un dispositivo con una gran CPU (Google incluso tiene un [tutorial](https://aiyprojects.withgoogle.com/voice/) para montar un asistente de voz en una Raspberry Pi Zero). Además, todas cuentan con una capa gratuita de solicitudes mensuales. 

Personalmente, suelo preferir las alternativas de software open source. Existen algunos proyectos interesantes de ASR, como Kaldi y CMUSphinx. La mejor opción de NLU creo que es Rasa. También encontramos varios TTS entre los que elegir, como MaryTTS y MozillaTTS.

No obstante, si lo que buscamos es un proyecto orientado a desarrollar una VUI que integre todos estos componentes, tenemos dos grandes opciones: Mycroft y Snips. Aunque tienen muchos aspectos en común, me decidí por usar Snips en mi TFG debido a su consola de desarrollo, que simplifica enormemente la tarea de desarrollar skills, y a que funciona completamente en local (no necesita conexión a Internet).

Que el asistente de voz se pudiera ejecutar en local era de gran utilidad para mi proyecto, ya que muchas personas mayores no suelen disponer de conexión a Internet (sobretodo en pueblos pequeños). Por otro lado, la consola de Snips nos permite entrenar al NLU de forma sencilla escribiendo frases con diferentes sintaxis (Snips ofrece la generación automática de frases de entrenamiento como parte de sus servicios premium). También disponemos de diferentes slots ya configurados (fecha, temperatura, números) y podemos crear los nuestros propios cargando datos de diferentes fuentes. Por ejemplo, yo creé un slot “ciudad” enlazando una lista de municipios de España.

Sin embargo, Snips no es era un proyecto open source. Así lo explican en su FAQ:

<img src="{{ 'assets/img/kayak.jpg' | relative_url }}" alt="Consola de Snips: frases de entrenamiento. FAQ de Snips: ¿Es Snips gratuito? ¿Es Snips libre?" />

## El fin del Snips libre (que nunca lo fue)

El 20 de noviembre de 2019, apenas dos meses después de haber presentado mi TFG, Sonos [anunciaba](https://investors.sonos.com/news-and-events/investor-news/latest-news/2019/Sonos-Announces-Acquisition-of-Snips/default.aspx) la compra de Snips por 37,5 millones de dólares. Una semana más tarde, Snips comunicaba que su consola de desarrollo se cerraría el 31 de enero de 2020 para usos no comerciales.

<img src="{{ 'assets/img/kayak.jpg' | relative_url }}" alt="Mensaje en el foro de Snips: la consola cierre" />

La adquisición de Snips me parece un gran movimiento estratégico por parte de Sonos. De esta forma, ya no tiene que depender de las interfaces de voz de Amazon y Google, lo cual siempre viene bien si les piensas [declarar la guerra](https://www.nytimes.com/2020/01/07/technology/sonos-sues-google.html).

Sin embargo, la noticia no ha sentado bien en el mundo maker. Snips contaba con una comunidad de desarrolladores bastante activa (de la que yo mismo empezaba a formar parte), que de la noche a la mañana se han enterado que no podrán continuar con sus proyectos.

Parece que Snips no «será open source pronto» como prometían, ni tampoco seguirá siendo gratuito. Quedan los repositorios de Github que el equipo de Snips había compartido, pero es poco probable que los actualicen en el futuro. Aunque existen otras alternativas para desarrollar interfaces de voz, Snips era de las mejores y su cierre a la comunidad maker es una gran pérdida.
