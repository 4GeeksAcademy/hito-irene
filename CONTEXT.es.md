# Contexto de tu empresa: HealthCore

## 1. Resumen Ejecutivo y Diagnóstico

- **Empresa:** HealthCore (Servicios de Salud Ambulatoria fundada en 2011).
- **Alcance:** 12 clínicas en total: 9 en EE. UU. (Texas, Florida, Georgia) y 3 en el Reino Unido (Londres, Manchester).
- **Tamaño e Ingresos:** ~200 empleados y ~$28M USD en ingresos anuales.
- **Problema Principal:** La infraestructura tecnológica no ha crecido a la par de la empresa. Existen sistemas de historias clínicas electrónicas (HCE) fragmentados entre EE. UU. y el Reino Unido que no se comunican, una tasa de inasistencia a citas del 22% ($1.8M anuales en pérdidas), un 14% de denegación de reclamaciones de facturación en EE. UU., registros manuales en hojas de cálculo y falta de visibilidad en tiempo real para el equipo ejecutivo.
- **Objetivo del Sistema (HealthCore Digital):** Desarrollar una capa unificada de datos (API central), herramientas automatizadas e inteligencia artificial para optimizar la documentación clínica, predecir ausencias, mejorar el ciclo de facturación, supervisar el cumplimiento (HIPAA/RGPD) y dotar a la dirección ejecutiva de un panel de control unificado.

---

## 2. Departamentos y Problemáticas Específicas

| Departamento                          | Lider / Responsable                 | Problemática Clave                                                                                                                                                                        |
| :------------------------------------ | :---------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Operaciones Clínicas**              | Dr. Marcus Reid (~120 clínicos)     | Sistemas de HCE incompatibles entre EE. UU. y Reino Unido. 35 minutos diarios por clínico perdidos en papeleo manual. Falta de portabilidad del historial al cambiar de centro.           |
| **Experiencia y Acceso del Paciente** | Priya Nair (Londres)                | Sin reservas en línea unificadas. Tasa de inasistencia del 22% ($1.8M anuales perdidos) y falta de recordatorios o seguimientos proactivos.                                               |
| **Ciclo de Ingresos y Facturación**   | Tom Callahan                        | Tasa de rechazo de reclamaciones del 14% en EE. UU. (promedio del sector es 5-8%). Prácticas de codificación inconsistentes y gestión separada de facturación NHS/privada en Reino Unido. |
| **Cumplimiento y Gobernanza**         | Claire Whitfield                    | Operación bajo HIPAA (EE. UU.) y RGPD (Reino Unido) con registros de auditoría y acceso dispersos. Responder a solicitudes de datos de pacientes requiere trabajo manual intensivo.       |
| **Personas y Fuerza Laboral**         | Diane Foster                        | Proceso de contratación clínica lento (47 días). Seguimiento de formación médica continua (FMC) llevado manualmente en hojas de cálculo.                                                  |
| **Tecnología**                        | James Osei (Director de TI, Austin) | Mosaico de sistemas heredados sin capa de datos unificada, telemetría o alertas centralizadas. Los fallos se detectan solo cuando las clínicas llaman por teléfono.                       |
| **Liderazgo Ejecutivo**               | Dra. Sandra Okonkwo (CEO)           | Sin visión en tiempo real del negocio. Reportes semanales inconsistentes, manuales y desfasados por días. Imposibilidad de responder métricas básicas sin llamadas telefónicas.           |

---

## 3. Personajes y Stakeholders Principales

- **Dra. Sandra Okonkwo (CEO):** Busca un panel ejecutivo unificado en tiempo real con reportes automáticos semanales y asistencia en lenguaje natural para toma de decisiones.
- **Dr. Marcus Reid (Dir. Operaciones Clínicas):** Requiere una API unificada de HCE, asistencia de IA para notas clínicas y panel de flujo de pacientes.
- **Priya Nair (Gerente de Experiencia):** Necesita plataforma de reservas unificada, recordatorios multicanal (SMS/Email/App) y modelos predictivos para ausencias.
- **Tom Callahan (Gerente de Facturación):** Busca revisión de reclamaciones asistida por IA, sugerencia automática de códigos médicos y analítica de denegaciones.
- **Claire Whitfield (Gerente de Cumplimiento):** Exige un panel centralizado de cumplimiento normativo (HIPAA/RGPD), logs de auditoría unificados y automatización de solicitudes de datos (DSAR).
- **Diane Foster (Gerente de RR. HH.):** Requiere portal de empleados, seguimiento automatizado de FMC/licencias y chatbot para preguntas frecuentes.
- **James Osei (CTO):** Necesita API central de HealthCore, monitoreo en tiempo real, pipeline de datos y documentación técnica indexada para búsqueda semántica.

---

## 4. Estructura de Datos y Entidades Principales

1. **Pacientes (`Patients`):** ID, Nombre, Fecha de Nacimiento, Contacto, Jurisdicción (US/UK), Historial y Consentimientos HIPAA/RGPD.
2. **Citas (`Appointments`):** ID, Paciente_ID, Clínica_ID, Médico_ID, Fecha/Hora, Estado (Confirmada, Cancelada, No-show), Riesgo de Inasistencia (IA score).
3. **Historial Clínico (`ClinicalRecords`):** ID, Paciente_ID, Nota Médica, Transcripción IA, Diagnósticos (CIE-10/11), Tratamientos.
4. **Reclamaciones y Facturación (`Claims`):** ID, Cita_ID, Código_Procedimiento (CPT), Estado (Enviado, Aprobado, Rechazado), Motivo de Rechazo, Riesgo de Rechazo (IA score).
5. **Auditoría y Cumplimiento (`AuditLogs`):** ID, Usuario_ID, Acción, Sistema_Origen, Marca de Tiempo, Norma (HIPAA / RGPD).
6. **Personal (`Staff`):** ID, Nombre, Rol, Clínica_ID, Estado de Licencia FMC, Días de Incapacidad/Vacaciones.

---

## 5. Casos de Uso e Integraciones con IA

1. **Documentación Clínica con IA:** Asistencia de PNL/LLMs para resumir consultas médicas y reducir el tiempo administrativo de 35 min/día.
2. **Predicción de Inasistencias (No-Shows):** Modelo predictivo entrenado con datos de citas para identificar visitas de alto riesgo y activar recordatorios automáticos.
3. **Sugerencia de Codificación y Auditoría de Facturación:** Sistema de IA que escanea notas clínicas, sugiere códigos de facturación correctos y detecta errores en reclamaciones antes del envío para reducir la tasa de rechazo del 14%.
4. **Búsqueda Semántica de Cumplimiento (RAG):** Asistente RAG para responder dudas sobre normativas HIPAA/RGPD y consolidar logs de auditoría.
