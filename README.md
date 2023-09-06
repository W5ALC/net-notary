# net-notary

AllStar/Hamvoip Node Cron Job Setup Script

------------------------------------------

![net-notary](https://github.com/W5ALC/ARES/blob/main/net-notary-new.gif?raw=true)

This Bash script simplifies the process of setting up cron jobs for connecting and disconnecting AllStarLink nodes on your system. It is designed to work on both Arch Linux and Debian-based systems, ensuring compatibility.

------------------------------------------

# Table of Contents:

1. Introduction
2. Prerequisites
3. Usage
4. Main Node Number
5. Cron Job Configuration

------------------------------------------

# Introduction:

This script streamlines the setup of cron jobs for managing AllStarLink nodes. It prompts you for the necessary information to create cron entries for connecting and disconnecting nodes, making it easier to automate these tasks.

------------------------------------------

# Installation:
for ASL systems:

```
curl -s https://raw.githubusercontent.com/W5ALC/net-notary/main/net-notary | sudo bash -c 'cat > /usr/local/sbin/net-notary && chmod +x /usr/local/sbin/net-notary'
```

for Hamvoip systems:

```
curl -s https://raw.githubusercontent.com/W5ALC/net-notary/main/net-notary | bash -c 'cat > /usr/local/sbin/net-notary && chmod +x /usr/local/sbin/net-notary'
```


# Usage:  MUST BE RAN AS ROOT

1. Run the script using the following command or with the flag "-c" for connects only or "-d" for disconnects only
```
   # net-notary
```
![net-notary](https://github.com/W5ALC/ARES/blob/main/net-notary.png)

```
   # net-notary -c    # for connect only cron entries
```
![net-notary-c](https://github.com/W5ALC/ARES/blob/main/net-notary-c.png)

```
   # net-notary -d    # for disconnect only cron entries
```
![net-notary-d](https://github.com/W5ALC/ARES/blob/main/net-notary-d.png)

------------------------------------------

2. Follow the prompts to provide the required information for cron job setup:
```
    # net-notary
```
```
Enter AllStarLink node number to connect: 29332

Enter hour to connect (0-23): 10

Enter minute to connect (0-59): 30

Enter hour to disconnect (0-23): 13

Enter minute to disconnect (0-59): 30

Enter days of the week for connections (1-7 or * for everyday 1=Monday): *
```

# Connects only

1. Run the script using the following command:
```
   # net-notary -c
```

2. Follow the prompts to provide the required information for cron job setup:
```
Enter AllStarLink node number to connect: 29332

Enter hour to connect (0-23): 10

Enter minute to connect (0-59): 30

Enter days of the week for connections (1-7 or * for everyday 1=Monday): *
```

# Disconnects only

1. Run the script using the following command:
```
   # net-notary -d
```

2. Follow the prompts to provide the required information for cron job setup:
```
Enter AllStarLink node number to disconnect: 29332

Enter hour to disconnect (0-23): 10

Enter minute to disconnect (0-59): 30

Enter days of the week for disconnections (1-7 or * for everyday 1=Monday): *
```



3. The script will automatically create cron entries for connecting and disconnecting the specified node based on your input.

------------------------------------------

Main Node Number:

The script extracts the main node number from the /etc/asterisk/rpt.conf file. Make sure this file exists and is properly configured for accurate results.

------------------------------------------

# Cron Job Configuration:

The script constructs the cron commands for connecting and disconnecting nodes and adds them to your user's crontab. The commands are scheduled to run at the specified times and days of the week.

Here's an example of the generated cron entries:

------------------------------------------

```
Connect:    30 10 * * * asterisk -rx "rpt fun 49947 *329332"

Disconnect: 30 13 * * * asterisk -rx "rpt fun 49947 *129332"
```
------------------------------------------

Feel free to customize this script to suit your specific needs and requirements. Happy automating your AllStarLink nodes!

