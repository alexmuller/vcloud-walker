# vCloud Walker

vcloud-walker is a command line tool to describe different VMware vCloud
Director 5.1 entities. It uses [fog][] under the hood.

[fog]: http://fog.io/

## Installation

Add this line to your application's Gemfile:

    gem 'vcloud-walker'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install vcloud-walker

## Usage
Run `vcloud-walk` to get usage information.

You can perform the following operations with vcloud-walker.

#### Walk VDCs (virtual data centres):
    vcloud-walk vdcs

describes all VDCs within a given organization. This includes vApp, VM and network
information.

#### Walk catalogs:
    vcloud-walk catalogs

describes all catalogs and catalog items within a given organization.

#### Walk organization networks:
     vcloud-walk networks

describes all organization networks.

#### Walk Edge Gateways:
    vcloud-walk edgegateways

describes all Edge Gateways for given organization. Each Edge Gateway includes
configuration for firewall, load balancer and NAT services.

#### Walk an entire organization:
     vcloud-walk organization

describes the entire organization, which includes Edge Gateway, catalogs,
networks and VDCs within an organization.

## Credentials

Please see the [vcloud-tools usage documentation](https://gds-operations.github.io/vcloud-tools/usage/)
for instructions on how to authenticate with vCloud Director.

## Output

Walker can output data in JSON or YAML format. The default output format is JSON.
You can use command line option ```--yaml``` for YAML output.

Find sample JSON output in the [docs/examples/](/docs/examples) directory.

## The vCloud API

vCloud Tools currently use version 5.1 of the [vCloud API](http://pubs.vmware.com/vcd-51/index.jsp?topic=%2Fcom.vmware.vcloud.api.doc_51%2FGUID-F4BF9D5D-EF66-4D36-A6EB-2086703F6E37.html). Version 5.5 may work but is not currently supported. You should be able to access the 5.1 API in a 5.5 environment, and this *is* currently supported.

The default version is [defined in fog](https://github.com/fog/fog/blob/244a049918604eadbcebd3a8eaaf433424fe4617/lib/fog/vcloud_director/compute.rb#L32).

If you want to be sure you are pinning to 5.1, or use 5.5, you can set the API version to use in your fog file, e.g.

`vcloud_director_api_version: 5.1`

## Debugging

`export EXCON_DEBUG=true` - this will print out the API requests and responses.

`export DEBUG=true` - this will show you the stack trace when there is an exception instead of just the message.

## Testing

Run the default suite of tests (e.g. lint, unit, features):

    bundle exec rake

Run the integration tests (slower and requires a real environment):

    bundle exec rake integration
