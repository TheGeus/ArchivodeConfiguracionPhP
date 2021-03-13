function lecturaArchivo()
{ //comprobacion de si se ha iniciado datos en la session y si no, la creamos
    $fp = fopen("./config2.conf", "r") //ubucacion del archivo
    or die ("no existe el archivo de configuracion"); //si no existe
    $datos = []; //donde guardaremos los datos
    while (!feof($fp)) {
        $linea = fgets($fp);
        $datos[] = preg_split("~=~", $linea); //expresion regular para delimitar donde cortaremos la linea (el resultado sera en varias partes partes ejemplo [0]=> hola [1]=como estas [2] bien
    }
    fclose($fp);
    //filtrado
    $newArray = array(); //array final para utilizar los datos ya filtrados
    for ($i = 0; $i < count($datos); $i++) {
        $contador = 0; //contador de datos por linea
        $aux = []; // array auxilizar para posteriormente pasarlo al array final
        for ($j = 0; $j < 3; $j++) { //3 ciclos 
            if (empty($datos[$i][1])) { //si la linea 1 parte 2 esta vacia borramos el array auxiliar y salimos del bucle.
                $aux = null;
                $j = 2;
            } else {
                if (!empty($datos[$i][$j])) {
                    $aux[$j] = $datos[$i][$j];
                    $contador++; //incrementamos el contador por cada linea encontrada
                    if ($contador == 3) { //si la linea fue trociada en 3 pues automaticamente limpiamos el array auxiliar para no mandar informacion
                        $aux = null;
                    }
                }
            }
        }
        if (!empty($aux)) {
            array_push($newArray, $aux);
        }
    }
    echo "<pre>";
    print_r($newArray); 
    echo "</pre>"; //mostramos los datos con un preformateado
}
