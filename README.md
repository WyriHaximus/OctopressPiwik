
# puppet-wifi

A Puppet module to configure and manage Wi-Fi access points on Linux systems.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
  - [Basic Configuration](#basic-configuration)
  - [Advanced Configuration](#advanced-configuration)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Overview

The `puppet-wifi` module allows you to automate the setup and management of Wi-Fi access points using Puppet. It supports various Linux distributions and provides a declarative approach to network configuration.

## Features

- **Access Point Configuration**: Define SSID, security settings, and IP addressing.
- **Multiple Interface Support**: Manage multiple Wi-Fi interfaces simultaneously.
- **Security Protocols**: Configure WPA2, WPA3, and open networks.
- **Static and Dynamic IP Addressing**: Support for both static IP and DHCP configurations.
- **Service Management**: Ensure that the necessary services are enabled and started.
- **Cross-Platform Compatibility**: Works across various Linux distributions.

## Requirements

- Puppet 6.0 or higher
- Linux-based operating system with `hostapd` and `dnsmasq` installed
- Root privileges for network configuration

## Installation

To install the module, use the following command:

```bash
puppet module install opus-codium-wifi
````

## Usage

### Basic Configuration

To set up a simple Wi-Fi access point:

```puppet
class { 'wifi':
  ssid            => 'MyNetwork',
  security        => 'wpa2',
  passphrase      => 'securepassword',
  interface       => 'wlan0',
  ip_address      => '192.168.1.1',
  netmask         => '255.255.255.0',
  gateway         => '192.168.1.254',
}
```

### Advanced Configuration

For more complex setups, such as multiple interfaces or advanced security settings:

```puppet
class { 'wifi':
  interfaces => [
    {
      name        => 'wlan0',
      ssid        => 'Network1',
      security    => 'wpa3',
      passphrase  => 'password1',
      ip_address  => '192.168.1.1',
      netmask     => '255.255.255.0',
      gateway     => '192.168.1.254',
    },
    {
      name        => 'wlan1',
      ssid        => 'Network2',
      security    => 'wpa2',
      passphrase  => 'password2',
      ip_address  => '192.168.2.1',
      netmask     => '255.255.255.0',
      gateway     => '192.168.2.254',
    },
  ],
}
```

## Testing

To test the module, you can use the included RSpec tests:

```bash
bundle install
bundle exec rake spec
```

Ensure that you have the necessary dependencies installed before running the tests.

## Contributing

Contributions are welcome! Please fork the repository, create a new branch, and submit a pull request with your changes. Ensure that your code adheres to the existing style and includes appropriate tests.

## License

This module is licensed under the Apache-2.0 License. See the [LICENSE](LICENSE) file for more details.
