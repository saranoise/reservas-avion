DROP DATABASE IF EXISTS reservas_vuelos;

CREATE DATABASE reservas_vuelos CHARACTER SET utf8;

USE reservas_vuelos;

SET default_storage_engine=INNODB;

drop table if exists ciudad;
create table ciudad (
    id_ciudad   smallint(6) primary key NOT NULL AUTO_INCREMENT,
    nombre  varchar(30) NOT NULL,
    país    varchar(30) NOT NULL
);

drop table if exists aeropuerto;
create table aeropuerto (
    cod_aeropuerto  char(3) primary key NOT NULL,#el código de aeropuertos es de 3 letras y no es único, pero como es un trabajo con fechas, no voy a hacer florituras.
    nombre  varchar(30) NOT NULL,
    categoria   integer NOT NULL,
    id_ciudad   smallint(6) NOT NULL
);

drop table if exists aerolinea;
create table aerolinea (
    cod_aerolinea   char(3) primary key NOT NULL,#lo mismo que arriba
    nombre  varchar(20) NOT NULL 
);

drop table if exists vuelo_generico;
create table vuelo_generico (
    num_vuelo   smallint(6) primary key NOT NULL AUTO_INCREMENT,
    hora_salida char(5) NOT NULL,
    hora_llegada char(5) NOT NULL,
    precio  float(6,2) NOT NULL,
    capacidad   integer NOT NULL,
    cod_aerolinea char(3),
    cod_aeropuerto_salida char(3) NOT NULL,
    cod_aeropuerto_llegada char(3) NOT NULL
);

drop table if exists vuelo;
create table vuelo (
    id_vuelo   smallint(6) primary key NOT NULL AUTO_INCREMENT,
    fecha char(8) NOT NULL,
    plazas_libres   integer NOT NULL,
    num_vuelo   smallint(6) NOT NULL
);


drop table if exists reserva;
create table reserva (
    num_reserva smallint(6) primary key NOT NULL AUTO_INCREMENT,
    nombre  varchar(30) NOT NULL,
    apellidos   varchar(40) NOT NULL,
    telefono    char(9) NOT NULL,
    tarjeta char(16) NOT NULL,
    importe float(6,4) NOT NULL,
    id_vuelo smallint(6) NOT NULL

);

ALTER TABLE aeropuerto 
ADD CONSTRAINT fk_ciudad_aeropuerto
FOREIGN KEY (id_ciudad)
REFERENCES ciudad(id_ciudad);

ALTER TABLE vuelo_generico 
ADD CONSTRAINT fk_aerolinea_vueGenerico
FOREIGN KEY (cod_aerolinea)
REFERENCES aerolinea(cod_aerolinea);

ALTER TABLE vuelo_generico 
ADD CONSTRAINT fk_aeropuerto_vueGenerico_salida
FOREIGN KEY (cod_aeropuerto_salida)
REFERENCES aeropuerto(cod_aeropuerto);

ALTER TABLE vuelo_generico 
ADD CONSTRAINT fk_aeropuerto_vueGenerico_llegada
FOREIGN KEY (cod_aeropuerto_llegada)
REFERENCES aeropuerto(cod_aeropuerto);

ALTER TABLE vuelo
ADD CONSTRAINT fk_vueGenerico_vuelo
FOREIGN KEY (num_vuelo)
REFERENCES vuelo_generico(num_vuelo);


ALTER TABLE reserva
ADD CONSTRAINT fk_vuelo_reserva
FOREIGN KEY (id_vuelo)
REFERENCES vuelo(id_vuelo);