[![Travis status](https://secure.travis-ci.org/smartlogic/raddocs.png)](https://secure.travis-ci.org/smartlogic/raddocs)


# Raddocs

Raddocs is a browser for JSON outputted by the [rspec_api_documentation](http://github.com/zipmark/rspec_api_documentation) gem.

## Install

`Gemfile`
```ruby
gem 'raddocs'
```

`config/routes.rb`

```ruby
  mount Raddocs::App => "/docs"
```

Make sure RspecApiDocumentation is generating JSON:

`spec/spec_helper.rb`

```ruby
RspecApiDocumentation.configure do |config|
  config.format = :json
end
```


## Configuration
* `api_name` - Name of the API on the example index page
* `docs_dir` - where the JSON output from rspec_api_documentation is located
* `docs_mime_type` - if you use the middleware, what mime type are you serving your docs as, must be a regex. eg: `/text\/vnd.org.oestrich.raddocs\+plain/`
* `include_bootstrap` - Boolean to disable including bootstrap if you are using your own css
* `external_css` - Array of css files to include, with a full URL to them
* `url_prefix` - Optional prefix to insert before URLs generated by Raddocs

```ruby
Raddocs.configure do |config|
  config.docs_dir = "doc/api"
end
```

### Custom CSS

You can include extra css by the config option `external_css` or add a directory to the docs dir named `styles`. Every css file in the styles dir will be included as a link element on all pages.
