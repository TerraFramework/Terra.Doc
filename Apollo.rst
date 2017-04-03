Apollo
========

Terra.Framework içerisinde bulunan bootstrap tabanlı User Interface katmanıdır.

Kurulum
--------

Terra.Apollo paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

    $ Install-Package Terra.Apollo -Version 1.0.3-pre-alpha -Source http://nuget.bilgeadam.com/nuget/Default/

Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Apollo* yu aratarak indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/en/latest/Baslarken.html

Metotlar
---------

+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Metot Adı       | Özellik                                                                                                                           | Örnek                                                           |
+=================+===================================================================================================================================+=================================================================+
| Icon            | Component’lara,İcon,eklemek için kullanılır.İçerisinde bulunan,Icons enum’ı sayesine,standart,font awesome iconlarını barındırır. | @Html.Terra().FormButton().Icon(Icons.Bell, IconPosition.right) |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| SetId           | Component’lara, Id,ataması yapmak için kullanılır.                                                                                | @Html.Terra().FormButton().SetId(“formButton”)                  |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Value           | Component’lara, Value,ataması yapmak için kullanılır.                                                                             | @Html.Terra().FormButton().Value(“5”)                           |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| AddCssClass     | Component’lara, stil class'ı eklemek,için kullanılır.                                                                             | @Html.Terra().FormButton().AddCssClass(“btn btn-success”)       |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| RemoveCssClass  | Component’lara, verilen stil classlarını silmek, için kullanılır.                                                                 | @Html.Terra().FormButton().RemoveCssClass(“btn btn-success”)    |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Attribute       | Component’lara, attribute eklemek, için kullanılır.                                                                               | @Html.Terra().FormButton().Attribute(“İsim”,”Değer”)            |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| RemoveAttribute | Component’lara,eklenen attributleri silmek, için kullanılır.                                                                      | :@Html.Terra().FormButton().RemoveAttribute(“İsim”,”Değer”)     |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Name            | Component’lara, Name,ataması yapmak için kullanılır.                                                                              | @Html.Terra().FormButton().Name(“formButton”)                   |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Html            | Component’lara, Html,ataması yapmak için kullanılır.                                                                              | @Html.Terra().FormButton().Html(“formButton”)                   |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Text            | Component’lara, Text,ataması yapmak için kullanılır.                                                                              | @Html.Terra().FormButton().Text(“formButton”)                   |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| SetText         | Component’lara, Text,ataması yapmak için kullanılır.                                                                              | @Html.Terra().FormButton().,SetText(“formButton”)               |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Position        | Component’lara, konum,ataması yapmak için kullanılır.                                                                             | @Html.Terra().FormButton().Position(Position.Left)              |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Tooltip         | Component’lara, tooltip,ataması yapmak için kullanılır.                                                                           | @Html.Terra().FormButton().Tooltip(“testTooltip”)               |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Color           | Component’lara, tooltip,ataması yapmak için kullanılır.Standart bootstrap,renklerini kullanır.                                    | @Html.Terra().FormButton().Color(Colors.Info)                   |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Enable          | Component’lara, aktif ve pasif,ataması yapmak için kullanılır.                                                                    | @Html.Terra().FormButton().Enable(true)                         |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+

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
