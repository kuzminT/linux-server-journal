## Add user
- useradd -m -U -s /bin/bash -G sudo holu
- passwd holu

All subsequent changes in the SSH configuration file refer to the following file: `/etc/ssh/sshd_config`.

## Tips
- [Moving /usr to another partition](http://yavin4.anshul.info/2006/07/17/moving-usr-to-another-partition/)
- 


## Deactivate webcam:
	
	sudo modprobe -r uvcvideo
	# To enable your webcam again
	sudo modprobe uvcvideo

## Change timezone

- [Смена часового пояса](https://vps.ua/wiki/change-time-zone/)


## Logs

    # redirect stderr to stdout
    
    ./aaa.sh 2>&1 | tee -a log
    ./aaa.sh |& tee -a log

## Архивация

        
        # Архивация файлов в gz-формате        
        tar cfvz archive.tar.gz *.php
        # Распаковка
        tar xfvz archive.tar.gz




