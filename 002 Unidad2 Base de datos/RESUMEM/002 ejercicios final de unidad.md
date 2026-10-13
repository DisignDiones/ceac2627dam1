Subunidad 1:
Ejemplo:
Alumno
	-nombre
  -apellidos
  -fecha_de_nacimiento
  -email
  -telefono


Subunidad 2:
sudo mysql -u root -p

CREATE DATABASE Diones1;
USE Diones1;
SHOW TABLES;

Subunidad 3:
CREATE TABLE alumnos (
    nombre VARCHAR MARIO (100),
    apellidos VARCHAR GODOI (100),
    fecha_de_nacimiento VARCHAR 10/10/1989 (100),
    email VARCHAR MARIO@GMAIL.COM (100),
    telefono VARCHAR99 9666-1001 (100)
);
SHOW TABLES;
DESCRIBE alumnos;

Subunidad 4:
ALTER TABLE alumnos
ADD Identificador INT AUTO_INCREMENT PRIMARY KEY;
DESCRIBE alumnos;
INSERT INTO alumnos VALUES(
	'Jose Vicente',
  'Carratalá Sanchis',
  '1978-04-14',
  '535252354',
  'info@jocarsa.com',
  NULL
);
SELECT * FROM alumnos;

Subunidad 5:
ALTER TABLE alumnos
ADD CONSTRAINT chk_clientes_email
CHECK (
    email IS NULL
    OR email REGEXP '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,}$'
);

Subunidad 6: (nos la saltamos)

Subunidad 7: Claves ajenas
CREATE TABLE asignaturas (
    nombre VARCHAR(100)
);
ALTER TABLE asignaturas
ADD Identificador INT AUTO_INCREMENT PRIMARY KEY;

CREATE TABLE matriculas (
    fecha DATE,
    id_alumno INT,
    id_asignatura INT
);
ALTER TABLE matriculas
ADD Identificador INT AUTO_INCREMENT PRIMARY KEY;

Subunidad 9: Vistas: Pedir algo que involucre a todas las tablas
SELECT 
matriculas.fecha,
alumnos.nombre AS 
alumnos.apellidos,
asignaturas.nombre 
FROM matriculas
LEFT JOIN alumnos ON matriculas.alumno_id = alumnos.Identificador
LEFT JOIN asignaturas ON matriculas.asignatura_id = asignaturas.Identificador;

Subunidad 10:
CREATE USER 'josevicente2627'@'localhost' IDENTIFIED BY 'CEAC123$';
GRANT USAGE ON *.* TO 'josevicente2627'@'localhost';

ALTER USER 'josevicente2627'@'localhost' 
REQUIRE NONE 
WITH MAX_QUERIES_PER_HOUR 0 
MAX_CONNECTIONS_PER_HOUR 0 
MAX_UPDATES_PER_HOUR 0 
MAX_USER_CONNECTIONS 0;

GRANT ALL PRIVILEGES ON empresadam2627.* 
TO 'josevicente2627'@'localhost';

FLUSH PRIVILEGES;


