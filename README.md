# Backup everything using your telegram bot.


A script to create a backup of the files of the html directory and mysql and sending it to your telegram group.

Originally designed for Wordpress it will also work for others.

In our use case all applications are installed under /home/ and telegram_backup in /usr/local/bin. Lets say we have a Wordpress app in /home/wordpress and a non Wordpress web app in /home/webapp. The web roots are in /home/wordpress/html and /home/webapp/html. The Wordpress app is owned by user wordpress and the web app by user webapp.

You need to provide your telegram_apikey and telegram_chat_id on the command line. This will show up in the bash history if run manually, but not if run as cron which is what we do.

- Install Telegram,
- Create a Bot using the Telegram BotFather
- Follow the prompts, and finally copy it’s API Token,
- Create a Group,
- Add the Bot to it,
- Select the Bot User from the Group members list,
- Press the SEND MESSAGE button (to send the start),
- Send the User a message.
- Visit https://codesandbox.io/s/get-telegram-chat-id-q3qkk
- Check the js code if you like in the sandbox before putting your token in
- Retrieve the Chat ID from the chat data using this tool.
 

# Usage:
```
telegram_backup [OPTION]...

Backup Wordpress Codebase + Database.
Version 0.1.0

    Options:
        -tc,    --telegram-chat-id   Telegram chat_id - mandatory
        -tt,    --telegram-bot-token Telegram bot token - mandatory
        -bd,    --dir-to-backup      Directory to backup - default=/home/wordpress/html
        -bs,    --storage-dir        Backup storage directory - default=/home/userdir/backups
        -uc,    --use-mysql-config   Use MySQL config file (~/.my.cnf)
        -bn,    --backup-name        Backup filename without extension - default userdir
        -bk,    --backup-keep-days   Days of backup to keep in storage - default 0 (none)
        -nw,    --not-wordpress      This is not a workdpress backup - default is wordpress
        -dh     --database-host      Database host - mandatory for not wordpress unless using MySQL config
        -dn     --database-name      Database name - mandatory for not wordpress unless using MySQL config
        -dp     --database-pass      Database name - mandatory for not wordpress unless using MySQL config
        -h,     --help               Display this help and exit
        -v,     --version            Output version information and exit

    Minimal example for Wordpress:
    telegram_backup --telegram-chat-id=569502265 --telegram-bot-token=UU7grZ_ZunE-9ijNeq5dmE4t-u85gTzrNdc

    Minimal example for other web apps:
    telegram_backup --not-wordpress --use-mysql-config --telegram-chat-id=569502265 --telegram-bot-token=UU7grZ_ZunE-9ijNeq5dmE4t-u85gTzrNdc
```
