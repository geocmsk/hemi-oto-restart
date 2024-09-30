



```
#!/bin/bash

restart_count=0
restart_log="restart_log.txt"

while true; do
    # Start the application
    ./popmd

    # Increment the restart count and write to the log file
    ((restart_count++))
    echo "Restart $restart_count at $(date)" >> $restart_log

    # Uygulama çökerse veya durursa, döngü yeniden başlar
    echo "Uygulama durdu. 5 saniye sonra yeniden başlatılacak..."
    sleep 5
done
```
