# justReactive
Adding reactive to string templates engine.

Добавлят односторонеею связаность шаблоноа и данных при вставке в любое место DOM страницы

# Принцип работы

Вызов anyObject.justText('host_url') возвращает html код который надо вставить в тело страницы или в шаблон используемого вами шаблонизатора.
Так же на объект переданный для отслеживания ставятся гетор и сетор.
После этого любое присваивание в объект будет вызывать гетор который в свою очередь обновит html код во всех местах где вызывалось отслеживание.
Если при вызове отслеживания был передан колбек то будет вызван колбек и в тело страницы в том месте будет вставлен результат который вернётся через колбек а не исходное значение объекта.

# Примеры

Примеры вызова в рамках использования шаблонизатора [JUST.js](https://github.com/baryshev/just) но данная библиотека может быть использована с любым другим текстовым шаблонизатором.

Подстановка без фильтрации
```
<%= anyObject.justHtml('anyValue') %>
```

Подстановка без фильтрации но с колбеком
```
<%= anyObject.justHtml('anyValue', function(v){return (v+"").replace("a", "D") }) %>
```

Подстановка без фильтрации но с колбеком и дополнительными данными передаваемыми в колбек
```
<%= anyObject.justHtml('anyValue', function(v, custom_data){return (v+"").replace("a", "D") }, {custom:'data'}) %>
```

Подстановка текста 
```
<%= anyObject.justText('host_url') %>
```

Подстановка текста с колбеком
```
<%= anyObject.justText('anyValue', function(v){return (v+"").replace("a", "G") }) %>
```

Подстановка текста с колбеком и дополнительными данными передаваемыми в колбек
```
<%= anyObject.justText('anyValue', function(v, custom_data){return (v+"").replace("a", "G") }, {custom:'data'}) %>
```

Подстановка класса если знаение не false
```
<h1 class="<%= anyObject.justClass('anyValue', 'anyClassName') %> " >Any text</h1>
```

Подстановка класса если клбек вернул не false
```
<h1 class="<%= anyObject.justClass('anyValue', 'anyClassName', function(v, custom_data.custom){return v && custom_data.custom }, {custom:'data'}) %> " >Any text</h1>
```

Подстановка класса если знаение false
```
<h1 class="<%= anyObject.justNotClass('anyValue', 'anyClassName') %> " >Any text</h1>
```

Подстановка класса если клбек вернул false
```
<h1 class="<%= anyObject.justClassName('anyValue', function(v, custom_data){return v && custom_data.custom }, {custom:'data'}) %> " >Any text</h1>
```

Подстановка того что вернул клбек в качестве класса 
```
<h1 class="<%= anyObject.justNotClass('anyValue', 'anyClassName', function(v, custom_data.custom){return v + custom_data.custom }, {custom:'data'}) %> " >Any text</h1>
```

Подстановка атрибута 
```
<h1 <%= anyObject.justAttr('anyValue', 'data-test') %> >Any text</h1>
```

Подстановка атрибута с колбеком
```
<h1 <%= anyObject.justAttr('anyValue', 'data-test', function(v){return (v+"").replace("a", "G") }) %> >Any text</h1>
```
 
Подстановка атрибута с колбеком и дополнительными данными передаваемыми в колбек
```
<h1 <%= anyObject.justAttr('anyValue', 'data-test', function(v, custom_data){return (v+"").replace("a", "G") }, {custom:'data'}) %> >Any text</h1>
```
