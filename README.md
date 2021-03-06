# thingsboard-data-migration
This tool performs data migration between two different instances of ThingsBoard, regardless of the technology used for the database.
<br>
It also allows the transfer of data between two different devices of the same ThingsBoard instance.
<br>
The tool exploits the native ThingsBoard <i>HTTP APIs</i> to retrive data, and the ThingsBoard <i>MQTT broker</i> to send data.

# How to use
usage: migration-script.py [-h] [-c CONFIGURATION] [-m MODE] -i 
       INITIALTS -f FINALTS -s SOURCEDEVICEID -t  
       TARGETDEVICETOKEN -k TIMESERIESKEY
       
Command example:<br>
<b>python</b> migration-script.py <b>-m</b> both <b>-c</b> ./migrationConf.yml <b>-i</b> 1546361494000 <b>-f</b> 1578415926000 <b>-s</b> dc872480-85e5-11e9-acf5-fb7ea3e0493d <b>-t</b> phhQnVa4nSKjyJ1QMwtx <b>-k</b> data_key

# Help
python migration-script.py --help

# Operating modes
You can perform three different operations with this script:
1) Fetch data via HTTP RESTful API (from source ThingsBoard instance) <i>and</i> send via MQTT (to target ThingsBoard instance) --> use argument "-m <b>both</b>", default behavior
2) Fetch data via HTTP RESTful API (from source ThingsBoard instance) and save in local file --> use argument "-m <b>fetch</b>"
3) Fetch data from local file and send via MQTT (to target ThingsBoard instance) --> use argument "-m <b>send</b>"

<i>*** IMPORTANT ***</i>
<br>
You shall always pass ALL the arguments, even if not used within the chosen operating mode. Next version of this script will include an automated argument check to allow the user specify only the strictly necessary ones.
