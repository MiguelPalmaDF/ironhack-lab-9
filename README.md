# ironhack-lab-9
Repositorio de Laboratorio 9 de IronHack

---

# Microservices Architecture Lab

## Implementation Simulation

### Design Solution Outline:

**Identificación de Microservicios:**

1. **User Service**:
   - Responsabilidades: Gestión de perfiles de usuario, autenticación y autorización.
   - Comunicación: Utiliza tokens JWT para autenticación. Comunicación síncrona con otros servicios a través de REST.
   - Datos: Base de datos NoSQL para almacenar datos de usuario.

2. **Product Catalog Service**:
   - Responsabilidades: Gestión de productos, búsqueda y categorización.
   - Comunicación: REST para comunicación síncrona con el frontend y otros servicios.
   - Datos: Base de datos NoSQL para alta disponibilidad y consultas rápidas.

3. **Order Service**:
   - Responsabilidades: Gestión de carritos, procesamiento de pedidos, pagos y historial de pedidos.
   - Comunicación: REST para operaciones y comunicación con el Payment Service para procesamiento de pagos.
   - Datos: Base de datos relacional para garantizar la consistencia transaccional.

4. **Customer Support Service**:
   - Responsabilidades: Gestión de tickets de soporte, devoluciones, quejas y comentarios.
   - Comunicación: REST para interacción con User Service y Order Service.
   - Datos: Base de datos NoSQL para gestión eficiente de tickets.

**Inter-Service Communication:**

- **API Gateway:** Utilizado para manejar las solicitudes de los clientes y enrutar a los microservicios adecuados.
- **Message Broker:** Utilizado para la comunicación asíncrona entre servicios, especialmente para operaciones que no requieren respuesta inmediata.

### Project Simulation Report:

#### Migration Roadmap:

1. **Identificación y Prioritización:**
   - Iniciar con la Gestión de Usuarios y Catálogo de Productos, ya que son menos críticos que el procesamiento de pedidos.
   - Continuar con el Procesamiento de Pedidos y finalmente el Soporte al Cliente.

2. **Estrategia de Migración:**
   - **Gestión de Usuarios:**
     - Migrar datos de usuarios a una base de datos NoSQL.
     - Implementar el User Service con autenticación JWT.
     - Redirigir el frontend para interactuar con el nuevo User Service.
   - **Catálogo de Productos:**
     - Migrar productos a una base de datos NoSQL.
     - Implementar el Product Catalog Service.
     - Actualizar el frontend para utilizar el nuevo servicio de catálogo.
   - **Procesamiento de Pedidos:**
     - Crear el Order Service y establecer comunicación con el Payment Service.
     - Migrar datos de pedidos a una base de datos relacional.
     - Ajustar el frontend para el nuevo flujo de pedidos.
   - **Soporte al Cliente:**
     - Migrar tickets de soporte a una base de datos NoSQL.
     - Implementar el Customer Support Service.
     - Actualizar el frontend para interactuar con el nuevo servicio de soporte.

#### Architecture Documentation:

**Proposed Microservices Architecture:**

![Microservices Architecture Diagram](https://via.placeholder.com/800x400?text=Microservices+Architecture+Diagram)

La decisión de utilizar bases de datos NoSQL para servicios que requieren alta disponibilidad y consultas rápidas (como User Service y Product Catalog Service) se basa en la necesidad de rendimiento y escalabilidad. Para el Order Service, se eligió una base de datos relacional debido a la necesidad de consistencia transaccional.

El uso de un API Gateway facilita la gestión de solicitudes de clientes y la redirección a los microservicios apropiados, mientras que un Message Broker permite una comunicación asíncrona eficiente entre los servicios, mejorando la capacidad de respuesta y la resistencia del sistema.
