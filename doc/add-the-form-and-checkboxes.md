## Добавление форм и чекбоксов

Ятобы добавить форму для создания новых todo и сделать отметку о уже выполненных мы внесём изменения в наш шаблон `index.html.erb`.

Поменяйте первую строку – ту, что с `<%= @todos.size %>` – следующим кодом:

```html
<h1>Todos: <span id="todo-count"><%= @todos.size %></span></h1>

<form id="todo-form" action="/todos" method="post">

  <input name="authenticity_token" value="<%= form_authenticity_token %>" type="hidden">

  <div class="ui action input">
    <input name="todo[description]" type="text" placeholder="What to do?" />
    <button class="ui button submit">Add</button>
  </div>

</form>
```

Это добавит форму для добавления новых todo.

Эта форма делает `POST` запросы к `/todos` в нашем приложении. Rails использует HTTP-метдоы для маршрутизации запросов от пользователей. Вы можете видеть какие маршруты к каким контролерам и действиям и с какими HTTP-method, просто запустив (<span style="display:inline-block;float:right;margin-top:-3.5em;margin-right:.5em;position:relative;">:whale:</span>):

```shell
rake routes
```

Форма также содержит скрытый инпут с названием **authenticity_token**, он будет добавлять токен к данным, которые отправляет форма для подтверждения, что они идут от нашего приложения.

После сохранения шаблона, перейдите в браузер и обновите `http://DOCKER_IP:3000/todos`. Вы должны увидеть форму и она должна работать и создавать новые todo!

Теперь мы поменяем вид списков todos немного используя `semantic-ui`-css классы и заставим всё работать добавив немного JavaScript.

В шаблоне поменяйте `<ul>` и всё остальное в нём на следующее:

```html
<ul id="todo-list">

  <% @todos.each do | todo | %>
    <li>

      <div class="ui checkbox">
        <input type="checkbox" data-id="<%= todo.id %>"<%= todo.done ? ' checked="checked"' : '' %>>
        <label><%= todo.description %></label>
      </div>

    </li>
  <% end %>

</ul>
```
Теперь todos содержит также чекбоксы и классы для улучшения внешнего вида.

Чекбоксы используют аттрибут "done" в Todo, чтобы знать отмечен он сделанным или нет. Мы перейдём к этому на следующем этапе. Перед этим мы добавим чуть-чуть JavaScript к `application.js` для создания и обновления наших todos делая запрос в фоне:

```javascript
$(document).ready(function () {

  $('#todo-list input[type="checkbox"]').on('click', function (event) {
    $.ajax({
      url: '/todos/' + $(event.target).data('id'),
      method: 'put',
      data: {
        todo:{
          done: event.target.checked
        }
      }
    });
  });

});
```

Убедитесь, что вы добавили это **после** первого блока комментариев. Запрос также использует аттрибут "done". Мы должны теперь его развернуть и разрешить.


💾 [Добавьте форму и чекбоксы к Todos](https://github.com/bastilian/todo-application/commit/ffe88069fc6192d9d390e869535e1f7621e0f29d)
