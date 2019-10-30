---
title: A RESTful Approach
layout: post
---

I was reading about an approach DHH takes when structuring his controllers in a RESTful way. He basically states that everytime they make a new action, they create a new controller. The controller would then only utilize RESTful CRUD actions such as `index`, `show`, `new`, `edit` etc. I thought this was an interesting approach. One that enforces seperations of concern by creating a more uniform controller structure.

## How it works

Let's say we have a controller (`BooksController`). This controller handles the usual RESTful actions such as `index`, `create`, `edit`, and `delete` to handle a book's state. We add a new action called `publish`, and what it does is, it publishes the book and sends information about the book to a publisher. In such an approach, we would create a route `post :publish`, and an action within `BooksController` (`def publish`).

That sounds great, but what if we wanted to enforce a strictly RESTful approach to this? Instead of having an action called `publish`, which does not fall under a REST CRUD action, we create a new controller for it. The new controller would be namespaced under `Books`.

<pre><code class="ruby">class Books::PublishController < ApplicationController
    def index
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