# DevOpsTFM
Este repositorio forma parte de un trabajo fin de master

Consta de un vagrantfile que ejecutara 3 maquinas virtuales:
  1 Maquina virtual para alojar la aplicacion que se desplegara y configurara con Ansible con el playbook ubicado en la carpeta "provisioningWebApp"
  1 Maquina virtual para alojar la Base de Datos que se desplegara y configurara con Ansible con el playbook ubicado en la carpeta "provisioningMySQL"
  1 Maquina virtual para alojar la herramienta Jenkins que se configurara con Ansible con el playbook ubicado en la carpeta "provisioningJenkins"
  
La aplicacion se ha desarrollado con visual studio usando el framework net core con arquitectura MVC. Debido a que es una aplicacion de uso industrial no se subira a este repositorio pero si se desea ejecutar cualquier aplicacion net core con arquitectura MVC, unicamente hay que alojar todos los archivos que se crean al publicar la aplicacion en "provisioningWebApp\files\publish" y configurar el archivo "provisioningWebApp\templates\service\webapi.service" sustituyendo en la linea "ExecStart=/usr/share/dotnet/dotnet /var/www/webapi/CalendarWebApp.dll" el nombre de la plicacion ("CalendaWebApp.dll") por el nombre de la nueva aplicacion.

Para ejecutar la solucion se debe ejecutar en el terminal vagrant up. Una vez cargada la solucion: 
  - la aplicacion se ejecutara en: http://192.168.33.10:88/
  - jenkins se ejecutara en: http://192.168.33.30:8080/ y la clave de admin se mostrara en los logs de vagrant justo antes de terminar la ejecucion.
