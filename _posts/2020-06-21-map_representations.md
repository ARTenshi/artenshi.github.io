---
layout: post
title: "Map representations for mobile robot localization"
categories: robotics
author:
- Luis Contreras
meta: "Robotics"
---

Hemos venido desarrollando progresivamente la teoría y práctica en robótica móvil, como son los robots de servicio, robots humanoides y vehículos autónomos.

Cada robot ha sido diseñado para realizar tareas específicas, por lo que la representación de su entorno no es necesariamente la misma. Un robot de servicio requiere un mapa en el que se indique el espacio libre por el que pueda desplazarse y aquel ocupado por muebles o personas. Un auto autónomo requiere un mapa en el que se indiquen las calles, líneas de tránsito y espacios para estacionarse.

En nuestra publicación "Map representation using hidden Markov models for mobile robot localization", presentado en la 13th International Conference on Electromechanics and Robotics (2018), en Rusia, se propone una representación del mundo útil para la relocalización de robots; esto es, dado un mapa conocido, el robot debe de ser capaz de determinar su posición y orientación en él (por ejemplo, estoy en la sala, a un metro de la puerta y viendo hacia el televisor).

Se considera un robot que se desplaza sobre una superficie y tiene un sensor láser para detectar la posición de los obstáculos frente a él. El robot se desplaza manualmente por una serie de habitaciones con diferentes obstáculos y usando modelos probabilísticos (como son los Modelos Ocultos de Markov) es posible extraer las características clave del entorno que más ayuden a localizar al robot, descartando aquellas que generen ambigüedad o errores.

Además, se ha hecho evidente que, aunque la tarea sea la misma, cada robot requiere una representación diferente de su entorno. Por ejemplo, para la tarea de desplazarse del punto A al punto B en un ambiente dinámico, como lo sería un laboratorio con personas moviéndose en él, la forma y capacidades del robot definen el mapa: un robot de servicio se desplaza sobre un plano (el suelo), por lo que requiere un mapa en 2D en donde se indique el espacio libre y el ocupado por los muebles; por otro lado, un auto a escala, por sus dimensiones, puede desplazarse por lugares que el robot no podría, como debajo de mesas y sillas, por lo que, aunque el tipo de mapa es el mismo (2D), el espacio navegable sería diferente. 

Si la tarea es desplazarse de un lado de una mesa al otro, el robot móvil tendría que rodearla, mientras el auto a escala podría pasar debajo de ella. 

Si, en cambio, se trabaja con robots aéreos, como los drones, el ambiente se vuelve 3D y la misma tarea de moverse al otro lado de una mesa tendría múltiples soluciones: rodeando, pasando debajo o sobre la mesa, por lo que la representación en un mapa del espacio navegable se vuelve distinta -- y más interesante. Es por ello que hemos enfocado parte de nuestros esfuerzos en entender la relación entre la representación del mundo y la tarea a realizarse y de las propiedades físicas del robot para generar modelos del espacio (mapas) útiles para un robot.
