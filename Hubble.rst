
Hubble
========

Terra.Framework içerisinde loglama işleminin yapıldığı bölümdür.Ayrıca Hubble.Monitoring.Extension paketi ile. Monitoring uygulamasının çalıştığı api üzerinden loglama yapabilir.

Kurulum
--------

Terra.Hubble Paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

   Install-Package Terra.Hubble -Version 1.0.11-pre-alpha -Source http://nuget.bilgeadam.com/nuget/Default/
    
Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Hubble* ı aratarak Terra.Hubble ı bularak indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/en/latest/getting_started.html

::

   public void ConfigureServices(IServiceCollection services)
   {
            //Verilen path’e loglama yapar.
            services.AddHubble(new HubbleConfiguration()
            {
                LogsFolder = "log",
                EnableSystemLogs = false,
                EnableNavigatingLog = true
            });

            //OPTIONAL
            services.AddHubble(new HubbleConfiguration 
            { 
            EnableNavigatingLog = true 
            });

            services.AddHubbleMonitoring(new HubbleMonitoringConfiguration
            {
                Key = "KEY",
                Secret = "SECRET",
                MonitoringUrl = "url"
            }); 


   }

   public void Configure(IApplicationBuilder app)
   {
            app.UseHubble();     
   }


    
Kullanımı
----------

 
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
               _hubble.Log("Add Operaton Success");
               return View();
           }
       }

 

Ayarlar
----------
      
       
+-------------------------+-------------------------------------------------+
| Özellikler              | Açıklama                                        |  
+=========================+=================================================+
| EnableSystemLog         | .NET’ in tüm loglarını Hubble üzerinden loglar. | 
+-------------------------+-------------------------------------------------+ 
| EnableNavigatingLog     | Bütün sayfa gezinimlerini loglar.               | 
+-------------------------+-------------------------------------------------+ 
| EnableExceptionHandling | Exceptionları yakalar.                          | 
+-------------------------+-------------------------------------------------+ 
| LogsFolder              | Loglama yapılacak klasörün path'ini set eder.   | 
+-------------------------+-------------------------------------------------+ 
| MaxfileSize             | Log dosyasının maksimum büyüklüğünü set eder.   | 
+-------------------------+-------------------------------------------------+ 

