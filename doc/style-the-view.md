## Стили для отображения


Так как мы сфокусируемся на Ruby on Rails here, то мы будем использовать CSS-Framework (SemanticUI) для обеспечения нам некоторого базового стиля. Добавьте следующее к вашему `Gemfile`:

```
gem 'semantic-ui-sass', github: 'doabit/semantic-ui-sass'
```

Для включения стилей и скриптов, чтобы наш SemanticUI заработал, нам нужно вызвать в `require` их.

Добавьте это в файл `app/assets/stylesheets/application.css` в блоке комментариев наверху перед `*/`:

```
*= require semantic-ui
```

И добавьте javascript в `app/assets/javascripts/application.js`:

```
//= require semantic-ui
```

Также в первом блоке комментариев, лучше перед `require_tree .`.

Для окончания работы со стилями, добавьте этот кусок в `application.css`:

```
body { padding: 2em 35%; }
.input { width: 100%; }
ul { margin: 2em 0; padding: 0;}
li { list-style: none; }
```

Это чуть подправит внешний вид наших Todo, когда мы их добавим чуть больше к нашему шаблону.

💾 [Добавление SemanticUI](https://github.com/bastilian/todo-application/commit/b5867646342b9ecfe2abc8f5dae77df48df8ca38)
