
Hubble
========

Terra.Framework içerisinde loglama işleminin yapıldığı bölümdür.Ayrıca Hubble.Monitoring.Extension paketi ile. Monitoring uygulamasının çalıştığı api üzerinden loglama yapabilir.

Kurulum
--------

Terra.Hubble Paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

   Install-Package Terra.Hubble -Version 1.0.0-pre-alpha -Source http://nuget.bilgeadam.com/nuget/Default/
    
Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Hubble* ı aratarak Terra.Hubble ı bularak indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/en/latest/getting_started.html


    
Kullanımı
---------
Startup.cs ConfigureServices metodunda Hubble'ın ayarlarını yapmanız gerekmektedir.::

   services.AddHubble(new Terra.Hubble.Configuration.HubbleConfiguration
   {
         EnableNavigatingLog = true,
   });
   
   services.AddHubbleMonitoring(new HubbleMonitoringConfiguration
   {
       Key = "KEY",
       Secret = "SECRET",
       MonitoringUrl = "url"
   }); 

   
::

       public class HomeController : Controller
       {
           private IHubble _hubble;

           public HomeController(IHubble hubble)
           {
               _hubble = hubble;
           }
           public IActionResult Index()
           {
               _hubble.Log("Loglanan veri");
               return View();
           }
       }
       
       Properties:
       
         +-------------------------+------------+-----------+ 
         |EnableSystemLog          | Header 2   | Header 3  | 
         +=========================+============+===========+ 
         | EnableNavigatingLog     | column 2   | column 3  | 
         +-------------------------+------------+-----------+ 
         | EnableExceptionHandling | Cells may span columns.| 
         +-------------------------+-----------+----------+ 

