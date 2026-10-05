# Lista de Pruebas de Permisos

## 1. Información Clínica (Historia clínica, Diagnósticos, Resultados)

### PR-01 (Denegada) - [IMPRESCINDIBLE]
* **Cuenta:** Personal de Administración
* **Acción:** Solicitar la historia clínica, diagnóstico o resultados de un paciente
* **Resultado esperado:** El servidor rechaza la petición con error `403 Forbidden`

### PR-01b (Pareja Permitida)
* **Cuenta:** Profesional sanitario con relación asistencial activa con el paciente
* **Acción:** Solicitar la historia clínica, diagnóstico o resultados del paciente
* **Resultado esperado:** El servidor devuelve la información clínica (`200 OK`)

---

### PR-02 (Denegada) - [IMPRESCINDIBLE]
* **Cuenta:** Profesional sanitario sin vínculo asistencial directo con el paciente
* **Acción:** Solicitar la historia clínica, diagnóstico o resultados de dicho paciente
* **Resultado esperado:** El servidor rechaza la petición con error `403 Forbidden`

### PR-02b (Pareja Permitida)
* **Cuenta:** Profesional sanitario con vínculo asistencial directo activo con el paciente
* **Acción:** Consultar o modificar la historia clínica, diagnóstico o resultados de dicho paciente
* **Resultado esperado:** El servidor permite la lectura/escritura (`200 OK` / `204 No Content`)

---

### PR-03 (Denegada) - [IMPRESCINDIBLE]
* **Cuenta:** Alumno en prácticas sin tutoría activa o en consulta no tutelada
* **Acción:** Solicitar la lectura de la historia clínica, diagnóstico o resultados
* **Resultado esperado:** El servidor rechaza la petición con error `403 Forbidden`

### PR-03b (Pareja Permitida)
* **Cuenta:** Alumno en prácticas con tutoría activa y mediante consulta tutelada
* **Acción:** Consultar la historia clínica, diagnóstico o resultados
* **Resultado esperado:** El servidor permite la lectura (`200 OK`)

---

### PR-04 (Denegada) - [IMPRESCINDIBLE]
* **Cuenta:** Alumno en prácticas
* **Acción:** Intentar crear, modificar o borrar cualquier tipo de dato en el sistema
* **Resultado esperado:** El servidor rechaza la petición con error `403 Forbidden`

---

### PR-05 (Denegada) - [IMPRESCINDIBLE]
* **Cuenta:** Paciente autenticado
* **Acción:** Solicitar la historia clínica, diagnóstico o resultados de otro paciente
* **Resultado esperado:** El servidor rechaza la petición con error `403 Forbidden`

### PR-05b (Pareja Permitida)
* **Cuenta:** Paciente autenticado
* **Acción:** Consultar su propia historia clínica, diagnóstico o resultados
* **Resultado esperado:** El servidor devuelve su información personal (`200 OK`)

---

## 2. Datos de Usuario y Contenidos

### PR-06 (Denegada)
* **Cuenta:** Editor de contenidos
* **Acción:** Consultar o modificar datos personales o clínicos de cualquier usuario
* **Resultado esperado:** El servidor rechaza la petición con error `403 Forbidden`

### PR-06b (Pareja Permitida)
* **Cuenta:** Editor de contenidos
* **Acción:** Leer y editar contenidos generales del portal
* **Resultado esperado:** El servidor permite la lectura y escritura (`200 OK`)

---

## 3. Administración y Auditoría

### PR-07 (Denegada) - [IMPRESCINDIBLE]
* **Cuenta:** Administrador del sistema
* **Acción:** Consultar o modificar datos clínicos, citas, cuentas o contenidos del portal
* **Resultado esperado:** El servidor rechaza la petición con error `403 Forbidden`

### PR-07b (Pareja Permitida)
* **Cuenta:** Administrador del sistema
* **Acción:** Solicitar la lectura de los registros de auditoría
* **Resultado esperado:** El servidor devuelve los registros de auditoría (`200 OK`)

---

### PR-08 (Denegada) - [IMPRESCINDIBLE]
* **Cuenta:** Cualquier rol del sistema (incluido Administrador)
* **Acción:** Intentar modificar o eliminar un registro de auditoría
* **Resultado esperado:** El servidor rechaza la petición con error `403 Forbidden` o `405 Method Not Allowed`