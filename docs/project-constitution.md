# Cognaris Starter Platform

## Constitución técnica del proyecto

**Estado:** Aprobación inicial
**Versión:** 0.1
**Ámbito:** Plataforma interna de ingeniería de Cognaris

---

## 1. Propósito

Cognaris Starter Platform es la base técnica reutilizable para iniciar proyectos de software a medida desarrollados por Cognaris.

Su propósito es reducir el tiempo necesario para comenzar nuevos productos, estandarizar decisiones técnicas y evitar la repetición de infraestructura, arquitectura y funcionalidades comunes.

La plataforma proporcionará una base modular para desarrollar:

* aplicaciones web;
* APIs;
* sistemas administrativos;
* productos SaaS;
* aplicaciones móviles;
* portales para clientes;
* herramientas internas;
* soluciones empresariales a medida.

La plataforma no representa un producto final para un cliente específico. Es una infraestructura interna de ingeniería sobre la cual se construyen productos.

---

## 2. Visión

Cognaris debe poder comenzar un nuevo proyecto desde una base:

* funcional;
* segura;
* probada;
* documentada;
* modular;
* actualizable;
* mantenible;
* preparada para web y dispositivos móviles.

Un nuevo proyecto no debe comenzar resolviendo nuevamente autenticación, estructura de carpetas, manejo de errores, configuración de entornos, integración continua o documentación básica.

Debe comenzar resolviendo el problema de negocio del cliente.

---

## 3. Principios fundamentales

### 3.1. Núcleo pequeño y estable

El núcleo incluirá únicamente capacidades necesarias para la mayoría de los proyectos.

Una funcionalidad no se incorporará al núcleo solo porque sea útil en un proyecto particular.

Para formar parte del núcleo deberá cumplir, como mínimo, estas condiciones:

* ser reutilizable en múltiples tipos de proyectos;
* no depender de un dominio empresarial específico;
* poseer una interfaz estable;
* contar con pruebas;
* estar documentada;
* no introducir dependencias innecesarias.

---

### 3.2. Modularidad antes que personalización permanente

Las funcionalidades especializadas se implementarán como módulos opcionales.

Ejemplos:

* roles y permisos;
* organizaciones;
* multitenancy;
* facturación;
* notificaciones;
* archivos;
* tareas en segundo plano;
* geolocalización;
* reportes;
* workflows.

Los módulos deberán poder activarse o excluirse sin alterar el núcleo de forma destructiva.

---

### 3.3. Separación entre plataforma y producto

La plataforma define:

* arquitectura;
* convenciones;
* componentes comunes;
* contratos;
* herramientas;
* flujos de trabajo;
* infraestructura reusable.

Cada producto define:

* reglas de negocio;
* entidades específicas;
* procesos del cliente;
* interfaz especializada;
* integraciones particulares;
* decisiones comerciales.

El código específico de un cliente no debe incorporarse al núcleo.

---

### 3.4. Arquitectura pragmática

La plataforma utilizará separación de responsabilidades y arquitectura limpia cuando aporte claridad, testabilidad y mantenibilidad.

No se crearán capas, abstracciones o interfaces sin una necesidad concreta.

La arquitectura debe reducir complejidad, no fabricarla.

---

### 3.5. Contratos antes que implementaciones

Las capacidades compartidas entre backend, frontend web y aplicación móvil deberán definirse mediante contratos explícitos.

Se priorizarán:

* OpenAPI;
* esquemas de validación;
* modelos de errores uniformes;
* estructuras de paginación consistentes;
* versionado de API;
* documentación de endpoints.

Los clientes web y móviles deberán consumir el mismo contrato de API.

---

### 3.6. Seguridad por defecto

La seguridad formará parte de la base inicial y no será una etapa posterior.

La plataforma deberá incluir o facilitar:

* manejo seguro de credenciales;
* variables de entorno;
* políticas de contraseñas;
* autenticación segura;
* expiración y renovación de sesiones;
* control de acceso;
* validación de entradas;
* protección contra abuso;
* tratamiento seguro de archivos;
* registro de eventos relevantes;
* manejo responsable de datos personales.

Las configuraciones inseguras no deberán utilizarse como valores predeterminados.

---

### 3.7. Privacidad y minimización de datos

Solo se almacenarán los datos necesarios para cumplir una finalidad definida.

Las funcionalidades deberán evitar:

* recolectar datos sin propósito;
* registrar información sensible en logs;
* duplicar datos personales;
* conservar información indefinidamente sin justificación;
* exponer datos internos en respuestas de error.

Cada producto derivado deberá definir sus propios límites de privacidad.

---

### 3.8. Testabilidad desde el diseño

Las funcionalidades deberán diseñarse para poder ser probadas.

El proyecto utilizará:

* pruebas unitarias;
* pruebas de integración;
* pruebas de API;
* pruebas de componentes;
* pruebas end-to-end;
* pruebas de aceptación cuando corresponda.

Una funcionalidad crítica no se considerará terminada si depende exclusivamente de pruebas manuales.

---

### 3.9. Automatización repetible

Toda tarea frecuente deberá ser candidata a automatización.

Esto incluye:

* instalación;
* configuración local;
* ejecución de pruebas;
* análisis estático;
* creación de entornos;
* generación de documentación;
* construcción;
* despliegue;
* actualización de dependencias.

La configuración del proyecto deberá poder reproducirse sin depender de conocimiento no documentado.

---

### 3.10. Evolución controlada

La plataforma tendrá versiones propias.

Los cambios deberán clasificarse según su impacto:

* compatibles;
* deprecados;
* incompatibles;
* experimentales.

Los proyectos derivados deberán poder identificar con qué versión de la plataforma fueron creados.

Las migraciones importantes deberán documentarse.

---

## 4. Stack tecnológico base

### 4.1. Backend

El backend utilizará como base:

* Python;
* Django;
* Django REST Framework;
* PostgreSQL;
* JWT;
* pytest;
* factory_boy;
* Ruff;
* Black;
* isort;
* mypy;
* OpenAPI;
* Docker;
* GitHub Actions.

Django será responsable de:

* autenticación;
* API;
* persistencia;
* lógica de aplicación;
* administración;
* integraciones del servidor.

PostGIS, Redis, Celery y otros servicios serán opcionales.

---

### 4.2. Frontend web

El frontend web utilizará como base:

* React;
* TypeScript;
* Vite;
* React Router;
* TanStack Query;
* React Hook Form;
* Zod;
* Tailwind CSS;
* Material 3 o componentes visuales compatibles;
* Vitest;
* Testing Library;
* Playwright;
* ESLint;
* Prettier.

El frontend se organizará por funcionalidades y no únicamente por tipo técnico de archivo.

---

### 4.3. Aplicaciones móviles

Las aplicaciones móviles utilizarán como base:

* Flutter;
* Dart;
* Material 3;
* BLoC;
* Freezed;
* Dio;
* GoRouter;
* flutter_secure_storage;
* json_serializable;
* mocktail;
* integration_test.

Flutter consumirá los mismos contratos de API utilizados por el frontend web.

---

### 4.4. Base de datos

PostgreSQL será la base de datos predeterminada.

SQLite podrá utilizarse únicamente en contextos específicos de pruebas o herramientas locales cuando no altere el comportamiento esperado.

No se diseñarán funcionalidades suponiendo características exclusivas de SQLite.

---

## 5. Capacidades obligatorias del núcleo

La primera versión estable deberá incluir:

### 5.1. Usuarios

* modelo de usuario personalizado;
* email como identificador principal;
* activación y desactivación;
* perfil básico;
* fecha de creación;
* fecha del último acceso;
* administración desde Django Admin.

El núcleo no incluirá roles empresariales rígidos.

Se conservarán los mecanismos administrativos propios de Django:

* `is_active`;
* `is_staff`;
* `is_superuser`.

---

### 5.2. Autenticación

* inicio de sesión;
* cierre de sesión;
* renovación de sesión;
* recuperación de contraseña;
* cambio de contraseña;
* consulta del usuario autenticado;
* manejo uniforme de errores de autenticación.

El registro público será configurable.

---

### 5.3. Landing page

* nombre genérico;
* logo genérico;
* hero;
* descripción;
* características;
* llamada a la acción;
* pie de página;
* acceso al formulario de contacto;
* diseño responsive;
* metadatos SEO básicos.

---

### 5.4. Formulario de contacto

* nombre;
* email;
* teléfono opcional;
* asunto;
* mensaje;
* consentimiento;
* protección básica contra abuso;
* almacenamiento;
* estado de seguimiento;
* notificación configurable.

---

### 5.5. Gestión de contactos

La plataforma distinguirá entre usuarios del sistema y contactos comerciales u operativos.

La gestión base deberá permitir:

* crear;
* consultar;
* editar;
* buscar;
* filtrar;
* etiquetar;
* registrar notas;
* archivar;
* exportar.

No deberá convertirse en un CRM completo dentro del núcleo.

---

### 5.6. Dashboard

El dashboard base deberá incluir:

* navegación;
* encabezado;
* perfil;
* tarjetas de métricas genéricas;
* actividad reciente;
* tablas reutilizables;
* estados vacíos;
* loading;
* manejo de errores;
* diseño responsive.

Los indicadores de negocio pertenecerán a cada producto.

---

### 5.7. Branding

El sistema deberá permitir configurar:

* nombre de la aplicación;
* nombre corto;
* logo;
* favicon;
* color principal;
* color secundario;
* email de soporte;
* textos institucionales básicos.

La identidad visual genérica deberá poder sustituirse sin modificar lógica de negocio.

---

### 5.8. Salud y versión

El backend deberá exponer mecanismos para consultar:

* estado de salud;
* disponibilidad;
* versión desplegada.

Rutas sugeridas:

```text
/api/v1/health/
/api/v1/readiness/
/api/v1/version/
```

---

### 5.9. Manejo de errores

Las APIs utilizarán una estructura consistente.

Ejemplo:

```json
{
  "code": "validation_error",
  "message": "No fue posible procesar la solicitud.",
  "fields": {
    "email": [
      "Ingrese una dirección de correo válida."
    ]
  }
}
```

Los errores internos no deberán revelar trazas, secretos o detalles de infraestructura.

---

### 5.10. Auditoría mínima

Las entidades relevantes deberán permitir conocer:

* fecha de creación;
* fecha de modificación;
* usuario creador, cuando corresponda;
* usuario modificador, cuando corresponda.

La auditoría avanzada será un módulo opcional.

---

## 6. Capacidades excluidas inicialmente

Las siguientes funcionalidades no formarán parte del núcleo inicial:

* roles empresariales;
* permisos complejos por dominio;
* multitenancy;
* facturación;
* pasarelas de pago;
* mensajería instantánea;
* WhatsApp;
* SMS;
* geolocalización;
* mapas;
* inteligencia artificial;
* workflows complejos;
* reportes especializados;
* integración con sistemas externos;
* almacenamiento documental avanzado.

Podrán desarrollarse como módulos independientes.

---

## 7. Estrategia de modularidad

Los módulos deberán declarar:

* propósito;
* dependencias;
* configuración;
* migraciones;
* endpoints;
* componentes web;
* componentes móviles;
* pruebas;
* documentación;
* compatibilidad con versiones del núcleo.

Un módulo no deberá acceder directamente a detalles internos de otro módulo.

La comunicación entre módulos se realizará mediante:

* servicios de aplicación;
* contratos;
* eventos;
* interfaces explícitas;
* APIs públicas internas.

---

## 8. Política de ramas

Las ramas representan trabajo temporal.

La plataforma utilizará:

```text
main
develop
feature/*
fix/*
release/*
hotfix/*
```

### `main`

Contendrá versiones estables.

### `develop`

Contendrá cambios integrados para la próxima versión.

### `feature/*`

Contendrá funcionalidades o especificaciones en desarrollo.

### `fix/*`

Contendrá correcciones no urgentes.

### `release/*`

Contendrá tareas de estabilización y preparación de una versión.

### `hotfix/*`

Contendrá correcciones urgentes derivadas de una versión estable.

Las ramas no se utilizarán como sistema permanente de selección de módulos.

Una vez fusionada una rama de trabajo, deberá eliminarse local y remotamente.

---

## 9. Flujo de desarrollo

El flujo estándar será:

```text
descubrimiento
→ especificación
→ decisión arquitectónica
→ criterios de aceptación
→ pruebas
→ implementación
→ revisión
→ UAT
→ versión
```

Toda funcionalidad deberá comenzar con una necesidad identificada.

Las decisiones importantes deberán registrarse antes o durante la implementación.

---

## 10. Specification-Driven Development

Las funcionalidades se desarrollarán a partir de especificaciones versionadas.

Cada especificación deberá incluir:

* identificador;
* contexto;
* problema;
* alcance;
* fuera de alcance;
* reglas de negocio;
* criterios de aceptación;
* escenarios;
* riesgos;
* dependencias;
* estrategia de pruebas.

El código deberá responder a una especificación existente.

Las especificaciones podrán evolucionar, pero no deberán modificarse silenciosamente para justificar una implementación divergente.

---

## 11. Decisiones arquitectónicas

Las decisiones técnicas significativas deberán documentarse mediante ADR.

Ejemplos:

* elección de monorepo;
* estrategia de autenticación;
* modularidad;
* OpenAPI;
* manejo de configuración;
* estrategia de actualización;
* selección de BLoC;
* estrategia de despliegue.

Las decisiones sobre reglas conceptuales o del dominio de la plataforma podrán documentarse mediante RDR.

---

## 12. Definition of Done

Una funcionalidad se considerará terminada cuando:

* existe una especificación;
* los criterios de aceptación están cubiertos;
* las pruebas pasan;
* el análisis estático pasa;
* los permisos fueron revisados;
* los errores fueron contemplados;
* la documentación fue actualizada;
* las migraciones fueron verificadas;
* el changelog fue actualizado cuando corresponda;
* pasó revisión de código;
* pasó validación funcional cuando corresponde;
* no introduce secretos ni configuraciones locales en el repositorio.

---

## 13. Compatibilidad entre plataformas

El backend será la fuente principal de reglas compartidas y contratos.

El frontend web y Flutter deberán:

* consumir contratos equivalentes;
* utilizar los mismos nombres conceptuales;
* representar de manera consistente estados de error;
* respetar permisos;
* evitar duplicar reglas críticas;
* mantener compatibilidad con la versión de API utilizada.

Una regla de negocio crítica no deberá depender exclusivamente del cliente web o móvil.

---

## 14. Configuración por entornos

La plataforma deberá distinguir al menos:

* desarrollo;
* pruebas;
* staging;
* producción.

Los secretos y datos sensibles no deberán almacenarse en Git.

El repositorio deberá incluir:

```text
.env.example
```

El archivo deberá documentar las variables requeridas sin incluir valores secretos.

---

## 15. Política de dependencias

Una nueva dependencia deberá justificar:

* problema que resuelve;
* madurez;
* mantenimiento;
* licencia;
* impacto de seguridad;
* peso operativo;
* compatibilidad;
* dificultad de sustitución.

No se incorporarán dependencias únicamente para evitar implementar una función pequeña y estable.

Las versiones deberán controlarse explícitamente.

---

## 16. Política de actualización

Los proyectos derivados deberán registrar:

* versión inicial del starter;
* módulos utilizados;
* cambios propios;
* divergencias respecto al núcleo.

Las actualizaciones no deberán aplicarse mediante copia manual indiscriminada.

La estrategia futura podrá utilizar:

* Copier;
* paquetes internos;
* scripts de migración;
* CLI propia;
* generación desde plantillas.

Hasta definir esa estrategia, todo cambio compartido deberá documentarse cuidadosamente.

---

## 17. Propiedad intelectual

El código de la plataforma pertenece a Cognaris.

La plataforma será privada salvo decisión explícita en contrario.

El código desarrollado exclusivamente para un cliente deberá separarse del código reusable.

Antes de incorporar código de un proyecto de cliente al starter deberá verificarse:

* titularidad;
* contrato;
* confidencialidad;
* ausencia de información específica;
* posibilidad real de reutilización.

---

## 18. Criterios para incorporar capacidades al núcleo

Una capacidad podrá incorporarse al núcleo cuando:

* sea utilizada o previsiblemente necesaria en varios proyectos;
* no esté atada a un sector;
* tenga una interfaz clara;
* posea pruebas;
* pueda configurarse;
* tenga costos operativos razonables;
* no fuerce dependencias evitables;
* sea coherente con esta constitución.

En caso contrario deberá permanecer como módulo o como funcionalidad específica de producto.

---

## 19. Gobierno del proyecto

Los cambios a esta constitución deberán:

* realizarse mediante Pull Request;
* incluir una explicación;
* identificar el impacto;
* actualizar la versión del documento;
* ser revisados antes de integrarse.

Las excepciones deberán ser explícitas, temporales y documentadas.

---

## 20. Regla final

Cuando exista duda entre acelerar una implementación aislada o preservar una base reusable, se deberá evaluar el costo total para Cognaris.

La plataforma no debe convertirse en un laboratorio infinito ni en un framework universal.

Debe permitir construir software real, de manera más rápida y con menor deuda técnica.
