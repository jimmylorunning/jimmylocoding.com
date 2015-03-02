---
layout: post
title: "Method Chaining to the Madness"
tags:
- chaining
- geocode
- object oriented design
- ruby
- SRP
---

I said I'd write a little bit about some of the challenges I encountered while writing the <a href="https://github.com/codeforatlanta/csv_geocoder">CSV Geocoder</a> utility. So here's a small problem and solution:

### Problem:

The purpose of the class is very simple. I want to add geocode data to the CSV, then write it to a file. So I write a method like `write_csv_with_geocode(file)` that joins the CSV with the geocode data and then writes it to a file. However, this violates the <a href="http://en.wikipedia.org/wiki/Single_responsibility_principle">single responsibility</a> per method principle. It does two things: adds the geocode data, then writes it to a file.

{% highlight ruby %}
  def write_csv_with_geocode(file)
    merge_csv_with lat_lngs
    CSV.open(file, 'wb') do |csv|
      @csv.each do |row|
        csv &lt;&lt; row
      end
    end
  end
{% endhighlight %}

I could break the method out into two separate methods, but I know that in 99% of the use cases, the user will want to add_geocode then write. The two responsibilities are intimately related in this case. So the user would have to type two methods (three if you count the initializer) instead of one every time, like this:

{% highlight ruby %}
data = CSVGeocoder.new 'data.csv'
data.add_geocode
data.write 'data_with_geocode.csv'
{% endhighlight %}

which wouldn't be so bad if it weren't something they'd have to do every time for such a simple task.

The upside of having it all in one method is that I can accomplish two related tasks in one method call instead of having to call both of them separately every time.

###	Solution:

Chaining! I make add_geocode assign the new value to an instance variable, then return self (returning self is the key to making methods chainable). Then the write method takes the instance variable and writes it to a CSV file. So now the user can do the simple task in one line, and the operations are also separated into their own methods. Best of both worlds! In fact, I realized I could do the same with all of the methods in the class, so that you could now write the following line:

{% highlight ruby %}
CSVGeocoder.new('data.csv').add_geocode.write 'data_with_geocode.csv'
{% endhighlight %}

Isn't it pretty? Here's the new code:

{% highlight ruby %}
  def add_geocode
    @new_csv = merge_csv_with lat_lngs
    self
  end

  def write(file)
    CSV.open(file, 'wb') do |csv|
      @new_csv.each do |row|
        csv &lt;&lt; row
      end
    end
  end
{% endhighlight %}

### What do you think?

Is chaining a good solution to this problem? How would you have done it? Also: are there other ways I could improve this class?