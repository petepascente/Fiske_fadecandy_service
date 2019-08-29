#!/bin/bash
#title        : fadecandy
#description  : start/stop/restart fadecandy
#########################################
### install   : cp fadecandy /etc/init.d/
#               update-rc.d fadecandy defaults
### uninstall : update-rc.d -f fadecandy remove
### BEGIN INIT INFO
# Provides: fadecandy
# Required-Start:
# Required-Stop:
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: fadecandy
# Description: Fadecandy USB service
### END INIT INFO
FC_SCRIPT=/bin/fc_script.sh
PID_FILE=/tmp/fadecandy.pid

case "$1" in
    start)
        echo "Starting fadecandy service..."

        COMMAND_TO_RUN=`start-stop-daemon -S -b -m -p $PID_FILE -x $FC_SCRIPT& :`
        setsid sh -c $COMMAND_TO_RUN> /dev/null 2>&1 < /dev/null

        echo -e "\E[31;33m[ OK ]\E[0m"
        ;;
    stop)
        echo "Stopping fadecandy service..."

        start-stop-daemon -K -q -p $PID_FILE

        echo -e "\E[31;33m[ OK ]\E[0m"
        ;;
    restart|reload)
        "$0" stop
        "$0" start
        ;;
    *)
        echo $"Usage: $0 {start|stop|restart}"
        exit 1
esac

exit $?