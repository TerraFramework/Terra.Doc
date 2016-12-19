Voyager
========

Terra.Framework içerisinde tercih edilen dile göre localization yapan bölümdür.

Kurulum
--------

Terra.Voyager Paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

    Install-Package Terra.Voyager -Version 1.0.0-pre-alpha -Source http://10.10.0.237/nuget/Default/
    
Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Voyager* yi aratarak Terra.Voyager yi bulup Terra.Voyager'yi indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/en/latest/Baslarken.html


    
Kullanımı
---------

Öncelikle Voyager' ı kullanmak istediğimiz projeye bir tane *Resources* klasörü ekliyoruz. Ve içine istediğimiz dile ait olan json dosyasını ekliyoruz.  tr-TR. json ve ya en-EN.json gibi.
Daha sonra starup içerisinde aşağıdaki kodu ekliyoruz::
    public void ConfigureServices(IServiceCollection services)
            {
                // Add framework services.
                services.AddVoyager(new Voyager.Configuration.VoyagerConfiguration
                {
                    ResourcesFolder = "resources"
                });
            }
            
Burada önemli olan kısım kendi oluşturduğunuz resources klasörünün adı ile burada yazdığınız klasör adının birbiriyle aynı olmasıdır. Startup'ta ekledikten sonra istediğimiz controller içerisinde aşağıdaki örnekte olduğu gibi implemente edebiliriz.::

    private IVoyager _voyager;
           public HomeController(IVoyager voyager)
           {
               _voyager = voyager;
           }
           
Örnek kullanım ise şu şekildedir.::

    public IActionResult Index()
          {
              var txt = _voyager.Get("test");
              ViewData["Message"] = txt;
              return View();
           }

 


