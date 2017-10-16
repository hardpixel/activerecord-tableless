# Tableless

Create models that are not bound to the database and take advantage of the ActiveRecord features, such as validation, relationships, etc.

[![Gem Version](https://badge.fury.io/rb/tableless.svg)](https://badge.fury.io/rb/tableless)
[![Build Status](https://travis-ci.org/hardpixel/tableless.svg?branch=master)](https://travis-ci.org/hardpixel/tableless)
[![Maintainability](https://api.codeclimate.com/v1/badges/853a6013a50339b2baea/maintainability)](https://codeclimate.com/github/hardpixel/tableless/maintainability)

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'tableless'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install tableless

## Usage

Define a model like this:

```ruby
class ContactMessage < ActiveRecord::Base
  include Tableless

  attribute :name,  :string
  attribute :email, :string

  validates :name, :email, presence: true
end
```

You can now use the model in a view like this:

```ruby
<%= form_for :message, @message do |f| %>
  Name: <%= f.text_field :name %>
  Email: <%= f.text_field :email %>
<% end %>
```

And in the controller:

```ruby
def message
  @message = ContactMessage.new(params[:message])

  if @message.valid?
    # Process the message...
  end
end
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment. To install this gem onto your local machine, run `bundle exec rake install`.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/hardpixel/tableless. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the Tableless project’s codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/hardpixel/tableless/blob/master/CODE_OF_CONDUCT.md).
