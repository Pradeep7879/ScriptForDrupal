# ScriptForDrupal
This Script help you to setup Project and required Modules
===============================================================

    #!/bin/bash
    # Ask the user for their name
    echo "Hello, who am I talking to?";
    echo -e '\t';
    read varname

    echo -e "It's nice to meet you $varname \n";

    echo $varname "What is your Drupal project Name."
    echo "Please Enter here: $projectName"
    read projectName

    echo -e $varname "your Project Name is $projectName \n";

    composer create-project drupal/recommended-project:9.2.1 $projectName

    cp -r web/sites/default/default.settings.php web/sites/default/settings.php

    mkdir web/sites/default/files
    chmod -R 777 web/sites/default/files

    echo -e "Go on the browser, hit the URL:- localhost/$projectName/web/ \n"
    echo -e "Once you Setup the project, go on the next comeback on this terminal and press Enter Key\n"
    echo -e "please install the Drush to run some addtional commands on your terminal ex: cache clear, module enable and disable \n"
    cd $projectName

    read -s -n 1 key  # -s: do not echo input character. -n 1: read only 1 character (separate with space)

    # double brackets to test, single equals sign, empty string for just 'enter' in this case...
    # if [[ ... ]] is followed by semicolon and 'then' keyword
    if [[ $key = "" ]]; then 
        echo 'You pressed enter!'
    else
        echo "You pressed '$key'"
    fi


    composer require drush/drush
    ./vendor/drush/drush/drush cr

    composer require 'drupal/admin_toolbar:^3.0'
    ./vendor/drush/drush/drush en admin_toolbar
