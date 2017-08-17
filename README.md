# Unofficial Infusionsoft API Ruby Wrapper

<a href="https://app.codesponsor.io/link/Z24Ypyn8iC1Q4i6uCwNyLW3r/cavneb/infusionsoft_legacy" rel="nofollow"><img src="https://app.codesponsor.io/embed/Z24Ypyn8iC1Q4i6uCwNyLW3r/cavneb/infusionsoft_legacy.svg" style="width: 888px; height: 68px;" alt="Sponsor" /></a>

Allows for usage of the Infusionsoft XML-RPC API using Ruby's XML-RPC library. Find more info at http://help.infusionsoft.com/developers/api-basics/

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'infusionsoft_legacy'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install infusionsoft_legacy

## Usage

Each example below requires initializing a new InfusionsoftLegacy client

```ruby
infusionsoft = InfusionsoftLegacy.new("Infusionsoft Account Name", "API Key Goes Here")
```

##### Add Contact

```ruby
contact = { FirstName: "John", LastName: "Doe", Email: "johndoe@email.com" }
infusionsoft.ContactService("add", contact)
# => ...
```

##### Merge two duplicate contacts

```ruby
contact_id           = 56
duplicate_contact_id = 57
infusionsoft.ContactService("merge", contact_id, duplicate_contact_id)
# => ...
```

##### Query a contact using data service

```ruby
table         = "Contact"
return_fields = ["Id", "FirstName"]
query         = { FirstName: "John" }
limit         = 10
page          = 0
infusionsoft.DataService("query", table, limit, page, query, return_fields)
# => ...
```

##### Return a products inventory using product service

```ruby
product_id = 1
infusionsoft.ProductService("getInventory", product_id)
```

##### Charge an invoice using the invoice service

```ruby
invoice_id          = 16
notes               = "API Upsell Payment"
credit_card_id      = 2
merchant_account_id = 1
bypass_commissions = false
infusionsoft.InvoiceService("chargeInvoice", invoice_id, notes, credit_card_id, merchant_account_id, bypass_commissions)
```

##### Send an email using the email service

```ruby
contact_list = [123, 456, 789]
from_address = "john@test.com"
to_address   = "~Contact.Email~"
cc_address   = ""
bcc_address  = ""
content_type = "Text"
subject      = "This is just a test email, relax!"
html_body    = ""
text_body    = "This is the contant for the email"
infusionsoft.APIEmailService("sendEmail", contact_list, from_address, to_address, cc_address, bcc_address, content_type, subject, html_body, text_body)
# => ...
```

##### Get all report columns using the search service

```ruby
saved_search_id = 3
user_id         = 1
infusionsoft.SearchService("getAllReportColumns", savedSearchId, userId)
# => ...
```

##### Get all shipping options with the shipping service

```ruby
infusionsoft.ShippingService("getAllShippingOptions")
# => ...
```

##### Get affiliate payouts info using filter with the affiliate service

```ruby
from datetime import datetime
affiliateId = 2
filterStartDate = datetime(2012, 10, 18)
filterEndDate = datetime(2012, 10, 23)
print(infusionsoft.APIAffiliateService('affPayouts', affiliateId, filterStartDate, filterEndDate))
```

##### Get the download URL of a particular file

```ruby
file_id = 23
infusionsoft.FileService("getDownloadUrl", file_id)
# => ...
```

##### Using the library server method to access the API : Create a contact

```ruby
contact = { FirstName: "John", LastName: "Doe", Email: "johndoe@email.com" }
infusionsoft.server.ContactService.add(infusionsoft.key, contact)
# => ...
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/cavneb/infusionsoft_legacy. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the InfusionsoftLegacy project’s codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/cavneb/infusionsoft_legacy/blob/master/CODE_OF_CONDUCT.md).
