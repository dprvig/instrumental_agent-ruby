# Instrumental Agent

Instrument anything.

## Setup & Usage

Add the gem to your Gemfile.

```sh
gem 'instrumental_agent'
```

Visit instrumentalapp.com[instrumentalapp.com] and create an account, then 
initialize the agent with your API key, found in the Docs section.

```sh
I = Instrumental::Agent.new('YOUR_API_KEY', :test_mode => !Rails.env.production?)
```

We recommend setting test_mode to true in dev/test modes so that you don't pollute your production data.

Now you can begin to use Instrumental to track your application.

```sh
I.gauge('load', 1.23)
I.increment('signups')
```

Data without historical context sucks. Instrumental lets you 
backfill data, allowing you to see deep into your project's past.

```sh
User.find_each do |user|
  I.increment('signups', 1, user.created_at)
end
```

Want some general server stats (load, memory, etc.)? Install instrumental_tools and run this command (sorry not daemonized yet :)

```sh
gem install instrumental_tools
instrument_server
```

Running under Rails? You can also give our experimental Rack middleware 
a shot by initializing it with:

```sh
Instrumental::Middleware.boot
```

Need to quickly disable the agent? set :enabled to false on initialization and you don't need to change any application code.

## Troubleshooting & Help

We are here to help, please email us at [support@instrumentalapp.com](mailto:support@instrumentalapp.com).
