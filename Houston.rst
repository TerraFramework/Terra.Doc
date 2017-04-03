Houston
========

Terra.Framework içerisinde güvenlik mekanızmasının işlediği bölümdür.Bu katman temel olarak,login,işlemlerini,gerçekleştirir.

Kurulum
--------

Terra.Houston Paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

   Install-Package Terra.Houston -Version 1.0.15-pre-alpha -Source http://nuget.bilgeadam.com/nuget/Default/
    
Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Houston* u aratarak Terra.Houston u bulup Terra.Houston'u indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/en/latest/Baslarken.html


    
Kullanımı
---------
 Houston katmanı,tüm işlemleri gerçekleştirmek için,kimlik uygulaması ile entegre olarak çalışır.Mission Control'e yapılan,tanımlalamalardan,sonra,konfigürasyon gerçekleşir.
 
::

   public void ConfigureServices(IServiceCollection services)
   {
            app.UseHoustonClient(new HoustonClientConfiguration
            {
                Authority = "https://kimlik.x.com",
                ClientId = "CLIENT_KEY",
                ClientSecret = "CLIENT_SECRET"
            });
   }

   public void Configure(IApplicationBuilder app)
   {
            services.AddHoustonClient();
   }
   
   
Ayarlar
----------


Konfigürasyon,sonrası,yetki sisteminin,tüm projeye dahil olması için,aşşağıdaki,düzenlemeyi yapmanız gerekmektedir.

::

        public void ConfigureServices(IServiceCollection services)
        {
            services.AddMvc(options =>
            {
                options.Filters.Add(AllSecureFactory.CreateFilter());
            });
        }

