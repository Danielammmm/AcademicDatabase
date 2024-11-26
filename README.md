# AcademicDatabase
# **Sistema de Gestión Académica**

## **Descripción**
Este proyecto implementa un sistema de base de datos diseñado para gestionar estudiantes, cursos, secciones y prerrequisitos en una institución educativa. Incluye funciones y procedimientos almacenados para automatizar tareas comunes, como verificar prerrequisitos y gestionar cupos en secciones.

## **Estructura del proyecto**
El sistema se compone de los siguientes elementos principales:
- **Tablas:** Estructura relacional definida en el script `DDL.sql`.
- **Inserciones:** Población inicial de datos en `inserts.sql`.
- **Funciones:** Scripts para cálculos específicos, como:
  - `fncEstudianteCumplePrerrequisitos.sql`: Verifica si un estudiante cumple los prerrequisitos de un curso.
  - `fncObtenerCantidadEstudiantesSeccion.sql`: Obtiene el número de estudiantes inscritos en una sección.
- **Procedimientos almacenados:**
  - `SP.sql`: Proceso general para la gestión académica.
  - `SP_CambioCupos.sql`: Permite realizar cambios en los cupos de las secciones.
- **Consultas de control:** Incluidas en `TableroControl.sql` para analizar el estado de las inscripciones.

## **Componentes principales**
### **Tablas**
El sistema incluye las siguientes tablas con sus atributos principales:
- **Estudiante:**
  - `idEstudiante` (PK), `nombre`, `fechaNacimiento`, `correo`.
- **Curso:**
  - `idCurso` (PK), `nombre`, `creditos`, `prerrequisitos`.
- **Sección:**
  - `idSeccion` (PK), `idCurso` (FK), `cupos`, `horario`.
- **Inscripción:**
  - `idInscripcion` (PK), `idEstudiante` (FK), `idSeccion` (FK).

### **Funciones destacadas**
- **`fncEstudianteCumplePrerrequisitos`:**
  Verifica si un estudiante tiene aprobados los cursos necesarios para inscribirse en un nuevo curso.
  ```sql
  SELECT dbo.fncEstudianteCumplePrerrequisitos(@idEstudiante, @idCurso);
