Apollo
========

Terra.Framework içerisinde bulunan bootstrap tabanlı User Interface katmanıdır.

Kurulum
--------

Terra.Apollo paketini PackageManager Console' dan aşağıdaki komutu yazarak indirebilirsiniz::

    $ Install-Package Terra.Apollo -Version 1.1.4-pre-alpha -Source http://nuget.bilgeadam.com/nuget/Default/

Ve ya Baslarken_ bölümünde yazılan adımları yaptıysanız NuGet'ten *Terra.Apollo* yu aratarak indirebilirsiniz.

.. _Baslarken: http://terradoc.readthedocs.io/tr/latest/Getting_Started.html

Metotlar
---------

+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Metot Adı       | Özellik                                                                                                                           | Örnek                                                           |
+=================+===================================================================================================================================+=================================================================+
| Icon            | Component’lara,İcon,eklemek için kullanılır.İçerisinde bulunan,
                    Icons enum’ı sayesine,standart,font awesome iconlarını barındırır.
              | @Html.Terra().FormButton().Icon(Icons.Bell, IconPosition.right) |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| SetId           | Component’lara, Id ataması yapmak için kullanılır.                                                                                | @Html.Terra().FormButton().SetId(“formButton”)                  |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Value           | Component’lara, Value ataması yapmak için kullanılır.                                                                             | @Html.Terra().FormButton().Value(“5”)                           |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| AddCssClass     | Component’lara, stil class'ı eklemek için kullanılır.                                                                             | @Html.Terra().FormButton().AddCssClass(“btn btn-success”)       |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| RemoveCssClass  | Component’lara, verilen stil classlarını silmek  için kullanılır.                                                                 | @Html.Terra().FormButton().RemoveCssClass(“btn btn-success”)    |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Attribute       | Component’lara, attribute eklemek  için kullanılır.                                                                               | @Html.Terra().FormButton().Attribute(“İsim”,”Değer”)            |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| RemoveAttribute | Component’lara,eklenen attributleri silmek  için kullanılır.                                                                      | :@Html.Terra().FormButton().RemoveAttribute(“İsim”,”Değer”)     |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Name            | Component’lara, Name ataması yapmak için kullanılır.                                                                              | @Html.Terra().FormButton().Name(“formButton”)                   |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Html            | Component’lara, Html tagleri basmak için kullanılır.                                                                              | @Html.Terra().Button().Html(“<a href='#'>Gönder</a>”)           |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Text            | Component’lara, Text ataması yapmak için kullanılır.                                                                              | @Html.Terra().FormButton().Text(“formButton”)                   |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| SetText         | Component’lara, Text ataması yapmak için kullanılır.                                                                              | @Html.Terra().FormButton().,SetText(“formButton”)               |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Position        | Component’lara, konum ataması yapmak için kullanılır.                                                                             | @Html.Terra().FormButton().Position(Position.Left)              |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Tooltip         | Component’lara, tooltip ataması yapmak için kullanılır.                                                                           | @Html.Terra().FormButton().Tooltip(“testTooltip”)               |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Color           | Component’lara, tooltip ataması yapmak için kullanılır.Standart bootstrap renklerini kullanır.                                    | @Html.Terra().FormButton().Color(Colors.Info)                   |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Enable          | Component’lara, aktif ve pasif ataması yapmak için kullanılır.                                                                    | @Html.Terra().FormButton().Enable(true)                         |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+


Html Kontrollerin Kullanımı
---------
Projenizde Terra kontrollerini kullanmak için View dosyanızın içerisine aşağıdaki tanımlamaları eklemeniz gerekmektedir::

   @using Terra.Apollo
   @using Terra.Nuclues

Daha sonra View sayfamızda Terrada bulunan html kontrollere erişmek için *Html.Terra()* yazarak kullanmak istediğimiz kontrolleri sayfamıza ekleyebiliriz. 

Anchor
--------
::

   @Html.Terra().Anchor().Target(Target.Blank).Href("http://www.google.com")

Buton
--------
::

     @Html.Terra().Button().Text("Save")

Checkbox
--------
::

    @Html.Terra().Checkbox().Name("checkboxName").Checked(true)

Collapsible Panel
-----------------
::

    @using (Html.Terra().CollapsiblePanel().HeaderText("Header").HeaderContent(Html.Terra().Anchor().Href("#").Text("HeaderLink")).FooterText("Footer").FooterContent(Html.Terra().Anchor().Href("#").Text("FooterLink")).Begin())
    {
        @Html.Terra().Anchor().Href("#").Text("ContentLink")
    }

Datetimepicker
-------------
::

    @Html.Terra().DateTimePicker()

Div
-------
::

    @using (Html.Terra().Div().AddCssClass(Columns.Col_Md_12).Begin())
    {
        @using (Html.Terra().Div().AddCssClass(Columns.Col_Md_6).Begin())
        {
            @Html.Terra().Anchor().Href("#").Text("First Col-md-6")
        }
        @using (Html.Terra().Div().AddCssClass(Columns.Col_Md_6).Begin())
        {
            @Html.Terra().Anchor().Href("#").Text("Second Col-md-6")
        }
    }
    
    
Detailview 
--------
::

    @using (Html.Terra().DetailView().Begin())
    {
        @Html.Terra().Anchor().Href("#").Text("ContentLink")
    }

Display
--------
::

    @Html.Terra().Display("Value")
    @Html.Terra().Display(DateTime.Now, "{0:dd.MM.yyyy HH:mm}")
    @Html.Terra().Display("Google Link").Link("http://google.com")

Dropdownlist
-----------
::

    @Html.Terra().DropDownList().Items(Model.List).OptionLabel("Please Select")
    @Html.Terra().DropDownList().Ajax(Url.Action("GetItems", "Home")).OptionLabel("Please Select") //Ajax Call

Form
----
::
    
    @using (Html.Terra().Form().Url(Url.Action("Add","Home")).Method(FormMethod.Post).Begin())
     {
         @Html.Terra().FormTextBox().SetId("name")
         @Html.Terra().Button().Type(ButtonTypes.Submit).Text("Save")
     }


Hidden
--------
::

    @Html.Terra().Hidden().Value("hiddenValue")

Icon
--------
::
    
    @Html.Terra().Icon().AddCssClass(Icons.Plus)

Label
--------
::

    @Html.Terra().Label().SetText("Label Content")

Ul/Li
--------
::

    @Html.Terra().Ul().Content(Html.Terra().Li().Content(Html.Terra().Anchor().SetText("Link 1"))).Content(Html.Terra().Li().Content(Html.Terra().Anchor().SetText("Link 2")))

Modal
--------
::

    @using (Html.Terra().Modal("modal_id").HeaderContent(Html.Terra().Label().Text("HeaderLabel")).FooterContent(Html.Terra().Label().Text("Footer Label")).Begin())
    {
        @using (Html.Terra().Div().AddCssClass(Columns.Col_Md_12).Begin())
        {
            @Html.Terra().Anchor().Href("#").Text("Modal Content")
        }
    }

Panel
--------
::

    @using (Html.Terra().Panel().HeaderText("Header").HeaderContent(Html.Terra().Anchor().Href("#").Text("HeaderLink")).FooterText("Footer").FooterContent(Html.Terra().Anchor().Href("#").Text("FooterLink")).Begin())
    {
        @using (Html.Terra().Div().AddCssClass(Columns.Col_Md_12).Begin())
        {
            @Html.Terra().Anchor().Href("#").Text("Panel Content")
        } 
    }

RadioButton
--------
::

    @Html.Terra().RadioButton().Name("radioButtonName")

Span
--------
::
  
    @Html.Terra().Span().SetText("Span Text")
    
TabPanel/TabContent
--------
::

    @using (Html.Terra().TabPanel().Tab("tab_1_1", "Tab Title 1", true, Icons.Male, IconPosition.left).Tab("tab_1_2", "Tab Title 2").Begin())
    {
        @using (Html.Terra().TabContent("tab_1_1", true).AddCssClass(Columns.Col_Md_12).Begin())
        {
            @Html.Terra().Anchor().Href("#").Text("Tab_1_1 Content")
        }
        using (Html.Terra().TabContent("tab_1_2").AddCssClass(Columns.Col_Md_12).Begin())
        {
            @Html.Terra().Anchor().Href("#").Text("Tab_1_1 Content")
        }
    }

Textbox
--------
::

    @Html.Terra().Textbox().Value("Textbox Value")
    
    
TextArea
--------
::

    @Html.Terra().TextArea().SetText("Lorem ipsum sit $.")
    
VideoPlayer
--------
::

    @Html.Terra().VideoPlayer().Source("Youtube", "https://www.youtube.com/watch?v=xoCiy2hTEnw")

