# Yocto Build and Dev Utils

This is a collection of simple utilities for yocto based development

# .vybashrc
    * Keep this under $HOME dir
    * Update $HOME/.bashrc to include .vybashrc
      (add 'source ~/.vybashrc' without quotes at the end of the file)
    * You can have a $HOME/vybashrc_config file to customize the configs

    # Usage
        * you can view the list of settings through 'shwset' (show settings)
        * you can set/unset certain setttings with alias given below
            -> scou / uscou         [Set/Unset Copy on Update, default=1]
            -> sstrip / usstrip     [Set/Unset Strip, default=1]
            -> sdrun / usdrun       [Set/Unset Dry Run, default=1]
        * also you can set certain params with alias given below
            -> sstbip 123.123.123.123   [Set STB IP, default=192.168.2.62 :)]
            -> sstbuser <stb_usr_name>  [Set STB User Name, default=root]
            -> sstbroot <stb_root_dir>  [Set STB Root Dir, default=/]
               This will allow you to copy binaries to relative to different dir than "/"
            -> log levels
                * svylln [Set Log Level - VY_LOG_LEVEL_NONE      (0) ]
                * svylle [Set Log Level - VY_LOG_LEVEL_ERROR     (1) ]
                * svyllw [Set Log Level - VY_LOG_LEVEL_WARN      (2) ]
                * svylli [Set Log Level - VY_LOG_LEVEL_INFO      (3) ]
                * svylld [Set Log Level - VY_LOG_LEVEL_DEBUG     (4) ]
                * svyllv [Set Log Level - VY_LOG_LEVEL_DEBUG_VAR (5) ]

# Sample vybashrc_config
    _cou=1
    _strip=1
    _dryrun=1
    _stb_ip=192.168.2.62
    _stb_user=root
    _stb_root=/
    VY_LOG_LEVEL=3

# flash_dev
    * Keep this file under any $PATH directory

# Updating publick key of system to STB
    To update your system public key to STB in order to carry out
    passwordless SCP, please follow the below steps

    ssh-copy-id <user>@<machine_ip>
     e.g ssh-copy-id root@192.168.2.62

    (or)

    cat ~/.ssh/id_rsa.pub | ssh <user>@<machine_ip> "mkdir -p ~/.ssh && cat >>  ~/.ssh/authorized_keys"
     e.g cat ~/.ssh/id_rsa.pub | ssh root@192.168.2.62 "mkdir -p ~/.ssh && cat >>  ~/.ssh/authorized_keys"


   Note :
   * In case of PaceXG1V3 boxes, remember to update iptables to accept all input packets (iptales -P INPUT ACCEPT)

   * Ensure dropbear is running (dropbear -p 0:22)

   * In some cases dropbear may display a warning banner about authorized (during scp/ssh)
     -> Remove the '-p xyz' parameter of dropbear /lib/systemd/system/dropbear.service
     -> Otherwiser trim the banner file ( 'echo "" > <the_banner_file>' )
