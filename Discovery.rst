Discovery
========

Terra.Framework içerisinde datalarla ilgili tüm işlerin yapıldığı katmandır.

Kurulum
--------

Terra.Discovery Paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

    Install-Package Terra.Discovery -Version 1.0.0-pre-alpha -Source http://10.10.0.237/nuget/Default/
    
Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Discovery* bularak indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/en/latest/Baslarken.html


    
Kullanımı
---------
Startup.cs dosyasında ConfigureServices metodunda Discovery eklememiz gerekmektedir.::      

        public void ConfigureServices(IServiceCollection services)
        {
            services.AddDiscovery(new DiscoveryConfiguration
            {
                DefaultSettings = new DbSettings(),
                AuditEnable = true,
                AuditUserProvider = new AuditUserProvider(),
                EnableEntityLogger = true,
                CreateEntityLoggerTable = true
            });
            // Add framework services.
            services.AddMvc();
        }

Controller classında kullanımı aşağıdaki gibidir::

        using Terra.Discovery.Interfaces;
        public class HomeController : Controller
        {
            private IUnitOfWork _uow;
            public HomeController(IUnitOfWork uow)
            {
                _uow = uow;
            }
             public IActionResult Index()
             {
                _uow.Set<MyClass>().Add(new MyClass
                {
                    Name = "Nikola",
                    Surname = "Tesla"
                });
                _uow.Save();
                var repo = _uow.Repo<MyClass>();
                repo.Remove(repo.GetBy().FirstOrDefault());
                _uow.Save();

               var myList = _uow.Repo<MyClass>().GetBy().ToList();
               return View(myList);
            }
        }
    
MyClass.cs::

        using Terra.Discovery.Types;
        public class MyClass : DiscoveryEntity
        {
            public string Name { get; set; }
            public string Surname { get; set; }
            public override void Map(ModelBuilder modelBuilder)
            {
                modelBuilder.Entity<MyClass>(opt =>
                {
                    //opt.ToTable("MyClass"); Veritabanında tablo var ise burada tablonun ismini yazıyoruz.
                    opt.HasKey(x => x.Id);
                    opt.HasAlternateKey(x => x.AutoId);
                    opt.Property(x => x.AutoId).UseSqlServerIdentityColumn();
                });
            } 
        }
