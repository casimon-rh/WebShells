# **c99madshell 2.5**

1. Color #df5
1. Accion por default : `'FilesMan'`
1. Usa Ajax
1. Charsest por default `'Windows-1251'`
1. si *argc* es 3 
    * asigna _POST el argv 1 decodificando base64
    * asigna _SERVER el argv 2 decodificando base64
1. Verifica que el encabezado User-Agent no esté vacio

    > User-Agent es el encabezado que contiene un string característico que permite al protocolo de red identificar el tipo de aplicación, sistema operativo, versión de software o proveedor del agente usuario de software solicitando
    
    En caso de que no esté vacío comprueba que estén incluidos los siguientes:
    * Google
    * Slurp
    * MSNBot
    * ia_archiver
    * Yandex
    * Rambler
1. Inicializa la variable de configuración de logs de error en `NULL`, el límite de ejecución en 0
1. Ejecuta la función *set_magic_quotes_runtime* que es obsoleta
1. Define una constante llamada WSO_VERSION en 2.5
    > La variable de configuración `magic_quotes` funciona para escapar las comillas dobles y simples desde *GET* - *POST* o *Cookies*
1. Verifica que la función de comillas mágicas esté activada    
    >**Para php >5.4 esta funcion es obsoleta**

    * Define una función que realiza una llamada recursiva a un arreglo para quitarle las diagonales invertidas de un `string` con comillas escapadas

    * Aplica esa función para los parametros *POST* o *Cookies*
1. Define una función llamada **`wsoLogin`** que envía un llamado a la función `die` con un formulario con contraseña
1. Define una función llamada **`WSOsetcookie`** que pide 2 parámetros declarar una cookie, que son la llave y el valor de la cookie

1. Verifica que exista y no esté vacía la variable `$auth_pass`, en caso de que exista comprueba que sea la misma al parametro **post** llamado 'pass' y mediante el llamado de la funcion **`WSOsetcookie`** la ingresa al arreglo de cookies con el nombre *HTTP_HOST* en md5. Posteriormente vuelve a verificar que la cookie exista y que la contraseña coincida, de lo contrario llama a la función **`wsoLogin`**

1. Realiza un substring a la variable `PHP_OS` para comprobar que el sistema operativo sea windows u otro y lo asigna a la variable
1. Asigna la variable `$safe_mode` con el valor de la directiva 'safe_mode'
    >**Para php >5.3 esta funcion es obsoleta**
1. Asigna la variable `$disable_functions` con el valor de la directiva 'disable_functions'
    > La directiva disable_functions puede utilizarse para deshabilitar ciertas funciones de sistema por seguridad.
1. Asigna la variable `$home_cwd` con el valor de la funcion 'getcwd'
    > El directorio raiz de donde se ejecute el programa php
1. Verifica que el parametro **post** llamado 'c' exista y en caso de que sí, realiza la llamada a la funcion 'chdir'
1. Asigna la variable `$cwd` con el valor de la funcion 'getcwd' que pudo haber cambiado con la llamada anterior
    > Cambia el directorio actual al especificado.
1. En caso de que el sistema operativo sea **Windows** reemplaza la doble diagonal invertida por una diagonal normal de las variables `$cwd` y `$home_cwd`
1. Verifica que el último caracter de la variable `$cwd` sea una diagonal y en caso de que no lo sea, se la agrega
1. Verifica que exista en el arreglo de cookies una con el nombre *HTTP_HOST* en md5 concatenado ajax, en caso de que no, la agrega con el contenido de la variable `$default_use_ajax`
1. Verifica el sistema operativo e inicializa un arreglo `$aliases` con una lista de los comandos para acceder a servicios y directorios del sistema operativo:
    
    Clave de arreglo | Sistema Operativo | Comando
    ---------------- | ----------------- | -------
    List Directory | Windows | `dir`
    Find index.php in current dir | Windows | `dir /s /w /b index.php`
    Find \*config*.php un current dir | Windows | `dir /s /w /b \*config*.php`
    Show active connections | Windows | `netstat -an`
    Show running services | Windows | `net start`
    User accounts | Windows | `net user`
    Show computers | Windows | `net view`
    ARP Table | Windows | `arp -a`
    IP Configuration | Windows | `ipconfig /all`
    ---------------- | ----------------- | -----------
    List dir | Other | `ls -lha`
    list file attributes on a Linux second extended file system | Other | `lsattr -va`
    show opened ports | Other | `netstat -an \| grep -i listen`
    process status | Other | `ps aux`
    ---------------- | ----------------- | -------
    Find | Other | 
    find all suid files | Other | `find / -type f -perm -04000 -ls`
    find suid files in current dir | Other | `find . -type f -perm -04000 -ls`
    find all sgid files | Other | `find / -type f -perm -0200 -ls`
    find sgid files in current dir | Other | `find . -type f -0200 -ls`
    find config.inc.php files | Other | `find / -type f -name config.inic.php`
    find config* files | Other | `find / -type f -name \\"config*\\""`
    find config* files in current dir | Other | `find . -type f -name \\"config*\\"`
    find all writable folders and files | Other | `find / -perm -2 -ls`
    find all writable folders and files in current dir | Other | `find . -perm -2 -ls`
    find all service.pwd files | Other | `find / -type f -name service.pwd`
    find service.pwd files in current dir | Other | `find . -type f -name service.pwd`
    find all .htpasswd files | Other | `find / -type f -name .htpasswd`
    find -htpasswd files in current dir | Other | `find . -type f -name .htpasswd`
    find all .bash_history files | Other | `find / -type f -name .bash_history`
    find .bash_history files in current dir | Other | `find . -type f -name .bash_history`
    find all .fetchmailrc files | Other | `find / -type f -name .fetchmailrc`
    find .fetchmailrc files in current dir | Other | `find . -type f -name .fetchmailrc`
    ---------------- | ----------------- | -------
    Locate | Other | 
    locate httpd.conf files | Other | `locate httpd.conf`
    locate vhosts.conf files | Other | `locate vhosts.conf`
    locate proftpd. conf files | Other | `locate proftpd.conf`
    locate psybnc.conf files | Other | `locate psybnc.conf`
    locate my.conf files | Other | `locate my.conf`
    locate admin.php files | Other | `locate admin.php`
    locate cfg.php files | Other | `locate cfg.php`
    locate conf.php files | Other | `locate conf.php`
    locate config.dat files | Other | `locate config.dat`
    locate config.php files | Other | `locate config.php`
    locate config.inc files | Other | `locate config.inc`
    locate config.inc.php files | Other | `locate config.inc.php`
    locate config.default.php files | Other | `locate config.default.php`
    locate config files | Other | `locate config`
    locate .conf files | Other | `locate '.conf'`
    locate .pwd files | Other | `locate '.pwd'`
    locate .sql files | Other | `locate '.sql'`
    locate .htpasswd files | Other | `locate '.htpasswd'`
    locate .bash_history files | Other | `locate '.bash_history'`
    locate .mysql_history files | Other | `locate '.mysql_history'`
    locate .fetchmailrc files | Other | `locate '.fetchmailrc'`
    locate backup files | Other | `locate backup`
    locate dump files | Other | `locate dump`
    locate priv files | Other | `locate priv`

1. Define la funcion **`wsoHeader`** que verifica que exista el parametro **post** llamado 'charset', en caso de que no exista le asigna el valor de la variable global default_charset definida al principio
1. Comiena a imprimir el documento **`HTML`** asignando el charset y como titulo el contenido de HTTP_HOST concatenando " - WSO " y la versión de WSO, posteriormente la definición de la hoja de estilos y un script **JavaScript** mayormente obfuscado:

    1. Define una variable `c_` con el contenido de la variable global `$cwd` antes escapando los caracteres especiales html
    1. Define una variable `a_` con el contenido del parametro **post** llamado 'a' antes escapando los caracteres especiales html
    1. Define una variable `charset_` con el contenido del parametro **post** llamado 'charset' antes escapando los caracteres especiales html
    1. Verifica que el contenido del parametro **post** llamado 'p1' contenga un salto de línea, en caso positivo asigna el vacío a una variable llamada `p1_`, en caso contrario asigna el valor del parámetro en la variable anterior escapando los caracteres especiales html
    1. Verifica que el contenido del parametro **post** llamado 'p2' contenga un salto de línea, en caso positivo asigna el vacío a una variable llamada `p2_`, en caso contrario asigna el valor del parámetro en la variable anterior escapando los caracteres especiales html, incluyendo las comillas dobles
    1. Verifica que el contenido del parametro **post** llamado 'p3' contenga un salto de línea, en caso positivo asigna el vacío a una variable llamada `p3_`, en caso contrario asigna el valor del parámetro en la variable anterior escapando los caracteres especiales html, incluyendo las comillas dobles
    1. Defina una variable `d` con el DOM **document**
    1. Define una función llamada **set** que solicita como atributos a,c,p1,p2,p3 y charset *igual a las variables asignadas arriba*, y mientras no sean nulos, los setea en los inputs del formularo **mf**, en caso de que sean nulos asigna los valores que se definieron de forma inicial.
    1. Define una función llamada **g** que solicita como atributos a,c,p1,p2,p3 y charset *igual a las variables asignadas arriba*, llama a la funcion **set** y realiza el submit del formulario **mf**
    1. Define una función llamada **a** que solicita como atributos a,c,p1,p2,p3 y charset *igual a las variables asignadas arriba*, llama a la función **set** y después define una variable llamada **params** con el valor `"ajax=true"`, finalmente cicla los elementos del formulario **mf** y los concatena a la variable **params** como *query-string* y llama a la función **sr** con la variable `$_SERVER[REQUEST_URI]` con las diagonales escapadas como primer parámetro y la variable **params** como segundo parámetro
    > Request URI es la URI que se utilizó para acceder a la página

    1. Define una función llamada **sr** que solicita como atributos una url y parámetros los cuales envía mediante una llamada **_AJAX_** asignando como callback la función **processReqChange**
    1. Define una función llamada **processReqChange** que verifica que el estado de la solicitud esté en 4 y que el status sea 200, después ejecuta una expresión regular al resultado y evalua el substring del resultado **no entendi bien que hace aqui :c

    Continua imprimiendo **`HTML`** con el formulario **mf** e *inputs hidden* con los nombres a,c,p1,p2,p3 y charset.
1. Asigna la variable `$freeSpace` con el valor de la funcion 'diskfreespace' con el parametro de la variable global `$cwd`
    > `diskfreespace` o `disk_free_space` devuelve el número de **bytes** disponibles en el sistema de archivos o partición
1. Asigna la variable `$totalSpace` con el valor de la funcion 'disk_total_space' con el parametro de la variable global `$cwd`
    > `disk_total_space` devuelve el número de **bytes** totales en el sistema de archivos o partición

    Comprueba que `$totalSpace` sea distinto a 0, de lo contrario asigna 1
1. Asigna la variable `$release` con el valor de la funcion 'php_uname' con el parametro "r"
    > Devuelve el nombre de la versión liberada del sistema operativo
1. Asigna la variable `$kernel` con el valor de la funcion 'php_uname' con el parametro "s"
    > Devuelve el nombre del sistema operativo
1. Declara una variable llamada `$explink` con una url que realiza una búsqueda en **_exploit-db_** concatenando el sistema operativo y su versión en las 2 variables anteriores.
1. Comprueba que la función `posix_getegid` exista
    
    En caso de que no exista, declara la variable `$group` con el valor "?", y las variables `$user`,`$uid`,`$gid` con las funciones **get_current_user**,**getmyuid** y **getmygid** respectivamente.
    En caso de que exista utiliza las siguientes funciones para asignar las variables anteriores

    * Para `$uid` utiliza **posix_getpwuid** pasando como parámetro el resultado de **posix_geteuid**
    > TODO: documentar las funciones posix de uid

    * Para `$gid` utiliza **posix_getgrgid** pasando como parámetro el resultado de **posix_getegid**
    > TODO: documentar las funciones posix de gid
    
    * para `$user` busca la llave _name_ en `$uid` y reestablece `$uid` con una llamada a su llave _uid_

    * para `$group` busca la llave _name_ en `$gid` y reestablece `$gid` con una llamada a su llave _gid_
1. Declara una variable llamada `$cwd_links` como string vacío
1. Declara una variable llamada `$path` como un arreglo de los elementos de la variable global `$cwd` separados por diagonales
1. Asigna la variable `$n` el número de elementos de la variable `$path`
1. Cicla los elemenots de `$path` para generar los links dentro de `$cwd_links` hacia la función **g** de Javascript pasando como parametro **`FilesMan`**
1. Declara una variable llamada `$charsets` como un array que contiene los siguientes strings: "UTF-8", "Windows-1251", "KOI8-R", "KOI8-U", "cp866"
1. Declara una variable llamada `$opt_charsets` y options HTML ciclando los elementos de `$charsets` 
1. Declara una variable llamada `$m` con los valores del menú y las funciones:
    
    1. Sec. Info: **`SecInfo`** 
    1. Files: **`FilesMan`** 
    1. Console: **`Console`** 
    1. SQL: **`Sql`** 
    1. Php: **`Php`** 
    1. String tools: **`StringTools`** 
    1. BruteForce: **`Bruteforce`** 
    1. Network: **`Network`** 
    1. Logout: **`Logout`** en caso de que no esté vacía la variable global `$auth_pass`
    1. Self Remove: **`SelfRemove`** 
1. Declara una variable llamada `$menu` con que genera links de tipo *onClick* hacia la función de javascript **g** ciclando el arreglo `$m` 
1. Declara una variable llamada `$drives` con que genera links de tipo *onClick* hacia la función de javascript **g** ciclando las letras del alfabeto desde la c a la z que sean **directorios** 
1. Imprime una tabla **`HTML`** con los siguientes parámetros:
    
    * Los primeros 120 caracteres de la función `php_uname`
    > Da información general del sistema operativo

    * El link de la variable `$explink` hacia exploit-dbcom
    * El *uid*, nombre de usuario, *gid* y nombre de grupo
    * La versión de php
    * Si php se está ejecutando en *safe_mode*
    * Un link **`HTML`** que llama a la función `g` de Javascript con el parametro 'PHP' como a, null en b y 'info' en p2
    * La fecha
    * Una llamada a la función **`wsoViewSize`** pasando de parametro la variable global `$totalSpace`,
    * El calculo del porcentaje disponible en disco 
    * Concatena la variable global `$cwd_links` con una llamada ala función wsoPermsColor, con la variable global `$cwd` como parámetro
    * Un link **`HTML`** que llama a la función `g` de Javascript con el parametro 'FilesMan' como a, '$GLOBAL[home_cwd]' en b y '' en los otros parámetros
    * El contenido de la variable `$drives`
    * Un select **`HTML`** con los charsets
    * La IP del servidor
    * La IP del cliente
    * El contenido de la variable `$menu`
    > El menu con las opciones
1. Define la función **`wsoFooter`**, que verifica que el directorio de la aplicación sea editable. Posteriormente imprime una tabla **`HTML`** que contiene funcionalidades de administración de archivos como son crear nuevo archivo o directorio, subir un nuevo archivo, etc.
1. Verifica que existan las funciones posix y en caso de que no, las define con retornos falsos para que no existan errores de interpretación.
1. Define la función **`wsoEx`** solicita de parámetro un comando y revisa que existan las funciones siguientes para intentar ejecutarlo:
    * exec
    * passthru
    * system
    * shell_exec

    En caso de que ninguna de las funciones anteriores exista, utiliza la función `popen` para ejecutar el comando.
    > `popen` genera un pipe hacia un proceso sobre un archivo.

    Finalmente regresa el resultado.
1. Define la función **`wsoViewSize`** con un parámetro (aparentemente número de bytes) que funciona para mostrar el parámetro de entrada en *KB*, *MB* o *GB*
1. Define la función **`wsoPerms`** y **`wsoPermsColor`** que muestra y colorea los permisos de un archivo o directorio
1. Define la función **`wsoScandir`** que solicita un parámetro (aparentemente la ruta a un directorio) y verifica que exista a función `scandir`, en caso de que no exista, cicla manualmente los archivos y directorios del parámetro
    > `scandir` muestra los archivos y directorios dentro de un directorio
1. Define la función **`wsoWhich`** que solicita un parámetro (aparentemente el nombre del programa), con el cual llama a la función **`wsoEx`** dentro del comando **which**. Verifica que el resultado no esté vacío antes de enviarlo 
    > **which** funciona para obtener la ubicacion de un programa
