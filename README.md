# Chap App v2

## 1. Install CLI and create the app

```
$ npm install -g ember-cli

$ ember new chat-app

$ cd chat-app

$ ember server
```
- [http://localhost:4200](http://localhost:4200)
- Ember Inspector

## 2. Add bootstrap and some css

Searching bootstrap package: [http://www.emberaddons.com](http://www.emberaddons.com)

```
$ ember install ember-bootstrap
```

Some extra style in `app/styles/app.css`

```
body {
  padding-bottom: 70px;
}

.message-bar {
  height: 70px;
  padding-top: 13px;
}

.alert-chat {
  padding: 5px;
}

.label-user {
  font-size: 100%;
  font-weight: normal;
}

.close-chat {
  line-height: 18px;
}
```

## 3. Add header to the main template

`/app/templates/application.hbs`

```html
<div class="container">
  <div class="page-header">
    <h1>Meetup Chat App
      <small>Let's talk about Ember</small>
    </h1>
  </div>

  {{outlet}}
</div>
```

## 4. Create two pages: index and chat

```
$ ember generate template index
```

Add content to index

```
<h1>Index</h1>
```

```
ember generate route chat
```

## Add dynamic segment to `chat` route

`app/router.js`

```
this.route('chat', { path: '/chat/:user_name' } );
```

## Input box with condition on index page

`app/templates/index.hbs`

```html
<div class="jumbotron text-center">
    <div class="container">
        <div class="col-md-4 col-md-offset-4">
          {{input class='form-control input-lg' placeholder="Enter your name." value=name}}
        </div>

        <div class="col-md-4 col-md-offset-4">
          {{#if name}}
              <h2>Please join to the chat {{name}}!</h2>
            {{#link-to 'chat' name class="btn btn-lg btn-success"}}Join{{/link-to}}
          {{else}}
              <p>Please enter your nickname and click the join button.</p>
          {{/if}}
        </div>
    </div>
</div>
```
