---
title: A RESTful Approach
layout: post
---

I recently read an article that explained how we can fully utlize a RESTful approach to structuring controllers. The main theme was the uniformaity of code, I.e. a controller should only be concerned with how it utlizes REST's CRUD actions to change the state of a process. Therefore creating a seperation of concern within the controllers themselves.

## How it works

Let's say we have a controller (`BooksController`). This controller handles the usual RESTful actions such as `index`, `create`, `edit`, and `delete` to handle a book's state. We add a new action called `publish`, and what it does is, it publishes the book and sends information about the book to a publisher. In such an approach, we would create a route `post :publish`, and an action within `BooksController` (`def publish`).

That sounds great, but what if we wanted to enforce a strictly RESTful approach to this? Instead of having an action called `publish`, which does not fall under a REST CRUD action, we create a new controller for it. The new controller would be namespaced under `Books`.

<pre><code class="ruby">class Books::PublishController < ApplicationController
    def create
        ...
    end

    def edit
        ...
    end
end
</code></pre>

`PublishController` is therefore concerned with CRUD operations specically around the process of publishing a book.

I implemented a similar structure for a feature I was working on and found it to be a refreshing change. It really made me consider how I should structure my controllers in a more RESTful way. Although, I would recommend not going overboard by creating a controller for _every_ new action. If the action's process is simple (E.g. setting a boolean), then it would make sense to have it within the parent controller.

<script>
    document.getElementById("ruby-on-rails-link").classList.add("active");
    hljs.initHighlightingOnLoad();
</script>