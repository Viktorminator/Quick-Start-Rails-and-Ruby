# Добавление аттрибутов к Todo

Когда вы добавляете или удаляете что-то из базы данных, то вы можете делать это с помощью "миграций". Миграции - это Руби код, где вы можете описывать что бы вы хотели поменять. Для начала вы можете сгенерировать миграцию следующей командой (<span style="display:inline-block;float:right;margin-top:-3.5em;margin-right:.5em;position:relative;">:whale:</span>):

```shell
rails generate migration add_todo_fields
```

Если вы взглянете на ваш редактор и откроете папку `db`, то вы увидите, что там есть новый файл, который включает "add_todo_fields" и timestamp. Давайте отредактируем этот файл и добавим несколько колонок (вы можете думать о базе данных как о странице Excel). Для этого мы добавим следующее в метод `change`:

```ruby
class AddTodoFields < ActiveRecord::Migration
  def change
    add_column :todos, :description, :string
    add_column :todos, :done_at,     :datetime
  end
end
```

Так, что же это всё делает? Когда вы запускаете миграцию она запустит метод `change` и добавит два поля к таблице, где мы храним наши todos. Также мы определили их вид: первая колонка - это строка и вторая - это время. Это поможет Rails понять как их обрабатывать.

Запустите следующую команду для того, чтобы база данных знала о вносимых нами изменениях (<span style="display:inline-block;float:right;margin-top:-3.5em;margin-right:.5em;position:relative;">:whale:</span>):

```
rake db:migrate
```


💾 [Добавьте поля Todo](https://github.com/bastilian/todo-application/commit/cca3ec307c80796080dc574a2bcfd0766bd9e8b1)
