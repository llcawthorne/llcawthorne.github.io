---
layout: post
title: "AWDWR 5.1 - Depot Application"
date: 2017-06-08
tags: ruby rails awdwr51 web
---

I'm going to go into a bit less detail on the Depot Application, and cover
several parts per post.  There should be room for plenty of code examples. 
Here's the repot that I'm pushing this project up to:
[Git Depot51](https://github.com/llcawthorne/depot51)
Check it out and run `bin/rails server` to view in action.

### Task A: Creating the Application

The new application is created by simply running `rails new depot51` from
the command-line.  As before, it starts us out with a full skeleton of an 
application.  First we want to create a model for the Product table, like
what we sketched out previously.  You can create the scaffold with:

```
bin/rails generate scaffold Product \
         title:string description:text image_url:string price:decimal
```

This generates a migration file,
`db/migrate/20170606004555_create_products.rb`.  Migrations always start
with a timestamp to keep them in order.  Here's what was generated:

```ruby
class CreateProducts < ActiveRecord::Migration[5.1] 
  def change
    create_table :products do |t|
      t.string :title
      t.text :description
      t.string :image_url
      t.decimal :price

      t.timestamps
    end 
  end
 end
```

We want to modify it so that price has eight significant digits and two
digits after the decimal point.  To do so, we edit the file to look like
this:

```ruby
class CreateProducts < ActiveRecord::Migration[5.1] 
  def change
    create_table :products do |t|
      t.string :title
      t.text :description
      t.string :image_url
      t.decimal :price, precision: 8, scale: 2

      t.timestamps
    end 
  end
 end
```

Then to apply it and create the table, we run `bin/rails db:migrate`.  We
can run our app now and navigate to the products page.  This is already
setup to allow us to browse our products table and create new items.

![products page](/img/2017-06-08/products-page.png)

The new product form is in `depot51/app/views/products/_form.html.erb` if
we wanted to modify it.  At this point, we can even `bin/rails test` to
make sure everything is working.  What we've done so far has already
generated 7 tests with 9 assertions that pass.

This is where I had my first problem following the instructions of the
book.  Rather than printing out the script to load samples, it links to a
`seeds.rb` file.  The link was dead.  There was also a dead link provided
that was supposed to have images to use to get started.  I imagine this
will be fixed when the book actually ships, but it was disappointing that
they didn't have the resources up already since they print the links in
their early release pdf.  The seed data file looks like:

```ruby
Product.delete_all

Product.create!(title: 'Seven Mobile Apps in Seven Weeks',
  description:
    %{<p>
      <em>Native Apps, Multiple Platforms</em>
      Answer the question “Can we build this for ALL the devices?” with a
      resounding YES. This book will help you get there with a real-world
      introduction to seven platforms, whether you’re new to mobile or an
      experienced developer needing to expand your options. Plus, you’ll find
      out which cross-platform solution makes the most sense for your needs.
      </p>},
  image_url: '7apps.jpg',
  price: 26.00)
```

And you load it to the database with `bin/rails db:seed`.  We want to
"pretty up" the product listing, so we will next modify the producs.scss
sass stylesheet that the scaffold command generated for us.  It starts out
empty except for comments.  The book takes advantage of the nesting of
sass to wrap everything in the products.scss file with a .products class.
That way, we can modify the application.html.erb file to put
`class='<%= controller.controller_name %>'` in the body tag and apply
the styles.  We do this because Rails loads all the stylesheets at once,
and we only want the products.scss rules to affect the products controller's
pages.  At this point, we have:

![products page styled](/img/2017-06-08/products-page-styled.png)

It would look a bit better if it had the images for each book, but since
they weren't available for download, I just commented out the image display.
I was surprised that it considered a missing image to be a server stopping
failure though.

### Task B: Validation and Unit Testing
