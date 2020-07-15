# Tarea
INDEX
<?php
include_once('utilities.php');
include_once('db/database_utilities.php');
$result = run_query()

?>
<!doctype html>
<html class="no-js" lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Curso PHP |  Bienvenidos</title>
    <link rel="stylesheet" href="./css/foundation.css" />
    <script src="./js/vendor/modernizr.js"></script>
  </head>
  <body>
    
    <?php require_once('header.php'); ?>

     
    <div class="row">
 
      <div class="large-9 columns">
        <h3>Manejo de base de datos</h3>
          <p>Listado</p>
        <div class="section-container tabs" data-section>
          <section class="section">
            <div class="content" data-slug="panel1">
              <div class="row">
              </div>
              <table>
                <thead>
                  <tr>
                    <th>Nombre</th>
                    <th>DNI</th>
                    <th>Direccion</th>
                    <th>Telefono</th>
                    <th>Observaciones</th>
                    <th>Correo</th>
                  </tr>
                </thead>
                <tbody>
                  <?php 
                  while($user = $result->fetch_assoc())
                  {
                  ?>
                  <tr>
                    <td><?php echo $user['ID']; ?></td>
                    <td><?php echo $user['Nombre']; ?></td>
                    <td><?php echo $user['DNI']; ?></td>
                    <td><?php echo $user['Dirección']; ?></td>
                    <td><?php echo $user['Teléfono']; ?></td>
                    <td><?php echo $user['Observaciones']; ?></td>
                  </tr>
                  <?php
                  }
                  ?>
                </tbody>

              </table>
            </div>
          </section>
        </div>
      </div>
    

    <?php require_once('footer.php'); ?>
    
    DATABASE_CREDENTIALES
    <?php
define('DB_HOST', 'localhost');
define('DB_DATABASE', 'tarea');
define('DB_USER', 'root');
define('DB_PASSWORD', '');
?>

  DATABASE_UTILITIES
  <?php
require_once('database_credentials.php');
$mysqli = new mysqli(DB_HOST,DB_USER,DB_PASSWORD,DB_DATABASE);
$result = '';

//Verifica la conexion con la base de datos, Si no conecta bota un mensaje de error y sale
if( $mysqli->connect_errno )
{
	echo 'Error en la conexión';
	exit;
}

//corre la consulta
function run_query()	
{
	global $mysqli, $result;
	$sql = 'SELECT * FROM user';
	return $mysqli->query($sql);
}
?>
