# GoogleDriver

A ruby library
for extracting spreadsheet data from [Google Drive](https://www.google.com/drive/).

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'google_driver'
```

Or install yourself with `gem install google_driver`.

## Usage

See [Prerequisites](#Prerequisites) section below for instructions on where to find configuration option values.

```` rb
spreadsheet_id = "1a2B3C45_x0G44lk15Ff_M33ps"
configuration_options = {
  :app_name => "my-app",
  :email_address => "abc-123@developer.gserviceaccount.com",
  :key_file_path => File.expand_path("../key_file/my-app-abc123xy456z.json", __FILE__),
  :extraction_procedure => Proc.new do |row|
    "PARSING A SPREADSHEET ROW HERE -- #{row.inspect}"
  end
}
GoogleDriver.extract(spreadsheet_id, configuration_options)
````

### Prerequisites

#### Drive API-enabled App

Visit the [google developer console](https://console.developers.google.com), create a new application, and note its name.

Navigate to the **APIs & Auth > APIs** menu and enable the *Drive API* by searching for it.

#### Service Account

Navigate to the **APIs & Auth > Credentials** menu and add credentials for a service account.

Choose the .json key file option, download it, optionally move it somewhere else, and finally note its file path.

Back in the browser, also note the service account's email address.

#### Spreadsheet

Create a spreadsheet, and inspect its url to find its document identifier: *docs.google.com/spreadsheets/d/`spreadsheet_id`/edit*.

Share the spreadsheet with the service account's email address in a "can edit" role.

## Contributing

Browse existing [issues](https://github.com/data-creative/google-driver-ruby/issues) or create a new issue to communicate bugs, desired features, etc.

After forking the repo and pushing your changes, create a pull request referencing the applicable issue(s).

### Developing

After checking out the repo, run `bin/setup` to install dependencies.

### Testing

Add the following environment variables to your .bash_profile:

 + GOOGLE_DRIVER_APP_NAME
 + GOOGLE_DRIVER_EMAIL
 + GOOGLE_DRIVER_KEY_FILE_NAME

Store a real service account .json key file in the **spec/key_file/** directory.

Run `rake rspec` or `bundle exec rspec spec/` to run the tests.

Optionally run `bin/console` for an interactive prompt that will allow you to experiment.

### Releasing

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## [License](LICENSE.txt)
