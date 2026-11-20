# 🏢 StayFlow PMS — Sistema de Gestión de Alquileres Temporarios

Aplicación web *full-stack serverless* diseñada para centralizar la operación diaria, el registro legal de huéspedes (*check-in*) y el control financiero de propiedades de alquiler temporario en Posadas, Misiones.

## 🎯 Problema Resuelto
La administración mediante planillas estáticas generaba duplicación de datos de clientes recurrentes, riesgo de superposición de fechas (*overbooking*), dificultad para gestionar extensiones de estadía o salidas tardías (*late check-out*) y cálculos manuales en la liquidación de comisiones. **StayFlow PMS** unifica el CRM de huéspedes, la validación de disponibilidad horaria en tiempo real y la emisión de fichas de ingreso imprimibles desde dispositivos móviles.

## 🛠️ Stack Tecnológico
* **Frontend:** HTML5, CSS3 (Grid/Flexbox responsivo *mobile-first*), JavaScript Vanilla (ES6+ Async/Await).
* **Backend & Base de Datos:** PostgreSQL en la nube mediante **Supabase** (BaaS / API REST).
* **Despliegue:** **Netlify** (CI/CD y configuración como Web App en iOS).

## ✨ Funcionalidades Principales
* **Detección de Conflictos y Alertas de Recambio:** Validación automática de solapamiento de fechas (`checkin < checkout_existente AND checkout > checkin_existente`) y alertas preventivas cuando una reserva posee *Late Check-out* (`> 10:00 hs`) el mismo día de un nuevo ingreso.
* **CRM y Autocompletado Incremental:** Búsqueda en tiempo real sobre el historial de huéspedes por nombre, teléfono o DNI, autocompletando fichas de clientes recurrentes.
* **Extensión Dinámica de Estadías:** Recálculo automático de noches, tarifas diferenciales por ocupación extra, cargos por horas adicionales y ajuste proporcional de comisiones pendientes.
* **Registro Legal y Documentación A4:** Almacenamiento de titulares y lista flexible de acompañantes mediante tipo de dato semiestructurado **`JSONB`** en PostgreSQL, con generación de ficha imprimible para firma física o PDF.
* **Panel Financiero y Auditoría:** Seguimiento separado entre facturación de propiedades, saldos pendientes de huéspedes y comisiones cobradas vs. pendientes de liquidación, con exportación mensual a **CSV**.

## 🗄️ Arquitectura de Datos
El modelo relacional (`schema.sql`) consta de dos entidades principales vinculadas mediante clave foránea (`huesped_id`):
1. `huespedes`: Maestro único de clientes con datos de contacto, documento y domicilio.
2. `reservas`: Registro transaccional de estadías, horarios de egreso, estados de pago, liquidación granular de comisiones y arreglo `JSONB` de acompañantes.

## 🚀 Instalación y Despliegue Local
1. Clonar el repositorio:
   ```bash
   git clone [https://github.com/TU-USUARIO/stayflow-pms.git](https://github.com/TU-USUARIO/stayflow-pms.git)
