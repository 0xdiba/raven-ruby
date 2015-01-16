0.12.3
------

- URL query parameters are now sanitized for sensitive data [pcorliss, #275]
- Raven::Client can now use a proxy server when sending events to Sentry [dcramer, #277]
- Raven::Client will now use a timed backoff strategy if the server fails [codekitchen, #267]
- Automatic integration loading is now a lot less brittle [dcramer, handlers, #263, #264]
- Fixed some issues with prefixes and DSN strings [nateberkopec, #259]
- If Raven is initialized without a server config, it will no longer send events [nateberkopec, #258]
- Slightly nicer credit-card-like number scrubbing [nateberkopec, #254]
- Fix some exceptions not being caught by Sidekiq middleware [nateberkopec, #251]
- Uncommon types are now encoded correctly [nateberkopec, #249]

0.12.2
------

- Security fix where exponential numbers in specially crafted params could cause a CPU attack [dcramer, #262]

0.12.1
------

- Integrations (Sidekiq, DelayedJob, etc) now load independently of your Gemfile order. [nateberkopec, #236]
- Fixed bug where setting tags mutated your configuration [berg, #239]
- Fixed several issues with SanitizeData and UTF8 sanitization processors [nateberkopec, #238, #241, #244]

0.12.0
------

- You can now give additional fields to the SanitizeData processor. Values matched are replaced by the string mask (*********). Full documentation (and how to use with Rails config.filter_parameters) [here](https://github.com/getsentry/raven-ruby/wiki/Advanced-Configuration#sanitizing-data-processors). [jamescway, #232]
- An additional processor has been added, though it isn't turned on by default: RemoveStacktrace. Use it to remove stacktraces from exception reports. [nateberkopec, #233]
- Dependency on `uuidtools` has been removed. [nateberkopec, #231]

0.11.2
------

- Fix some issues with the SanitizeData processor when processing strings that look like JSON


0.11.1
------

- Raven now captures exceptions in Rake tasks automatically. [nateberkopec, troelskn #222]
- There is now a configuration option called ```should_send``` that can be configured to use a Proc to determine whether or not an event should be sent to Sentry. This can be used to implement rate limiters, etc. [nateberkopec, #221]
- Raven now includes three event processors by default instead of one, which can be turned on and off independently. [nateberkopec, #223]
- Fixed bug with YAJL compatibility. [nateberkopec, #223]

0.10.1
------

- Updated to RSpec 3.
- Apply filters to encoded JSON data.


0.10.0
------

- Events are now sent to Sentry in all environments. To change this behavior, either unset ```SENTRY_DSN``` or explicitly configure it via ```Raven.configure```.
- gzip is now the default encoding
- Removed hashie dependency


0.9.0
-----

- Native support for Delayed::Job [pkuczynski, #176]
- Updated to Sentry protocol version 5


0.5.0
-----
- Rails 2 support [sluukonen, #45]
- Controller methods in Rails [jfirebaugh]
- Runs by default in any environment other than test, cucumber, or development. [#81]
