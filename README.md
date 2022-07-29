# pact-ruby-demo
Demo repo for Consumer Driven Contract Tests using Pact

A proof of concept of [Consumer Driven Contract Testing](https://pactflow.io/what-is-consumer-driven-contract-testing/) for a message based (non-HTTP) producer and consumer relationship using the `pact-message-ruby` gem.

Pact already supports [non-HTTP interactions and contracts](https://docs.pact.io/getting_started/how_pact_works#non-http-testing-message-pact) in most languages. An official [pact-message-ruby](https://github.com/pact-foundation/pact-message-ruby) gem has existed for several years.

## Scenario

This POC focuses on a hypothetical situation where a potential breaking change has been introduced to a message schema.

The consumer is expecting a message containing a `last_name` field, however this field has been renamed. The producer is now sending messages with a `surname` field.

## Usage

_Running consumer side tests and generating a contract_

1. Execute the consumer side test for the `TestMessageConsumer`.

`bundle exec rspec`

2. The consumer side test should pass.
3. A contract file will be created representing the consumers expectations of the message format.

_Running provider side verification of the contract_

1. Execute the Pact verification Rake task.

`bundle exec rake pact:verify`

2. The RSpec tests generated by the Pact provider side verification task should fail.
