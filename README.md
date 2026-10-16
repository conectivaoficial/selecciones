Drop table if exists Heroe_Mision;
Drop table if exists Misiones;
Drop table if exists Heroes;
Drop table if exists Bases;

-- Crear tablas
CREATE TABLE if not exists Bases (
    id_base INT PRIMARY KEY,
    nombre_base VARCHAR(50),
    ciudad VARCHAR(50),
    presupuesto DECIMAL(10,2)
);

CREATE TABLE if not exists Heroes(
    id_hero INT PRIMARY KEY,
    nombre_heroe VARCHAR(50),
    alias_real VARCHAR(50),
    poder_principal VARCHAR(50),
    nivel_fuerza INT,
    id_base INT,
    FOREIGN KEY (id_base) REFERENCES Bases(id_base)
);

CREATE TABLE if not exists Misiones(
    id_mision INT PRIMARY KEY,
    nombre_mision VARCHAR(50),
    nivel_peligro VARCHAR(20),
    recompensa DECIMAL(10,2)
);

CREATE TABLE if not exists Heroe_Mision(
    id_hero INT,
    id_mision INT,
    horas_invertidas INT,
    PRIMARY KEY (id_hero, id_mision),
    FOREIGN KEY (id_hero) REFERENCES Heroes(id_hero),
    FOREIGN KEY (id_mision) REFERENCES Misiones(id_mision)
);

-- Insertar Bases
INSERT INTO Bases VALUES (1, 'Torre Central', 'Nueva York', 500000.00);
INSERT INTO Bases VALUES (2, 'Base Submarina', 'Atlantis', 300000.00);
INSERT INTO Bases VALUES (3, 'Laboratorio Secreto', 'Tokio', 200000.00);
INSERT INTO Bases VALUES (4, 'Cuartel Abandonado', 'Gotham', 50000.00);

-- Insertar Héroes
INSERT INTO Heroes VALUES (1, 'Rayo Veloz', 'Barry Allen', 'Supervelocidad', 90, 1);
INSERT INTO Heroes VALUES (2, 'Capitán Acero', 'Clark Kent', 'Superfuerza', 99, 1);
INSERT INTO Heroes VALUES (3, 'Señor de las Olas', 'Arthur Curry', 'Control del agua', 85, 2);
INSERT INTO Heroes VALUES (4, 'Sombra Silenciosa', 'Bruce Wayne', 'Artes Marciales', 75, 4);
INSERT INTO Heroes VALUES (5, 'Mente Brillante', 'Tony Stark', 'Tecnología', 80, 3);
INSERT INTO Heroes VALUES (6, 'Defensor Nuevo', 'Desconocido', 'Telepatía', 60, NULL); -- Sin base asignada para probar Left Join

-- Insertar Misiones
INSERT INTO Misiones VALUES (101, 'Detener Robo al Banco', 'Bajo', 1500.00);
INSERT INTO Misiones VALUES (102, 'Salvar la Ciudad de Inundación', 'Alto', 10000.00);
INSERT INTO Misiones VALUES (103, 'Desactivar Bomba', 'Crítico', 25000.00);
INSERT INTO Misiones VALUES (104, 'Rescatar Gato en Árbol', 'Bajo', 100.00);

-- Insertar Relaciones Héroe - Misión
INSERT INTO Heroe_Mision VALUES (1, 101, 2);
INSERT INTO Heroe_Mision VALUES (1, 103, 5);
INSERT INTO Heroe_Mision VALUES (2, 102, 10);
INSERT INTO Heroe_Mision VALUES (2, 103, 8);
INSERT INTO Heroe_Mision VALUES (3, 102, 12);
INSERT INTO Heroe_Mision VALUES (4, 101, 3);




/*

TALLER PRÁCTICO DE BASES DE DATOS (SQL)

Tema: Consultas de selección, ordenamiento, filtrado, agregación y uniones de tablas

Instrucciones Generales
•	Lee atentamente cada requerimiento antes de escribir tu consulta.
•	Para cada uno de los puntos, analiza la información solicitada e identifica la estrategia y cláusula SQL adecuada (WHERE, ORDER BY, GROUP BY, INNER JOIN, LEFT JOIN, funciones de agregación (Min, Max, Count, Sum, Avg)) para construir la respuesta.
•	Cada consulta debe retornar exactamente la información que se pide en el enunciado.
*/

--Sección 1: Filtrado y Ordenamiento de Datos
--1.	Muestra el nombre y el nivel de fuerza de todos los héroes donde el nivel de fuerza sea estrictamente mayor a 80. Los resultados deben aparecer ordenados desde el héroe más fuerte hasta el más débil.


--2.	Muestra el nombre y el nivel de peligro de todas las misiones donde el nivel de peligro sea 'Bajo' o 'Medio'.


--Sección 2: Funciones de Agregación y Resumen
--3.	Calcula e informa cuántas misiones en total se encuentran registradas en la base de datos.


--4.	Muestra la suma total del dinero ofrecido como recompensa entre todas las misiones disponibles.


--5.	Obtén en una misma consulta el nivel de fuerza más alto (máximo) y el nivel de fuerza más bajo (mínimo) registrados entre todos los héroes.

--Sección 3: Agrupación de Información

--6.	Muestra cada nivel de peligro existente en las misiones y cuántas misiones hay asociadas a cada uno de esos niveles.


--7.	Muestra el identificador de cada base (id_base) y la cantidad total de héroes que tiene asignados cada una excluyendo los héroes que no tienen base  (IS NOT NULL).


--Sección 4: Relaciones entre Tablas (Joins)

--8.	Muestra el nombre de cada héroe junto con el nombre de su base y la ciudad donde se ubica. Solo deben aparecer aquellos héroes que tengan una base asignada.


--9.	Genera un listado con todos los héroes registrados en la base de datos y el nombre de su base correspondiente. Importante: Deben aparecer en la lista incluso aquellos héroes que no tienen ninguna base asignada (mostrando valor nulo en el nombre de la base).


--10.	Consulta el nombre del héroe, el nombre de la misión en la que participa y las horas invertidas en dicha misión.


--11.	Muestra el nombre del héroe, el nombre de la misión y las horas invertidas, pero únicamente para aquellas misiones donde la clasificación de peligro sea 'Alto' o 'Crítico' (IN). Ordena los resultados de mayor a menor según las horas invertidas. (Bonus)

