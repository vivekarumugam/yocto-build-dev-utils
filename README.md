# Yocto Build and Dev Utils

This is a collection of simple utilities for yocto based development

# .vybashrc
    * Keep this under $HOME dir
    * Update $HOME/.bashrc to include .vybashrc
      (add 'source ~/.vybashrc' without quotes at the end of the file)
    * You can have a $HOME/vybashrc_config file to customize the configs

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
