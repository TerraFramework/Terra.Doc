
Nucleus
========

Terra.Framework'ün çekirdek alt yapısını,barındıran, katmandır.İçerisinde bulunan,string ve object,extensionlar,sayesinde,bir çok,işlemi kolaylaştırmaktadır.

Kurulum
--------

Terra.Nucleus Paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

   Install-Package Terra.Nucleus -Version 1.0.10-pre-alpha -Source http://nuget.bilgeadam.com/nuget/Default/
    
Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Nucleus* ı aratarak Terra.Nucleus ı bularak indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/en/latest/getting_started.html



    
Kullanımı
----------

 
::

      Nucleus paketini,projemizde, kullanmak,için,aşşağıdaki referansları eklememiz gerekmektedir
      
      using Terra.Nucleus;

 

Metotlar
----------
:GetQueryString(object obj): Verilen,objeyi QueryString olarak çevirir. 
   
   

