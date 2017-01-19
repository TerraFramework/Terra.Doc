Apollo
========

Terra.Framework içerisinde bulunan bootstrap tabanlı User Interface katmanıdır.

Kurulum
--------

Terra.Apollo paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

    $ Install-Package Terra.Apollo -Version 1.0.3-pre-alpha -Source http://10.10.0.237/nuget/Default/

Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Apollo* yu aratarak indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/en/latest/Baslarken.html


Kullanımı
---------
Projenizde Terra kontrollerini kullanmak için View dosyanızın içerisine aşağıdaki tanımlamaları eklemeniz gerekmektedir::

   @using Terra.Apollo
   @using Terra.Nuclues

Daha sonra View sayfamızda Terrada bulunan html kontrollere erişmek için *Html.Terra()* yazarak kullanmak istediğimiz kontrolleri sayfamıza ekleyebiliriz. 

Örnek Buton kullanımı::

       @Html.Terra().Button().Text("Save") 

Örnek Form kullanımı::

     @using (Html.Terra().Form().Url(Url.Action("Add","Home")).Method(FormMethod.Post).Begin())
     {
         @Html.Terra().FormTextBox().SetId("name")
         @Html.Terra().Button().Type(ButtonTypes.Submit).Text("Save")
     }
