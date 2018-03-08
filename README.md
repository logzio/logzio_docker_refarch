Logz.io Docker Log Shipping Reference Architecture

The recommended approach for shipping logs from Docker containers to utilize the Docker JSON File logging driver and FluentD. Logz.io accepts many different methods of shipping, but provides more extended configuration references for the recommended approach below.

Requirements
fluent-plugin-logzio	Fluentd	Ruby
>= 0.0.15	>= v0.14.0	>= 2.1
< 0.0.15

Getting Started
Install Fluentd
gem install fluent-plugin-logzio
Make sure you have an account with Logz.io.
