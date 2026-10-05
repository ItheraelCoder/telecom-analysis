# 📊 ConnectaTel: Análisis Exploratorio de Datos y Segmentación de Clientes

Este proyecto realiza un análisis exploratorio de datos (EDA) integral sobre la base de usuarios y el tráfico de consumo de la empresa de telecomunicaciones **ConnectaTel**. El objetivo principal es evaluar la calidad de los datos, identificar patrones de consumo de voz y mensajería, segmentar a los usuarios por edad y uso, y proponer recomendaciones estratégicas para optimizar la oferta comercial de la compañía.

---

## 📌 Resumen Ejecutivo

* **Calidad de Datos:** Limpieza y tratamiento de valores centinela (`?`), nulos estructurales (diferenciación entre llamadas y SMS) e inconsistencias en fechas de registro.
* **Segmentación:** Clasificación de usuarios por nivel de uso (*Bajo*, *Medio*, *Alto*) y por grupos demográficos (*Jóvenes*, *Adultos*, *Adultos Mayores*).
* **Patrones Extremos:** Identificación de clientes con uso intensivo (*outliers*) para mitigar el riesgo de cancelación (*churn*) por cobros excesivos.
* **Estrategia Comercial:** Propuestas para el diseño de nuevos planes de voz y mensajería orientados a retención y captación de clientes.

---

## 🛠️ Tecnologías Utilizadas

* **Lenguaje:** Python 3.12+
* **Entorno:** Jupyter Notebook
* **Librerías:** `pandas`, `numpy`, `matplotlib`, `seaborn`

---

## 📊 Principales Hallazgos (Insights)

<details>
<summary><b>Haz clic aquí para desplegar el Análisis Ejecutivo</b></summary>

<br>

#### ⚠ Problemas detectados en los datos

* **Dataset `users`:**
  * **Valores centinela en `city`:** La columna presentaba el carácter `?`. Al reemplazarlo por nulos, representó un **14.13%** de datos faltantes.
  * **Nulos de negocio en `churn_date`:** Un **88.4%** de la columna contenía nulos, los cuales representan a los **clientes activos que continúan con el servicio**.
  * **Anomalías temporales en `reg_date`:** Existían fechas de registro futuras, corregidas convirtiendo a formato fecha e imputando las inconsistencias como `pd.NaT`.
* **Dataset `usage`:**
  * **Nulos menores en `date`:** Un **0.13%** de nulos que se descartaron por falta de representatividad.
  * **Nulos estructurales en `duration` (55.2%) y `length` (44.7%):** Se conservaron intactos porque obedecen a la variable `type` (los mensajes de texto no generan duración de llamadas y las llamadas no generan longitud de caracteres).

---

#### 🔍 Segmentos por Edad

* **Adultos (30–59 años):** Constituyen el núcleo principal con aproximadamente **2,000 usuarios**, representando la mayor estabilidad económica y menor morosidad.
* **Adultos Mayores (60+ años):** Representan una porción relevante con cerca de **1,200 usuarios**, requiriendo canales de atención accesibles y planes con foco en llamadas de voz.
* **Jóvenes (<30 años):** Representan el segmento menor con **~750 usuarios**, mostrando una oportunidad clara para campañas de adquisición orientadas a audiencias jóvenes.

---

#### 📊 Segmentos por Nivel de Uso

* **Uso medio:** Base principal del negocio con **~2,900 usuarios**, garantizando la mayor parte de los ingresos recurrentes y estables de ConnectaTel.
* **Bajo uso:** Segundo grupo más numeroso con **~750 usuarios**, con potencial para migrar a planes superiores mediante incentivos de reactivación.
* **Alto uso:** Grupo reducido con **~300 usuarios**, caracterizado por duraciones atípicas de llamadas y alto volumen de mensajes (*outliers*), con mayor riesgo de *churn* por cobros excesivos si no tienen tarifas planas.

---

➡️ **Esto sugiere que...**
La estrategia comercial de ConnectaTel no debe enfocarse únicamente en captar nuevos clientes, sino en **proteger la base central de Uso Medio** e implementar acciones defensivas en el segmento de **Alto Uso** para evitar la cancelación de líneas valiosas por sobrecostos. Además, la baja presencia del público joven señala la necesidad de reestructurar la oferta comercial para diversificar la audiencia.

---

#### 💡 Recomendaciones

* **Plan "Voz & Mensajes Ilimitados":** Diseñar una tarifa plana premium para los ~300 usuarios de **Alto uso**, eliminando penalizaciones por sobrecostos y asegurando un alto *ARPU*.
* **Plan "Conecta Senior":** Crear un paquete accesible y simplificado de voz/minutos dirigido al segmento de **Adultos Mayores** (~1,200 usuarios).
* **Plan "Conecta Joven":** Lanzar una oferta de entrada económica con tarifas atractivas en mensajes y llamadas cortas para captar la franja de menores de 30 años.
* **Upselling automatizado:** Implementar alertas de consumo para invitar a los clientes de **Bajo uso** a migrar a planes medios cuando su tráfico empiece a incrementarse.

</details>
