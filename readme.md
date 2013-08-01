# Stateless Password Manager

> **Warning: this is experimental software**

PWM is a statless password manager. With pwm, you can generate unique
passwords for each login using one master password; the unique passwords
will be generated using a key derivation function (PBKDF2), so there is
no data stored on your computer. Entering a wrong (or a different) master
password will simply generate a different unique password.

## Installation

If Python (>= 3.1.0) is installed properly, it is sufficient to simply
move the pwm executable to a place that appears in `$PATH`. E.g.:

    cp pwm /usr/bin/

## Parameters

PWM uses PBKDF2 with SHA512. The salt parameter is the unique password
identifier (argument: `--site`). The password length is 1.5 times the
length of the master password (rounded down towards negative infinity).
2^15-1 iterations of PBKDF2 are used to generate keys, which are then
encoded as BASE32 (lowercase and with the padding characters stripped).
