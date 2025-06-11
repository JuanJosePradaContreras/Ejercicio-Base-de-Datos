# Diseño de Base de Datos NoSQL para el Parque Nicole

## Integrantes

* Juan Jose Prada Contreras
* Victor Alejandro Pabon
* Breyner Fernando Pinto

## Introducción

El objetivo principal de este diseño es estructurar una base de datos NoSQL utilizando MongoDB para el parque de diversiones "Parque Nicole". Se optó por un enfoque híbrido que combina incrustación (embedding) y referencias (referencing) dependiendo de la cardinalidad, frecuencia de acceso y tamaño de los documentos relacionados.

## Análisis de Entidades y Propuesta de Modelo de Datos

### Diagrama ER

![Diagrama Entidad Relación](DiagramaER.jpg)

### Atracciones

**Nombre de la Colección:** Atracciones.

**Atributos Propuestos:**

- _id: ObjectId
- nombre:string
- tipo: string
- descripción: string
- altura_minima: number
- capacidad: number
- estado: number
- tiempo_espera_promedio: string

**Relaciones:**

- Tickets
- Empleados
- Mantenimiento

### Zonas del Parque

**Nombre de la Colección:** Zonas del Parque.

**Atributos Propuestos:**

- _id: ObjectId
- nombre: string
- descripción: string

**Relaciones:**

- Atracciones
- Empleados

### Visitantes

**Nombre de la colección:** Visitantes.

**Atributos Propuestos:**

- _id: ObjectId
- nombre: string
- apellido: string
- edad: number
- email: string
- numero_de_telefono: number
- historial_visitas: array {data time}

**Relaciones**

- Ticket

### Tickets

**Nombre de la colección:** Tickets

**Atributos Propuestos**

- _id: ObjectId
- tipo_de_ticket: string
- precio: string
- fecha_de_compra: data time
- fecha_de_expiración: data time

**Relaciones**

- Visitante
- Atracciones

### Empleados

**Nombre de la colección:** Empleados

**Atributos Propuestos:**

- _id: ObjectId
- nombre: string
- apellido: string
- tipo_de_identificación: string
- identificación: number
- numero_de_celular: number
- correo_electronico: string
- cargo: string
- horario_de_trabajo: array {data time}

**Relaciones**

- Atracciones
- Zonas del Parque
- Mantenimiento

### Eventos

**Nombre de la colección:** Eventos

**Atributos Propuestos**

- _id: ObjectId
- nombre_evento: string
- descripción_evento: string
- horario: data time

**Relaciones**

-Zonas del Parque
-Empleados

### Mantenimiento

**Nombre de la colección:** Mantenimiento

**Atributos Propuestos**

- _id: ObjectId
- fecha_de_mantenimiento: array {data time}
- descripción_mantenimiento: string
- precio: string

**Relaciones**

- Empleado
- Atracciónes