# Funcion-TinCar
Presentación de una funcion ejecutada en nuestra base de datos del proyecto
# Explicación:
Crea una nueva tabla llamada registros_parqueader donde se define una columna cedula como clave primaria,
Definimos una columna idParqueadero y una columna fecha para registrar la fecha y hora de uso del parqueadero.

  CREATE TABLE RegistroParqueadero(
  	 
       Cedula int PRIMARY KEY,
       idParqueadero int,
       fecha DATETIME 
       );

 # Creación de función 
 
    CREATE FUNCTION ContarConductores(idParqueadero INT)
    RETURNS INT
    DETERMINISTIC
    BEGIN
    	DECLARE conteo INT;
        SELECT COUNT(DISTINCT Cedula) INTO CONTEO
        FROM RegistroParqueadero
        WHERE idParqueadero = idParqueadero;
        RETURN conteo;
        
    END //
    
    DELIMITER ;


Usamos DELIMITER //: Cambia el delimitador para permitir el uso de ; dentro de la función. posterior a esto usamo: CREATE FUNCTION contarConductores(idParqueadero INT) que define la función contarConductores que toma un parámetro idParqueadero.
Usaremos RETURNS INT que especifica que la función devuelve un entero y posterior usamos DECLARE conteo INT que declara una variable conteo para almacenar el resultado.
Ahora con SELECT COUNT(DISTINCT cedula) INTO conteo que Cuenta los conductores únicos que han usado el parqueadero específico.
Usamos RETURN conteo que devuelve el conteo.


# Uso de la función:
Para usar esta función se ejecuta la siguiente consulta:

  SELECT ContarConductores (1);
