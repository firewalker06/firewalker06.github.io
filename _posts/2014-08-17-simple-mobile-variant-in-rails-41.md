---
layout: post
title: Simple Mobile Variant in Rails 4.1
published: True
categories: [tips]
tags: [rails rails4.1]
comments: true
---

ActionPack Variants is one of Rails 4.1 feature to help developing between different device by differentiate response and views in a simple way.

Use `browser` gem to get better user agent helpers

{% highlight ruby %}
gem browser
{% endhighlight %}

Add method in ApplicationController 

{% highlight ruby %}
class ApplicationController < ActionController::Base
  before_action :set_device_type

  private
  def set_device_type
    request.variant = :mobile if browser.mobile?
  end
end
{% endhighlight %}

That's it! Now you can use `+mobile` in views file name to indicate views for mobile device. For example: `index.html+mobile.erb`.

- This code was taken from: [http://codemy.net/posts/rails-4-1-variants](http://codemy.net/posts/rails-4-1-variants)
- To learn more about ActionPack Variants: [http://edgeguides.rubyonrails.org/4_1_release_notes.html#action-pack-variants](http://edgeguides.rubyonrails.org/4_1_release_notes.html#action-pack-variants)
