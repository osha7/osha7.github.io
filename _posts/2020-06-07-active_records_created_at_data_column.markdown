---
layout: post
title:      "Active Record's 'created_at' Data Column"
date:       2020-06-07 21:34:34 +0000
permalink:  active_records_created_at_data_column
---

For the full blog with images:  
[Medium](https://medium.com/@ogroetz/active-record-created-at-column-9e125aa2492a)

When building a CMS (Content Management System) through Sinatra, your CRUD/MVC application more than likely will benefit from the use of the Active Record column name ‘created_at’. Imagine you are creating an application for a blog and you want to save each post and show its readers the post)s) and when the post was published, our readers want to make sure that the information they are reading is current and relevant. You also want to be able to sort the posts on a rendered page in order of their date created, newest to oldest. This column, ‘created_at’, would be implemented in our database table to make this a simple and easy task.
Example of the create_table migration:


MySQL TIMESTAMP or DATETIME can both be used as the declared type of that column while creating your database. These data types will hold the date and time that a new instance of your model is created and added to your data table. Both of these types store the data as “YYYY-MM-DD HH:MM:SS” Although both data types are very similar, there are a few distinctions between the two, but we will stick to the differences that pertain to our desired use.
TIMESTAMP is more commonly used to track changes to records. TIMESTAMP values are stored converted from the current time zone to UTC, Coordinates Universal Time, and then converted to the users time zone once retrieved. DATETIME does not make this conversion.
A few decisions will need to be made here for how you would like your users to see the date the post was created. For this example we’ll say we would like to have each post listed on the ‘/posts’ route via the view.erb page. After our users create new posts, and we, as the developer, have created our ‘/posts/new’ and ‘/posts/create’ routes, and have established our params in doing so, we will work inside of this embedded Ruby file (view.erb) to use HTML and Ruby to sort through each of our post instances, listing them each with a ‘created_at’ stamp and an <a> tag link that will route users to view each individual post.

We will use Ruby’s .strftime method to arrange the date/time data in relation to the way we would like it to be rendered to the user. This method formats the date (and time, if so desired) according to the values of the string that have been directed by the programmer. If we imagine a new post was created today, the code above will give display the date as this: June 7, 2020. the commas and capital vs. lower casing here are an important part of the code. There are a number of great references for determining how best to use .strftime for your individual use, this article being one of the easiest I found for a beginner to understand.
As an example, the code above, while working together with the many other lines of code of our entire project, will render the page something like this:

Happy Coding!
