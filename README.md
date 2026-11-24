# SISTEMA FIT

Gestión de gimnasios con PHP, MySQL/MariaDB y SB Admin.

## Instalación local

1. Instalar XAMPP y colocar este proyecto en `C:\xampp\htdocs\sistema-gym`.
2. Iniciar Apache y MySQL desde el panel de XAMPP.
3. Revisar `config.php`: por defecto se conecta a MySQL en `127.0.0.1:3306`, con usuario `root`, sin contraseña y base de datos `sistema_gym`.
4. Abrir PowerShell en la carpeta del proyecto y ejecutar el instalador con el PHP de XAMPP:

   ```powershell
   C:\xampp\php\php.exe instalar.php
   ```

5. El instalador crea la base de datos y las tablas. Cuando solicite los datos de la cuenta, ingresar:

   | Campo | Valor |
   | --- | --- |
   | Nombre | Administrador Demo |
   | Rol | `administrador` |
   | Usuario | `44529770` |
   | Contraseña | `1234` |

6. Con Apache configurado en el puerto **8080**, abrir [el sistema en localhost](http://localhost:8080/sistema-gym/).

## Acceso de demostración

### Administrador

- **Usuario:** `44529770`
- **Contraseña:** `1234`

### Alumno

- **Usuario:** `123456789`
- **Contraseña:** `1234`

Para usar estos accesos, las cuentas deben existir en la base de datos con las contraseñas indicadas. En una instalación nueva, crear el administrador con los datos del paso 5; luego dar de alta al alumno con DNI `123456789` y cambiar su contraseña inicial a `1234` desde su perfil. Descargar el repositorio no crea usuarios automáticamente ni incluye la base de datos local del autor. Editar este README tampoco modifica las contraseñas del sistema.

Estas credenciales son públicas y están destinadas a pruebas locales. Para una instalación real, usar contraseñas propias.

GitHub aloja el código del proyecto. Para usar este sistema PHP con MySQL hay que instalarlo localmente o desplegarlo en un servidor compatible; GitHub Pages no ejecuta PHP.

Para actualizar los módulos de una instalación existente, ejecutar `C:\xampp\php\php.exe actualizar.php`. Este comando no crea la cuenta de demostración.

## Organización

- PHP en la raíz: pantallas y lógica compartida, con sus rutas actuales.
- assets/img/: logo de la aplicación.
- css/: plantilla SB Admin y ajustes propios.
- js/: menú lateral y fechas de rutinas.
- docs/: estructura y notas históricas.
- tests/: pruebas de integración, bloqueadas para acceso web.
- login.html: redirección de compatibilidad a login.php.

## Funciones

Administrador: alumnos, usuarios, cuotas manuales, rutinas, horarios y cupos, clases por fecha y avisos con texto enriquecido e imágenes.

Alumno: dashboard, perfil, cambio de contraseña, cuota, rutinas, avisos y reservas/cancelaciones semanales.

El alta de alumnos usa su DNI como usuario y contraseña inicial. El alumno puede cambiar la contraseña.
Las imágenes de avisos se almacenan en MySQL y se consultan con sesión iniciada.

## Verificación

Las pruebas en tests se ejecutan con PHP CLI y requieren MySQL y Apache en el puerto 8080.
Usan datos temporales que retiran al finalizar. No son necesarias para servir la aplicación.
Los scripts integracion.php y alumnos-datos.php contienen flujos anteriores al acceso automático con DNI y requieren adaptación antes de utilizarlos como validación completa.

Se retiraron las páginas y scripts de demostración que no usa el sistema. La base de datos y los módulos funcionales se conservaron.
