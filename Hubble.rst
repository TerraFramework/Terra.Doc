
Hubble
========

Terra.Framework içerisinde loglama işleminin yapıldığı bölümdür.

Kurulum
--------

Terra.Hubble Paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

   Install-Package Terra.Hubble -Version 1.0.0-pre-alpha -Source http://10.10.0.237/nuget/Default/
    
Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Hubble* ı aratarak Terra.Hubble ı bularak indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/en/latest/Baslarken.html


    
Kullanımı
---------
Projeniz içerisinde *logs* klasörü açarak içine *logs.terra* uzantılı dosya oluşturmalısınız. Loglarımızın tutulacağı dosya burasıdır.
Startup.cs ConfigureServices metodunda Hubble'ın ayarlarını yapmanız gerekmektedir.::

   services.AddHubble(new Terra.Hubble.Configuration.HubbleConfiguration
   {
         EnableNavigatingLog = false,
   });
   
   
Controller classında kullanımı.::

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
