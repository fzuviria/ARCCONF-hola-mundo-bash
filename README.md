# Programación Orientada a Unix - ARCCONF meetup

 ## [ Esto no es una presentación ]


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 ## [ El otro día conocí Squid ]

 
 
                                                                            * Squid
                                                                                - About Squid
                                                                                - Open Squid Configuration
                                                                                - Open Squid Folder
                                                                            * Paneo de Directorios
 
 
 

 
 
 
 
 
 
 ## [ Programación Orientada a Unix ]
 
 
 * El programa cumple una y solamente una funcion
 * Los programas se combinan para formar soluciones
 * Todo es un File
 
    -> El archivo persiste el estado
    -> Existen los programas (que son archivos).
    -> Un programa tiene entrada y salida estandar en forma de Stream de datos.
    -> Puedo conectar la entrada o salida estándar con cualquier archivo
    -> Puedo conectar la entrada o salida estándar con cualquier otro programa
    -> Un programa recibe parámetros
    -> Los parámetros pueden ser archivos
    
  Y un archivo no necesariamente existe en disco
  
            df | grep tmpfs
  
 ## [ Ejercicio: Hola mundo ]
 
 
 Armo proyecto

  ~
  git init ARCCONF-hola-mundo-bash
  cd ARCCONF-hola-mundo-bash
  mkdir bin var etc
  ll

  
  
  
  
  
  
  
    
 ## [ Ejercicio: Hola mundo ]
 
  
 Saludador Simple
 
  echo "hola mundo" #estamos saludando
  
 Creamos el script
  
  history | tail -n1 | cut -d ' ' -f 5- > bin/hola-mundo-convencional.sh
  chmod +x bin/hola-mundo-convencional.sh
  
 Probamos 
  
  bin/hola-mundo-convencional.sh

  
  
    
 ## [ Ejercicio: Hola mundo ]
 
 
 Saludador Stdin
 
  while read COSA; do echo "hola $COSA"; done; #Leo de std_in hasta el final del archivo y saludo

 Creamos el script
 
  history | tail -n1 | cut -d ' ' -f 5- > bin/saludador_stdin.sh
  chmod +x bin/saludador_stdin.sh

 Probamos
 
  ( echo "mundo"; echo "fruta"; ) | bin/saludador_stdin.sh 
  
  
  
    
 ## [ Ejercicio: Hola mundo ]

 
 Saludador Parametrizado
 
  while read COSA; do echo "hola $COSA"; done < $1; #Leo del primer parámetro el archivo hasta el final y saludo

 Creamos el script
 
  history | tail -n1 | cut -d ' ' -f 5- > bin/saludador_param.sh
  chmod +x bin/saludador_param.sh
  ( echo "mundo"; echo "fruta"; ) > etc/saludables
 
 Probamos
  
  bin/saludador_param.sh etc/saludables

  
  
 ## [ Combinando lo que ya hicimos ]

 
 Usando el Saludador Stdin pero con archivos
 
  bin/saludador_stdin.sh < etc/saludables
  
  cat etc/saludables | bin/saludador_stdin.sh

  
  
  
  
  
  
  
  
  
  
 ## [ Combinando lo que ya hicimos ]
  
  
 Usando el Saludador Parametrizado pero con Streaming
  
  bin/saludador_param.sh <(cat etc/saludables) #process substitution

  bin/saludador_param.sh <(echo chabón) #process substitution

  
  
  
  
  
  
  
  
  
  
 ## [ Branch, Commit ]
  
  
  Qué existe en mi directorio ?
 
 
 
 
 
 
 
 
 
 
 
 
 
 
  
 ## [ Volvamos al process substitution ]
  
 echo repite
    - si le paso un nombre de archivo,
      me devuelve un nombre de archivo
      
 cat concatena
    - si le paso un nombre de archivo,
      me devuelve su contenido

      

      
      
      
      
      
      
  
 ## [ Autoexplorándonos ]
  
  $$ expande a mi pid
  
  ls /proc
  
  
  
  
  
  
  
  
  
  
  
  
  
  
 ## [ Qué tan poderosa es la programación orientada a Unix? ]
  
  
  Ej 1: Sistema Operativo
  
  Ej 2: Map Reduce
  
    https://aadrake.com/command-line-tools-can-be-235x-faster-than-your-hadoop-cluster.html
  
  
  
  
  
  
  
  
  
  
  
 ## [ GRACIAS! ]
  
  
  

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
 
