# Вступление в Ruby

__**Замечание:** Перед началом, пожалуйста, прочитайте [README](../README.md)!__

Ruby = это язык, который может быть использован для нескольких задач программирования; сегодня мы взглянем на Ruby On Rails, фреймворк, разработанный специально для веб-разработки. Вот пример того, как выглядит Ruby:

```ruby
class Person
  attr_accessor :name

  def say_hello_to(person)
    puts "Hello #{person.name}"
  end
end

first_person = Person.new
first_person.name = "Diego"

second_person = Person.new
second_person.name = "Alice"

first_person.say_hello_to(second_person)
```

Класс позволяет вам описать объект (в нашем случае объект "Person") и мы даём ему аттрибут `attr_accessor`. Он также имеет метод `say_hello_to`, который берёт другой объект "Person" и использует его имя.

Вы можете запустить следующую команду (<span style="display:inline-block;float:right;margin-top:-3.5em;margin-right:.5em;position:relative;">:whale:</span>):

```shell
ruby examples/persons_talk.rb
```

Когда это произойдёт, то вы должны увидеть "Hello Alice" в вашем терминале.
