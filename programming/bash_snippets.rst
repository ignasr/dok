bash snippets
=============

100% Load 4 CPU cores 
---------------------

.. code-block:: bash

    for i in 1 2 3 4; do while : ; do : ; done &  done

show my ip
----------

.. code-block:: bash

   $ dig +short myip.opendns.com @resolver1.opendns.com

template
--------

.. code-block:: bash

    #!/bin/bash
    
    # ./script [-t DAYS] -a AGE -d DIR
    #   -t today date
    # ex: ./script -a 366 -d /srv/log
    
    DAY_ZERO=0
    LOG_DIR="/usr/local/empty"
    SCRIPT_DIR=$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )
    # Logging tag
    LTAG="$(basename $0)[$$]"
    
    do_log() {
        logger -t $LTAG "$*"
    }
    
    do_log "Started with params $*"
    
    # Script params
    while [ "$#" -ge "2" ] ; do
        case $1 in
            -t)
                DAY_ZERO=$2
                shift 2 ;;
            -a)
                AGE=$2
                shift 2 ;;
            -d)
                LOG_DIR=$2
                shift 2 ;;
            *) shift 1 ;;
        esac
    done
    
    find_in_dir() {
    }
    
    find_in_dir $LOG_DIR $AGE
    
    do_log "Finished."
    
    exit 0

