# Generación de catálogos de moda mediante prompt engineering



> **Curso:** Inteligencia artificial con generación de prompts
> 
> 
> **Número de Comisión:** #96090
> 
> 
> **Autor:** Santiago Mora Ortiz
> 
> 
> **Fecha:** Agosto de 2026
> 
> **Importante:** Parte de código fue creado con ayuda de la IA
>
> **IMPORTANTE:** SE RECOMIENDA DESCARGAR EL ARCHIVO PARA VER LA INTERFAZ
>
>**IMPORTANTE:** Mirar la carpeta assets para ver como se ve la interfaz, visualizar los resultados obtenidos y ver la foto original de la prenda que se subió en un inicio


## Presentación del problema:



### Contexto del Sector



En el e-commerce, existen una gran variedad de marcas de moda pequeñas de distintos tipos de vestuario el cual trabajan para lograr un resultado muy visual y donde la calidad del catálogo en línea puede ser un determinante entre atraer al consumidor para que compre o que se vaya a la competencia. El problema viene cuando estas pequeñas empresas tienen que mantener un catálogo actualizado y super competitivo en sus tiendas online, pues suele venir con varios costes, como lo es la inversión en estudios fotográficos, modelos profesionales y efectos visuales que elevan los costes de producción.

### Definición del Problema



Al momento de sacar una nueva colección o actualizar los productos en tienda web de estas pequeñas empresas de moda, se hace obligatorio pasar por un proceso de producción de fotografía tradicional el cual presenta diversos inconvenientes; entre estos, los altos costos fijos como la contratación de modelos, fotógrafos profesionales, estilistas, alquiler para los sets con iluminación de calidad; los tiempos de producción en donde las tomas pueden tardar semanas en ser acabadas retrasando las colecciones venideras; e incluso, la falta de personalización en sus prendas, porque como bien sabemos, cada uno cuenta con su propio cuerpo y el hecho de solo usar modelos perfectos hace que personas que no se ven como estos, sientan que no pueden tener este tipo de productos y tiendan a devolverlos con más frecuencia o incluso comprar en otros sitios.

### ¿Por qué es importante desarrollar una solución?



Resolver este problema puede ser un gran alivio para aquellos emprendedores pequeños que no cuentan con recursos suficientes para pagar un estudio de fotografía completo con todos los accesorios. De esta manera, usando herramientas de IA de texto e imágenes, podemos lograr resultados de alta calidad que permita crear catálogos estándar, con buenos fondos, un gran impacto visual e incluso llegar a la personalización para cada cliente.


## Desarrollo de la Propuesta de Solución



La solución se compone por dos fases integradas, un modelo de Lenguaje (texto-texto) que actúa como director de arte y estratega, y un modelo de difusión (texto-imagen) que actúa como un estudio fotográfico.

### Texto-texto



El modelo de lenguaje procesa las características del producto combinando varias técnicas de prompt engineering para resolver dos objetivos principales, el primero, la redacción persuasiva en la que redactamos descripciones de cada producto para aumentar su atractivo y conversión en la tienda online y el segundo objetivo para crear un generador de prompts experto en el área (meta-prompting) de fotografía para traducir instrucciones simples en una directriz mucho más robusta. De tal manera, se generan resultados mucho más profesionales evitando la iteración y las alucinaciones.

Para ejecutar este meta-prompting, se aplican las siguientes técnicas:

* **Role Prompting:** Se le asigna al modelo el rol de director de arte de fotografía y especialista en prompt engineering para e-commerce de moda, estableciendo contexto y vocabulario técnico.


* **Zero-prompt-shooting Y Meta-prompting:** Le pedimos generar la ficha y los prompts visuales directamente a partir de las instrucciones y variables, sin ejemplos previos, para evaluar su resultado.


* **One-Shoot-Prompting Y Meta-prompting:** Se incluye dentro del prompt un ejemplo resuelto completo (una prenda previa con su copy), sirviendo como guía de formato.


* **Few-Shot-Prompting Y Meta-prompting:** Se proporcionan dos o tres ejemplos variados (diferentes tipos de prendas y cortes) para fijar de manera estricta la estructura de la salida.



> **Rol:** Actúa como director de arte de fotografía y especialista en prompt engineering para e-commerce de moda.
> 
> 
> **Contexto:** Una marca de moda urbana necesita estandarizar la ficha técnica de una prenda y generar los prompts técnicos para su producción visual en dos formatos: catálogo de estudio y campaña editorial.
> 
> 

#### Ejemplo (one-shot):



**Lo que vas a recibir:**

* Tipo de prenda: Chaqueta Bomber impermeable


* Composición y color: Poliéster reciclado, color negro mate


* Perfil del modelo: Mujer joven contextura delgada, cabello liso


* Valores de marca: Estilo urbano técnico, resistencia al agua



**Salida esperada:**

* **Ficha comercial:** Chaqueta Bomber urbana con acabado mate impermeable. Confeccionada con textil técnico de alta resistencia, cuello acanalado y cierre reforzado. Ideal para climas cambiantes con el máximo estilo.


* Textil ultraligero y térmico


* Impermeabilidad de grado urbano


* Calce regular fit contemporáneo




* **Prompt técnico: catálogo e-commerce:** `Commercial studio fashion photography of a young woman with slim build and straight hair wearing a matte black waterproof bomber jacket, clean seamless pure white background, professional three-point softbox lighting, 85mm lens, f/8, sharp focus on waterproof fabric texture, high-end clean e-commerce catalog look --ar 4:5`

* **Prompt técnico campaña editorial:** `Editorial streetwear lifestyle photography of a young woman wearing a matte black bomber jacket in a rainy modern city street, warm neon lights reflection on wet pavement, candid walking posture, 35mm film aesthetic, shallow depth of field --ar 16:9`


#### Tarea actual:



**Lo que vas a recibir:**

* Tipo de prenda: Hoodie oversized con bolsillo canguro


* Composición y color: Algodón rústico pesado 400 GSM, color verde oliva


* Perfil del modelo: Hombre joven de contextura atlética, cabello corto ondulado


* Valores de marca: Minimalismo urbano, alta durabilidad, corte contemporáneo



**Instrucciones:**

1. Redacta una descripción de producto para e-commerce (100-120 palabras) con tono moderno, persuasivo y estructurado en viñetas de valor.


2. Construye un meta-prompt en inglés para fotografía de catálogo e-commerce (estudio, fondo blanco, iluminación uniforme, detalle de tejido).


3. Construye un meta-prompt en inglés para fotografía editorial lifestyle (entorno urbano exterior, luz natural, encuadre cinematográfico).



**Consigna de salida:**

* **Ficha comercial:** incluye descripción persuasiva y especificaciones técnicas.


* **Prompt técnico: catálogo e-commerce:** incluye prompt en inglés con modificadores de cámara, iluminación y fondo.


* **Prompt técnico campaña editorial:** incluye prompt en inglés con atmósfera urbana, ángulo de toma y composición.





### Componente texto-imagen (generación visual)



El modelo visual recibe los meta-prompts generados por el LLM para sintetizar los activos finales requeridos por la marca.

**Ejemplo del catálogo:**

```text
Commercial studio fashion photography of a young athletic man wearing an oversized olive green heavy cotton hoodie, relaxed frontal pose, pure seamless white background, professional softbox three-point lighting, clean fabric texture, sharp focus on seams and heavy drape, shot on Hasselblad H6D-100c, 85mm lens, f/8 aperture, ISO 100, high-end clean e-commerce catalog look --ar 4:5 --q 2

```

**Ejemplo de la editorial:**

```text
Editorial streetwear lifestyle photography of a young man wearing an oversized olive green hoodie, leaning against a brutalist raw concrete wall in an urban city street, cinematic warm golden hour side lighting, subtle background bokeh of modern architecture, 35mm photography aesthetic, authentic candid street-style posture, ultra-realistic cotton weave texture --ar 16:9 --v 6.0

```



## Justificación de la viabilidad del proyecto



Con las herramientas con las que se cuentan actualmente se puede crear un primer MCP que más adelante pueda evolucionar a una app completa si se quisiera.

Asimismo, el tiempo de ejecución podría tomar alrededor de 2 minutos por producto y por cada ficha y no se necesitaría de una infraestructura completa pues trabajaría directamente en la nube.

Por último; sobre los costos, usamos en este caso la suscripción de Google AI Pro para facilitar algunos aspectos como la creación de imágenes con mayor calidad usando NanoBanana Pro, aumentar los límites de uso y usar por más tiempo los modelos más potentes de Google.



## Identificación de limitaciones



* **Consistencia exacta de logos y diseños complejos:** Los modelos de imágenes basados en texto pueden interpretar libremente tipografías o logotipos específicos.


* **Mitigación:** Para el alcance de este proyecto, el objetivo es enfocarnos en partes esenciales de las prendas como la caída de la tela, la paleta de colores y la textura del material, utilizando descriptores de peso en los prompts.




* **Consistencia de modelo físico entre tomas:** Variación en los rostros generados al cambiar de escenario.


* **Mitigación:** Se utilizarán descripciones detalladas en las variables de entrada para garantizar los menores cambios posibles a lo largo del proyecto.







## Objetivos



### Objetivo General



Desarrollar una prueba de concepto (POC) en un Jupyter Notebook que demuestre la viabilidad técnica y operativa de automatizar la creación de catálogos comerciales y campañas visuales para marcas de moda emergentes, integrando técnicas como Role Prompting, One/Few-Shot y Meta-Prompting con modelos multimodales (texto-texto y texto-imagen) de forma eficiente y de bajo costo.

### Objetivos específicos



* **Experimentar y comparar técnicas de prompting:** Evaluar el desempeño entre zero-prompt, one-shot y few-shot prompting para la redacción de fichas comerciales y la construcción de meta-prompts fotográficos.


* **Optimizar el consumo de recursos y llamadas a la API:** Diseñar una estructura de prompt que resuelva en una sola consulta la ficha descriptiva y los dos prompts de imagen (catálogo de estudio y campaña editorial), reduciendo el gasto de tokens.


* **Validar la integración multimodal:** Documentar los resultados visuales obtenidos a partir de los meta-prompts en el motor de imagen, comprobando los detalles de los productos en la imagen como la caída del textil, la iluminación, el ambiente, etc.





## Metodología



El proyecto se desarrollará a través de cuatro etapas:

* **Etapa 1: Recopilación y organización de los datos de la prenda**

Se definen los datos clave que describen el producto como el tipo de prenda, composición, color, estilo visual de la marca, etc.


* **Etapa 2: Pruebas y generación con el modelo de texto**

Se estructura el entorno de trabajo en Python dentro del Jupyter Notebook.


Configuramos el modelo de lenguaje asignándole el rol de director de arte.


Hacemos pruebas comparando los tipos de prompts como Zero-Shot, One-Shot y Few-Shot con el fin de identificar cuál obtiene mayor precisión en el texto comercial y los prompts de fotografía en inglés (iluminación, tipo de plano).


* **Etapa 3: Creación de las imágenes con la IA visual**

Los prompts obtenidos del modelo de texto se introducen en la herramienta de generación de imágenes (en este caso de Nano Banana).


Obtenemos dos resultados visuales: la foto limpia de catálogo con fondo blanco y la foto editorial ambientada en la calle.


* **Etapa 4: Revisión de calidad, tiempos y costos**

Evaluamos las imágenes y los textos para ver que cumplan con la estética esperada, midiendo también el tiempo total y el consumo de consultas y tokens para estar seguros de que el proceso es rentable y más eficiente para la empresa pequeña.





## 4. Herramientas y Tecnologías



### Técnicas de Prompting Utilizadas y su Justificación



* **Role Prompting:** Le asignamos a la IA el rol de director de arte y especialista en prompts para moda. Esto ayuda a que el modelo se ponga en contexto y utilice un tono llamativo para vender la prenda usando los términos adecuados de fotografía (como tipos de lentes, luces y texturas de la tela).


* **Meta-Prompting:** La IA de texto no solo escribe la descripción de la prenda, sino que crea el prompt detallado en inglés que necesita la IA de imagen para hacer las fotos. De esta manera, el usuario no tiene que inventar configuraciones de cámara complejas, ya que el modelo las crea automáticamente.


* **Zero-Shot Prompting:** Consiste en pedirle al modelo que genere la ficha y los prompts de imagen dándole únicamente las instrucciones y los datos de la prenda, sin mostrarle ningún ejemplo. Esto sirve para conocer la capacidad de la IA y ver qué tan bien responde.


* **One-Shot y Few-Shot Prompting:** Aquí le mostramos a la IA uno o varios ejemplos resueltos del mismo mensaje. Al ver un ejemplo de cómo debe quedar el texto y los prompts, el modelo entiende mejor el formato que esperamos y comete menos errores.



### Herramientas y Programas Utilizados



* **Python y Jupyter Notebook:** Es el entorno donde organizamos todo el proyecto. Permite mezclar explicaciones escritas, bloques de código que se pueden ejecutar y las imágenes generadas para que cualquier persona pueda revisar el funcionamiento paso a paso.


* **Gemini 3.7 flash y 3.1 pro:** Son los modelos de texto que procesan la información de la prenda, redactan la ficha comercial y arman los prompts fotográficos en inglés de manera rápida.


* **Google Nano Banana:** Es la herramienta visual que toma los textos en inglés generados por el modelo de lenguaje y crea las imágenes finales entregando la foto limpia de catálogo con fondo blanco y la foto de campaña en la calle.





## Implementación:



La implementación con la explicación se encuentra en el archivo `entrega2_fast_prompting.ipynb`.



## Conclusión:



Este proyecto nos ayuda a entender que con un prompt bien estructurado no es necesario complicarse ni gastar recursos de más pues en lugar de hacer varias iteraciones y prueba-error, la IA logra analizar la foto de la prenda, redactar la descripción de la ficha comercial y armar los dos prompts fotográficos en una sola consulta. Así nos ahorramos llamadas innecesarias a la API, evitamos bloqueos de uso y conseguimos un resultado listo para publicar.
