# Dock Api (Seepix Digital) - Version 0.2.1

![Dock Icon](https://github.com/lagden/Dock/raw/master/img/logo_dock.png)

http://seepix.com.br/

Documentação
------------

> Especificação da Api Dock (Gerenciador de vinhetas e notificações).

### Rotas

    auth            POST   /login.:format
    template        GET    /template/:id.:format
    decoration      GET    /decoracao/:id.:format
    log             POST   /log/posta.:format
    log_message     POST   /log/mensagem/posta.:format
    channel         GET    /canal/lista.:format
    homepage        ANY    /

Autenticação
------------

### Url
`http://api.seepix.dock.seepix.com.br/login.:format`

### Formats
xml

### Method
HTTP Basic Authentication

### Example Response (Ok)

http://api.seepix.dock.seepix.com.br/login.xml

    <?xml version="1.0" encoding="UTF-8"?>
    <user>
      <id><![CDATA[1]]></id>
      <first_name><![CDATA[Thiago]]></first_name>
      <last_name><![CDATA[Lagden]]></last_name>
      <fullname><![CDATA[Thiago Lagden]]></fullname>
      <email><![CDATA[lagden@gmail.com]]></email>
    </user>

### Example Response (Error)

    <?xml version="1.0" encoding="UTF-8"?> 
    <error><![CDATA[Usuário ou senha inválida]]></error>


Template
--------

### Url
`http://api.seepix.dock.seepix.com.br/template/:id.:format`

### Formats
xml

### Method
GET

### Parameters
* id (required)

### Requires Authentication
true

### Example Response (Ok)

http://api.seepix.dock.seepix.com.br/template/1.xml

    <?xml version="1.0" encoding="UTF-8"?>
    <template id="1"><![CDATA[http://api.seepix.dock.seepix.com.br/uploads/test/templates/1/template.swf]]></template>

### Example Response (Error)

    <?xml version="1.0" encoding="UTF-8"?>
    <error><![CDATA[Template não encontrado]]></error>


Decoração
---------

### Url
`http://api.seepix.dock.seepix.com.br/decoracao/:id.:format`

### Formats
xml

### Method
GET

### Parameters
* id (required)

### Requires Authentication
true

### Example Response (Ok)

http://api.seepix.dock.seepix.com.br/decoracao/1.xml

    <?xml version="1.0" encoding="UTF-8"?>
    <decoration id="1"><![CDATA[http://api.seepix.dock.seepix.com.br/uploads/test/decorations/1/image.png]]></decoration>

### Example Response (Error)

    <?xml version="1.0" encoding="UTF-8"?>
    <error><![CDATA[Decoração não encontrada]]></error>


Log
---

### Url
`http://api.seepix.dock.seepix.com.br/log/posta.:format`

### Formats
xml

### Method
POST

### Values
* message (required)
* channel_id (opcional)
* note_id (opcional)

### Requires Authentication
true

### Example Response (Ok)

http://api.seepix.dock.seepix.com.br/log/posta.xml

    <?xml version="1.0" encoding="UTF-8"?>
    <log><![CDATA[Salvo]]></log>

### Example Response (Error)

    <?xml version="1.0" encoding="UTF-8"?> 
    <error><![CDATA[Somente POST]]></error>

    <?xml version="1.0" encoding="UTF-8"?> 
    <error><![CDATA[POST inválido]]></error>


Log de Mensagens (status de leitura)
------------------------------------

### Url
`http://api.seepix.dock.seepix.com.br/log/mensagem/posta.:format`

### Formats
xml

### Method
POST

### Values
* status (options: 'Não', 'Sim', 'Incompleto') (required)
* channel_id (required)
* note_id (opcional)

### Requires Authentication
true

### Example Response (Ok)

http://api.seepix.dock.seepix.com.br/log/mensagem/posta.xml

    <?xml version="1.0" encoding="UTF-8"?>
    <log><![CDATA[Salvo]]></log>

### Example Response (Error)

    <?xml version="1.0" encoding="UTF-8"?> 
    <error><![CDATA[Somente POST]]></error>

    <?xml version="1.0" encoding="UTF-8"?> 
    <error><![CDATA[POST inválido]]></error>


Listagem de Vinhetas e Notificações
-----------------------------------
 
### Url
`http://api.seepix.dock.seepix.com.br/canal/lista.:format`

### Formats
xml

### Method
GET

### Requires Authentication
true

### Example Response

http://api.seepix.dock.seepix.com.br/canal/lista.xml


    <?xml version="1.0" encoding="UTF-8"?> 
    <dock> 
     <channels> 
      <channel id="4" date_ini="2011-04-01 00:00:00" date_end="2011-09-01 00:00:00" updated_at="2011-07-29 11:28:48"> 
       <template id="3" updated_at="2011-07-29 11:25:58"><![CDATA[http://api.dock/uploads/template/3/file.swf]]></template> 
       <decoration id="1" border_top="10" border_right="10" border_bottom="10" border_left="10" updated_at="2011-07-29 11:25:58"><![CDATA[http://api.dock/uploads/decoration/1/image.png]]></decoration> 
       <moment type="Hora"> 
        <time value="13:51"/> 
        <time value="14:00"/> 
       </moment> 
       <frequency type="Semana"> 
        <day value="Segunda"/> 
        <day value="Quarta"/> 
        <day value="Sexta"/> 
       </frequency> 
       <notes> 
        <note id="2" updated_at="2011-07-29 11:28:48"> 
         <item type="title"><![CDATA[Nota 2 com HTML]]></item> 
         <item type="description"><![CDATA[Descri&ccedil;&atilde;o da Nota 1]]></item> 
         <item type="html"><![CDATA[<p><b>Superr!!!</b></p>
    <p><img src="/uploads/editorFiles/456/Thumbnails/b8/3d2a_festa181c3818e3349a4a21f918be19f-250x250.jpg" width="250" height="166" alt="festa na seepix" title="festa na seepix" /></p>
    <p>Teste do html</p>]]></item> 
        </note> 
       </notes> 
       <files updated_at="2011-07-29 11:28:48"><![CDATA[http://api.dock/uploads/editorFiles/456/456.zip]]></files> 
      </channel> 
      <channel id="1" date_ini="2011-05-01 16:32:15" date_end="2011-09-01 16:32:15" updated_at="2011-07-29 11:25:58"> 
       <template id="1" updated_at="2011-07-29 11:25:58"><![CDATA[http://api.dock/uploads/template/1/file.swf]]></template> 
       <moment type="Login"/> 
       <frequency type="Semana"> 
        <day value="Segunda"/> 
        <day value="Quinta"/> 
       </frequency> 
      </channel> 
      <channel id="3" date_ini="2011-04-01 16:32:15" date_end="2011-09-01 16:32:15" updated_at="2011-07-29 11:25:58"> 
       <template id="3" updated_at="2011-07-29 11:25:58"><![CDATA[http://api.dock/uploads/template/3/file.swf]]></template> 
       <decoration id="1" border_top="10" border_right="10" border_bottom="10" border_left="10" updated_at="2011-07-29 11:25:58"><![CDATA[http://api.dock/uploads/decoration/1/image.png]]></decoration> 
       <moment type="Hora"> 
        <time value="13:51"/> 
        <time value="14:00"/> 
        <time value="13:51"/> 
       </moment> 
       <frequency type="Semana"> 
        <day value="Segunda"/> 
        <day value="Quarta"/> 
        <day value="Sexta"/> 
       </frequency> 
       <notes> 
        <note id="1" updated_at="2011-07-29 11:25:58"> 
         <item type="title"><![CDATA[Nota 1]]></item> 
         <item type="description"><![CDATA[Descrição da Nota 1]]></item> 
        </note> 
       </notes> 
      </channel> 
     </channels> 
    </dock>

