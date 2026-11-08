# Sistema de incidencias

Práctica de laboratorio 13: integración continua con GitHub Actions.

## Autor
- **Nombre:** Edward Leon Bustamante
- **Sección:** 20137
- **GitHub:** [darket2210-cpu](https://github.com/darket2210-cpu)
- **Modalidad:** individual, sin compañero.

## Propósito
Validar los datos básicos de una incidencia informática y comprobar automáticamente que los cambios conservan el comportamiento esperado.

## Archivos
- `incidencias.js`: función `validarIncidencia`.
- `test.js`: tres pruebas automatizadas.
- `package.json`: comando `npm test`.
- `.github/workflows/ci.yml`: workflow con Node.js 22.
- `README.md`: procedimiento, resultados y respuestas.

## Procedimiento realizado
1. Creé este repositorio público con README.
2. Incorporé el código y las tres pruebas indicadas en la práctica.
3. Configuré el workflow **Pruebas de incidencias**, activado por `push` y `pull_request`, con `ubuntu-latest`, `actions/checkout@v4`, `actions/setup-node@v4`, Node.js 22 y `npm test`.
4. Verifiqué la primera ejecución: las tres pruebas pasaron.
5. Añadí temporalmente `urgente` a las prioridades permitidas. La prueba **rechaza prioridad desconocida** falló: esperaba `false`, pero la función devolvió `true`.
6. Restauré `['alta', 'media', 'baja']`. Las tres pruebas volvieron a pasar.
7. Conservé el historial de commits y las ejecuciones para verificar el fallo y su corrección. Los commits corresponden a mi cuenta `darket2210-cpu`. La práctica se realizó individualmente, sin invitación a otro colaborador.

## Ejecuciones verificables
| Etapa | Commit | Ejecución | Resultado |
| --- | --- | --- | --- |
| Configuración inicial | `7b7d0bd` | [Actions #1](https://github.com/darket2210-cpu/sistema-incidencias/actions/runs/42436399548) | 3 pasan, 0 fallan |
| Error controlado | `475df4c` | [Actions #2](https://github.com/darket2210-cpu/sistema-incidencias/actions/runs/42436423766) | 2 pasan, 1 falla |
| Corrección | `1cf5931` | [Actions #3](https://github.com/darket2210-cpu/sistema-incidencias/actions/runs/42436507117) | 3 pasan, 0 fallan |

[Historial de commits](https://github.com/darket2210-cpu/sistema-incidencias/commits/main/) · [Todas las ejecuciones](https://github.com/darket2210-cpu/sistema-incidencias/actions)

## Preguntas de reflexión

### ¿Qué evento activa el workflow?
Un `push` al repositorio o un evento de `pull_request` contemplado por GitHub al configurar este disparador, como abrir o actualizar una solicitud.

### ¿Qué verifica la prueba automatizada?
Las tres pruebas verifican que se acepte una incidencia válida, se rechace una prioridad desconocida y se rechace una descripción vacía.

### ¿Qué diferencia existe entre un commit y una ejecución de Actions?
Un commit registra una versión de los archivos en el historial de Git. Una ejecución de Actions procesa el workflow para un evento y commit determinados, ejecuta tareas y registra sus resultados.

### ¿Qué ventaja ofrece detectar un error antes de integrar más cambios?
Permite localizar y corregir la causa cuando el cambio es pequeño, evita propagar defectos y reduce el trabajo de corrección posterior.

## Conclusión
GitHub Actions detectó automáticamente la prioridad no permitida.
La corrección restableció las tres pruebas exitosas.
El historial permite verificar el error y su solución.
