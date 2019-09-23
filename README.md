# NAME

check\_raspberry\_shake - check the status of a Raspberry Shake

# USAGE

**check\_raspberry\_shake** **-H** _host_ **-f** _function_…

# DESCRIPTION

**check\_raspberry\_shake** checks the status of several properties of a Raspberry
Shake.

# REQUIRED ARGUMENTS

The host 

# OPTIONS

- ** -?, -h, --help**

    Show help

- ** -v, --verbose**

    Be more verbose

- **--version**

    Show version and license

- **--function**

    Check for function:

    - status: Running or not
    - version: System software version, default warns if not 0.15
    - producer: Data Producer on or not
    - consumer: Data Consumer on or not
    - forwarding: Data Forwarding on or not
    - connected: Server Connection connected or not
    - uptime: System uptime in minutes, defaults warning 10
    critical 5
    - disk\_available: Disk space available in Mb, defaults warning 500
    critical 100
    - disk\_used: Disk space used in percentage, defaults warning 90
    critical 95
    - cpu\_temp: CPU temperature in degrees Celcius, defaults warning 80
    critical 85

# DIAGNOSTICS

- Could not retrieve page '%s' to get data
(E) The resource containing the data could not be retrieved from the host
- Could not get data from resource '%s' for function '%s'
(E) The resource containing the data could be retrieved from the host but the
requested data was not found in that object
- Unknown function '%s', must be one of connected, consumer, cpu\_temp,
disk\_available, disk\_used, forwarding, producer, status, uptime, version (E)
The requested function is not supported, must be one of the system properties
'connected', 'consumer', 'cpu\_temp', 'disk\_available', 'disk\_used',
'forwarding', 'producer', 'status', 'uptime' or 'version'.

# EXAMPLES

`check_raspberry_shake -H rs.local -f cpu_temp`

# DEPENDENCIES

Perl 5.16.0, Monitoring::Plugin, HTTP::Tiny, JSON, List::MoreUtils, Readonly,
English

# EXIT STATUS

The exist status is handled by the monitoring interface.

# CONFIGURATION

The default warning and critical thresholds should be overridden by the
standard -w and -c options of the monitoring interface because they depend on
the usage of the device. The defaults thresholds are:

- uptime 10: 1:
- disk\_available 500: 100:
- disk\_used 90 95
- cpu\_temp 80: 85:

# INCOMPATIBILITIES

There are no known incompatibilities but since the data is retrieved from an
API in an undefined format, a different system software version could present
the data in a different format which might break things. It is compatible with
system software version `0.15`.

# BUGS AND LIMITATIONS

The 'status' function only determines between 'RUNNING' and not.

The 'producer', 'consumer', 'forwarding' and 'connected' functions only
determines between 'ON'/'CONNECTED' and not.

Please report any bugs or feature requests at

[Issues for github.com](https://github.com/ipenburg/check_raspberry_shake/issues).

# AUTHOR

Roland van Ipenburg, <ipenburg@xs4all.nl>

# LICENSE AND COPYRIGHT

Copyright 2019 by Roland van Ipenburg
This program is free software; you can redistribute it and/or modify
it under the GNU General Public License v3.0.

# DISCLAIMER OF WARRANTY

BECAUSE THIS SOFTWARE IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY
FOR THE SOFTWARE, TO THE EXTENT PERMITTED BY APPLICABLE LAW. EXCEPT WHEN
OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER PARTIES
PROVIDE THE SOFTWARE "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER
EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE
ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE SOFTWARE IS WITH
YOU. SHOULD THE SOFTWARE PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL
NECESSARY SERVICING, REPAIR, OR CORRECTION.

IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING
WILL ANY COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY AND/OR
REDISTRIBUTE THE SOFTWARE AS PERMITTED BY THE ABOVE LICENSE, BE
LIABLE TO YOU FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL,
OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE
THE SOFTWARE (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING
RENDERED INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A
FAILURE OF THE SOFTWARE TO OPERATE WITH ANY OTHER SOFTWARE), EVEN IF
SUCH HOLDER OR OTHER PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF
SUCH DAMAGES.
