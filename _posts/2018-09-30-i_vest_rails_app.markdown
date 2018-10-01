---
layout: post
title:      "i.vest Rails App"
date:       2018-10-01 00:56:33 +0000
permalink:  i_vest_rails_app
---


For my first Rails app I decided to create app to allow investors to share their investments and funds. Users can sign up through the site manually or through their Google account to start creating their own investment (purchase of a fund) and to view the top funds (stocks, bonds, etfs, etc) chosen by other users.


**Dysfunctional Relationships**

The app uses three models: User, Investments, and Funds, with Investments acting as the join table for the `has_many, through:` relationship with relevant controllers for each. Additionally, investments were a nested resource under users.

While a simple many_to_many relationship with a join model, handling the `has_many, through:` relationships in combination with nested resources and nested forms got me confused. Somehow, what was once a clear parent-child relationship soon became a dysfunctional family where members refused to acknowledge or relate to one another. 

The first major issue I had was setting up the models incorrectly. There is a huge difference between the two (hint: use the second one).

```
class User < ApplicationRecord
  has_many :funds, through: :investments
  has_many :funds
end

class User < ApplicationRecord
  has_many :investments
  has_many :funds, through: :investments
end
```

Remember the `has_many, through:` portion belongs to the model having many-to-many connection with this model and does not belong on the join table. 



**Hidden in Plain Sight**

A sneaky error that caused me quite a few hours in debugging time is not setting up the nested form properly. The app contained a nested form that allowed a user to create or select funds through the investment creation form. Unfortunately, at first the child refused to acknowledge the parent (fund was created without a user_id). 
```
<%=form_for([user, investment]) do |f|%>

  <%=f.label :quantity, "Quantity:" %>
  <%=f.number_field :quantity %><br>
```

A simple fix with a n added hidden_field added this to the params field.

```
  <%=f.hidden_field :user_id, :value => @user.id %>
```

But, wait! Why is the user_id still nil for my fund? 

```
  def investment_params
    params.require(:investment).permit(:quantity, :price, :user_id, :fund_id,
      new_fund: [:symbol])
  end
```

It won't be if you whitelist it in the controller params!


**The Render vs. Redirect Debate**

Since users cannot be trusted with entering data, we have validations in place. And to show them the error of their ways, we have a nice little div at the top listing the full error messages.

```
<% if @user.errors.any? %>
  <div id="errors">
    <h4>Error:</h4>

    <ul>
    <% @user.errors.full_messages.each do |msg| %>
      <li><%= msg %></li>
    <% end %>
    </ul>
  </div>
<% end %>
```

However, this exact setup only works if there is an instance variable. And unfortunately, our `session` is not one. 

```
<div id="errors">
  <h4><%= flash[:notice] %></h4>
</div>
```

What does work is passing along a little `flash[:notice] = "Invalid username or password. Please try again."` from the sessions controller. Then add a little something to the view, and you're all set!


**Now onto Javascript!**

![](https://pics.me.me/welcome-to-javascript-where-the-objects-are-made-up-and-13411868.pnghttp://)
