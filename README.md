# Oracle Cloud Thrifty Mod for Steampipe

An Oracle Cloud cost savings and waste checking tool.

Run checks in a dashboard:

![image](https://raw.githubusercontent.com/turbot/steampipe-mod-oci-thrifty/main/docs/oci_thrifty_dashboard.png)

Includes checks for:

- Underused **Autonomous Databases**
- Unused, underused and oversized **Compute Instances**
- Unused, underused and oversized **Block Volumes** and **Backups**
- **Object Storage Buckets** without lifecycle policies
- Unattached **Network Public IPs**
- [#TODO List](https://github.com/turbot/steampipe-mod-oci-thrifty/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22)

## Getting started

### Installation

Download and install Steampipe (https://steampipe.io/downloads). Or use Brew:

```sh
brew tap turbot/tap
brew install steampipe
```

Install the Oracle Cloud plugin with [Steampipe](https://steampipe.io):

```sh
steampipe plugin install oci
```

Clone:

```sh
git clone https://github.com/turbot/steampipe-mod-oci-thrifty.git
cd steampipe-mod-oci-thrifty
```

### Usage

Start your dashboard server to get started:

```sh
steampipe dashboard
```

By default, the dashboard interface will then be launched in a new browser
window at https://localhost:9194. From here, you can run benchmarks by
selecting one or searching for a specific one.

Instead of running benchmarks in a dashboard, you can also run them within your
terminal with the `steampipe check` command:

Run all benchmarks:

```sh
steampipe check all
```

Run a single benchmark:

```sh
steampipe check benchmark.compute
```

Run a specific control:

```sh
steampipe check control.compute_instance_long_running
```

Different output formats are also available, for more information please see
[Output Formats](https://steampipe.io/docs/reference/cli/check#output-formats).

### Credentials

This mod uses the credentials configured in the [Steampipe OCI plugin](https://hub.steampipe.io/plugins/turbot/oci).

### Configuration

Several benchmarks have [input variables](https://steampipe.io/docs/using-steampipe/mod-variables) that can be configured to better match your environment and requirements. Each variable has a default defined in its source file, e.g., `controls/compute.sp`, but these can be overwritten in several ways:

- Copy and rename the `steampipe.spvars.example` file to `steampipe.spvars`, and then modify the variable values inside that file
- Pass in a value on the command line:

  ```sh
  steampipe check benchmark.block_volume --var=boot_and_block_volume_max_size_gb=100
  ```

- Set an environment variable:

  ```sh
  SP_VAR_boot_and_block_volume_max_size_gb=100 steampipe check control.boot_and_block_volume_large
  ```

  - Note: When using environment variables, if the variable is defined in `steampipe.spvars` or passed in through the command line, either of those will take precedence over the environment variable value. For more information on variable definition precedence, please see the link below.

These are only some of the ways you can set variables. For a full list, please see [Passing Input Variables](https://steampipe.io/docs/using-steampipe/mod-variables#passing-input-variables).

## Contributing

If you have an idea for additional controls or just want to help maintain and extend this mod ([or others](https://github.com/topics/steampipe-mod)) we would love you to join the community and start contributing.

- **[Join our Slack community →](https://steampipe.io/community/join)** and hang out with other Mod developers.

Please see the [contribution guidelines](https://github.com/turbot/steampipe/blob/main/CONTRIBUTING.md) and our [code of conduct](https://github.com/turbot/steampipe/blob/main/CODE_OF_CONDUCT.md). All contributions are subject to the [Apache 2.0 open source license](https://github.com/turbot/steampipe-mod-oci-thrifty/blob/main/LICENSE).

Want to help but not sure where to start? Pick up one of the `help wanted` issues:

- [Steampipe](https://github.com/turbot/steampipe/labels/help%20wanted)
- [OCI Thrifty Mod](https://github.com/turbot/steampipe-mod-oci-thrifty/labels/help%20wanted)
