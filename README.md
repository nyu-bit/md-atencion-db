CREATE DATABASE atencion;
USE atencion;

CREATE TABLE tickets (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    cliente_id BIGINT NOT NULL,
    pedido_id BIGINT,
    asunto VARCHAR(200) NOT NULL,
    descripcion VARCHAR(1000),
    estado VARCHAR(20) NOT NULL,
    fecha_creacion DATETIME NOT NULL,
    fecha_cierre DATETIME
);

CREATE TABLE mensajes_ticket (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    ticket_id BIGINT NOT NULL,
    remitente VARCHAR(20) NOT NULL,
    mensaje VARCHAR(1000) NOT NULL,
    fecha_mensaje DATETIME NOT NULL,
    FOREIGN KEY (ticket_id) REFERENCES tickets(id)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);

CREATE TABLE resoluciones_ticket (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    ticket_id BIGINT NOT NULL,
    descripcion VARCHAR(1000),
    usuario_resolutor VARCHAR(100),
    fecha_resolucion DATETIME NOT NULL,
    FOREIGN KEY (ticket_id) REFERENCES tickets(id)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);
