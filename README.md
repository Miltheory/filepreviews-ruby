# FilePreviews.io (Ruby client)
[![Gem Version](http://img.shields.io/gem/v/filepreviews.svg?style=flat)](http://badge.fury.io/rb/filepreviews)
[![Build Status](http://img.shields.io/travis/jonahoffline/filepreviews-ruby.svg?style=flat)](https://travis-ci.org/jonahoffline/filepreviews-ruby)
[![Dependency Status](http://img.shields.io/gemnasium/jonahoffline/filepreviews-ruby.svg?style=flat)](https://gemnasium.com/jonahoffline/filepreviews-ruby)
[![Code Climate](http://img.shields.io/codeclimate/github/jonahoffline/filepreviews-ruby.svg?style=flat)](https://codeclimate.com/github/jonahoffline/filepreviews-ruby)
[![Gitter chat](https://img.shields.io/badge/gitter-filepreviews--ruby-blue.svg?style=flat)](https://gitter.im/jonahoffline/filepreviews-ruby)
[![Inline docs](http://inch-ci.org/github/jonahoffline/filepreviews-ruby.png)](http://inch-ci.org/github/jonahoffline/filepreviews-ruby)

Ruby client library and CLI tool for the [FilePreviews.io](http://filepreviews.io) service. Generate image previews and metadata from almost any kind of file.

## Installation

Add this line to your application's Gemfile:

    gem 'filepreviews'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install filepreviews

## Usage
Register your application for an API key at [FilePreviews.io](http://filepreviews.io).

### Configuration
To configure the gem to use your newly-registered `api + secret keys`, you can use one of the two configuration styles:

Block style:
```ruby
require 'filepreviews'

Filepreviews.configure do |config|
  config.api_key = 'YOUR_API_KEY'
  config.secret_key = 'YOUR_SECRET_KEY'
end
```

Simpler style:
```ruby
require 'filepreviews'

Filepreviews.api_key = 'YOUR_API_KEY'
Filepreviews.config.secret_key = 'YOUR_SECRET_KEY'
```

### Basic Example Code
```ruby
require 'filepreviews'

url = 'http://pixelhipsters.com/images/pixelhipster_cat.png'
result = Filepreviews.generate(url)

result.url
result.status
result.metadata # fetches metadata
```

#### Web Page Screencaptures
```ruby
url = 'http://pixelhipsters.com'
result = Filepreviews.generate(url)

result.url
result.status
result.metadata
```


#### Options
You can optionally send an options object (per request).

```ruby
conf = {
  options: {
    size: {
      width: 100,
      height: 999
    },
    # supported: 'exif', 'ocr', 'psd', 'checksum', 'multimedia',
    metadata: ['exif'],

    # supported: 'jpg', 'jpeg', 'png'
    format: 'jpg',

    # supported: '1', '1-3', '1,3,5', '1-3', 'all'
    pages: '1-3'
  }
}

result = Filepreviews.generate(url, conf)
result.url
result.metadata
```

### Command-Line Application
Options:

  * -k, --api_key    [key] - use API key from Filepreviews.io
  * -s, --secret_key [key] - use secret key from Filepreviews.io
  * -m, --metadata      - load metadata response
  * -v, --version       - display the version
  * -h, --help          - print help

### Command-Line usage examples

#### Basic use
	$ filepreviews http://www.pixelhipsters.com

#### With an API Key
	$ filepreviews --api_key YOUR_API_KEY_HERE --secret_key YOUR_SECRET_KEY_HERE http://www.pixelhipsters.com

#### Autoload Full (metadata) Response
	$ filepreviews -m http://pixelhipsters.com/images/pixelhipster_cat.png

**Note**: This will return a full metadata response, instead of the API's original response that only returns the `url` and `status` of the request.


## Author
  * [Jonah Ruiz](http://www.pixelhipsters.com)

## Discussion
If you have any questions, ideas or jokes:

[![Gitter chat](https://img.shields.io/badge/gitter-filepreviews--ruby-blue.svg?style=flat)](https://gitter.im/jonahoffline/filepreviews-ruby)


## Contributing

Is it worth it? let me fork it

I put my thing down, flip it and debug it

Ti gubed dna ti pilf nwod gniht ym tup I

Ti gubed dna ti pilf nwod gniht ym tup I
