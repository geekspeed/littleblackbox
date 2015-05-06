LittleBlackBox is a collection of thousands of private SSL and SSH keys extracted from various embedded devices. These private keys are stored in a database where they are correlated with their public certificates as well as the hardware/firmware that are known to use those private keys.

A command line utility is included to aid in the identification of devices or network traffic that use these known private keys. Given a public certificate, the utility will search the database to see if it has a corresponding private key; if so, the private key is displayed and can be used for traffic decryption or MITM attacks. Alternatively, it will also display a table of hardware and firmware that is known to use that private key.

The utility can obtain a public certificate several different ways:

  1. You may give it the path to a public SSL certificate file.
  1. You may give it the SHA1 hash of a public SSL/SSH certificate.
  1. Given a host, it will retrieve the host's public SSL certificate.
  1. Given a pcap file, it will parse the file looking for public SSL certificate exchanges.
  1. Given a live network interface, it will listen for public SSL certificate exchanges.