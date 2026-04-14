💰 MoneyHome - Sistema de Finanzas del Hogar

📌 Descripción
MoneyHome es una aplicación web desarrollada en Python con Flask que permite a los usuarios registrar y gestionar sus ingresos y gastos del hogar, visualizar su saldo y organizar sus movimientos mediante categorías.

⚙️ Requisitos
Antes de ejecutar el sistema, asegúrate de tener instalado:

- Python 3
- MySQL Server
- MySQL Workbench (opcional)
- Visual Studio Code

🧱 Configuración de la Base de Datos

1. Iniciar MySQL
- Abrir MySQL Workbench
- Conectarse a Local instance MySQL80
- Ingresar contraseña del usuario root

2. Crear la base de datos

CREATE DATABASE moneyhome;
USE moneyhome;

CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    password VARCHAR(255)
);

CREATE TABLE categorias (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100)
);

CREATE TABLE tipo_movimiento (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50)
);

CREATE TABLE movimientos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    usuario_id INT,
    monto DECIMAL(10,2),
    categoria_id INT,
    tipo_id INT,
    fecha DATE,
    descripcion TEXT,
    FOREIGN KEY (usuario_id) REFERENCES usuarios(id),
    FOREIGN KEY (categoria_id) REFERENCES categorias(id),
    FOREIGN KEY (tipo_id) REFERENCES tipo_movimiento(id)
);

3. Insertar datos iniciales

INSERT INTO categorias (nombre) VALUES
('Alimentación'),
('Transporte'),
('Ocio'),
('Salud'),
('Otros');

INSERT INTO tipo_movimiento (nombre) VALUES
('ingreso'),
('gasto'),
('transferencia');

⚠️ IMPORTANTE (ERROR 1175 MYSQL)

Si aparece este error al hacer UPDATE:

Error Code: 1175 (safe update mode)

Ejecutar antes:

SET SQL_SAFE_UPDATES = 0;

🔌 Configuración del Proyecto

1. Abrir proyecto en VS Code
2. Abrir terminal (Terminal → New Terminal)
3. Instalar dependencias

pip install flask mysql-connector-python

▶️ Ejecución del Sistema

1. Verificar conexión en app.py

def get_db_connection():
    return mysql.connector.connect(
        host="localhost",
        user="root",
        password="TU_PASSWORD",
        database="moneyhome"
    )

2. Ejecutar la aplicación

python app.py

3. Abrir en el navegador

http://127.0.0.1:5000

🔐 Funcionalidades

- Registro de usuario
- Inicio de sesión
- Registro de ingresos y gastos
- Clasificación por categorías
- Visualización de movimientos
- Cálculo automático de saldo
- Dashboard con resumen financiero

🧪 Notas

- MySQL debe estar en ejecución
- No es necesario mantener abierto MySQL Workbench
- Proyecto utiliza servidor de desarrollo Flask

🚀 Estado del Proyecto

Versión actual: MVP (Producto Mínimo Viable)

Incluye funcionalidades base con estructura escalable de base de datos.

👨‍💻 Autores

- Daniel Neculman
- Paula Matamala

📌 Observaciones

El sistema fue desarrollado con fines académicos, aplicando conceptos de desarrollo web, bases de datos relacionales y metodologías ágiles.
