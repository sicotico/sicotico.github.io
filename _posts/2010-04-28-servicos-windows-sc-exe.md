---

title: "Servicos Windows (sc.exe)"
date: "2010-04-28"
categories: 
  - "sin-categoria"
---

Para interaccionar con servicio en Windows existe un comando sc. Para borrar usamos sc delete "Nombre del servicio:"

Para obtener el nombre del servicio miramos en propiedades [![](images/servicioswin-270x300.png "Servicios Win")](https://luispuente.net/wp-content/uploads/2010/04/servicioswin.png)  Adjunto la información general del comando obtenida de [ss64.com](https://ss64.com) un proyecto licenciado bajo CC  [**Attribution-Non-Commercial-Share Alike 2.0 UK: England & Wales**](https://ss64.com/docs/copyright.html)

### SC.exe ([Resource Kit](https://ss64.com/links/windows.html#kits))

Service Control - Create, Start, Stop, Query or Delete any Windows [SERVICE](https://ss64.com/nt/syntax-services.html). The command _options_ for SC are case sensitive.

Syntax
      SC \[\\_server_\] \[_command_\] \[_service\_name_\] \[_Options_\]

Key
   _server_       : The machine where the service is running

   _service\_name_ : The KeyName of the service, this is often but not always
                  the same as the DisplayName shown in Control Panel, Services.
                  You can get the KeyName by running:
                     SC GetKeyName <DisplayName>

   _command_s:
          **query**  \[_qryOpt_\]   Show status
          queryEx \[_qryOpt_\]  Show extended info - pid, flags
          GetDisplayName    Show the DisplayName
          GetKeyName        Show the ServiceKeyName
          EnumDepend        Show Dependencies
          qc                Show config - dependencies, full path etc
          **start**          START a service.
          **stop**           STOP a service
          pause          PAUSE a service.
          continue       CONTINUE a service.
          create         Create a service. (add it to the registry)
          config         permanently change the service configuration
          delete         Delete a service (from the registry)
          control        Send a control to a service
          interrogate    Send an INTERROGATE control request to a service
          Qdescription   Query the description of a service
          description    Change the description of a service
          Qfailure       Query the actions taken by a service upon failure
          failure        Change the actions taken by a service upon failure
          sdShow         Display a service's security descriptor using SDDL
          SdSet          Sets a service's security descriptor using SDDL

   _qryOpt_:
          type= driver|service|all
                         Query specific types of service
          state= active|inactive|all
                         Query services in a particular state only
          bufsize= _bytes_
          ri= _resume\_index\_number_ (default=0)
          group= _groupname_
                         Query services in a particular group

   _Misc command_s that don't require a service name:
          SC  QueryLock  Query the LockStatus for the ServiceManager Database.
                         this will show if a service request is running
          SC  Lock       Lock the Service Database
          SC  BOOT       Values are {ok | bad} Indicates whether to save
                         the last restart configuration as the \`last-known-good\`
                         restart configuration
   Options
     The CREATE and CONFIG commands allow additional options to be set
     see the build-in help: 'SC create' and 'SC config'

Note the qryOpt options above are case sensitive - they must be entered in lower case, also the position of spaces and = must be exactly as shown.

The SC command duplicates some aspects of the [NET](https://ss64.com/nt/net.html) command but adds the ability to create a service. SC query will display if a service is running, giving output like this:

        SERVICE\_NAME       : messenger
        TYPE               : 20  WIN32\_SHARE\_PROCESS
        STATE              : 4  RUNNING
                                (STOPPABLE,NOT\_PAUSABLE,ACCEPTS\_SHUTDOWN)
        WIN32\_EXIT\_CODE    : 0  (0x0)
        SERVICE\_EXIT\_CODE  : 0  (0x0)
        CHECKPOINT         : 0x0
        WAIT\_HINT          : 0x0

To retrieve specific information from SC's output, [pipe](https://ss64.com/nt/syntax-redirection.html) into [FIND](https://ss64.com/nt/find.html) or [FindStr](https://ss64.com/nt/findstr.html) e.g.

  C:> SC query messenger | FIND "STATE" | FIND "STOPPED"

  C:> SC query messenger | FIND "STATE" | FIND "RUNNING"

The statements above will return an %ERRORLEVEL% = 1 if the text is not found

IF errorlevel 1 GOTO :my\_subroutine The [NET](https://ss64.com/nt/net.html) START command can be used in a similar way to check if a service is running:

   NET START | FIND "Service name" > nul
   IF errorlevel 1 ECHO The service is not running

The service control manager will normally wait up to 30 seconds to allow a service to start - you can modify this time (30,000 milliseconds) in the registry

HKLMSYSTEMCurrentControlSetControl ServicesPipeTimeout (REG\_DWORD)

Some options only take effect at the point when the service is started e.g. the SC config command allows the executable of a service to be changed. When the service next starts up it will run the new executable. Config changes requires the current user to have “permission to configure the service”.

**Examples:**

 SC GetKeyName "task scheduler"
 SC GetDisplayName schedule
 SC start schedule
 SC QUERY schedule
 SC QUERY type= driver
 SC QUERY state= all |findstr "DISPLAY\_NAME STATE" >svc\_installed.txt
 SC \\myServer CONFIG myService obj= LocalSystem password= mypassword
 SC CONFIG MyService binPath=c:myprogram.exe obj=".LocalSystem" password=""

Watch out for extra spaces: SC QUERY state= all Works SC QUERY sTate =all Fails!
