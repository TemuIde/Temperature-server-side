# Smart Body Temperature Scanner

Repositori aplikasi server-side untuk proyek prototip Smart Body Temperature Scanner. 

Reference: https://iotbytes.wordpress.com/store-mqtt-data-from-sensors-into-sql-database/ && https://github.com/pradeesi/Store_MQTT_Data_in_Database


## Main Development Files
Aplikasi server side bekerja sebagai listener dan virtual MQTT broker. Terdapat tiga file Python dan satu file service dalam repositori ini:

1. GeneralListener.py: Aplikasi utama, dijalankan sebagai daemon pada server. Berfungsi sebagai listener MQTT utama. Semua koneksi MQTT akan diterima oleh aplikasi ini, untuk kemudian diolah sesuai tipenya. Tipe MQTT message dikelola berdasarkan topic dari message. Secara konsepnya, aplikasi ini berlaku sebagai proxy MQTT broker.

2. CheckConnHandler.py: Berisi kumpulan fungsi yang memiliki peran mengirimkan informasi koneksi dan waktu serta tanggal kepada sensor

3. Gateway.py: Berisi kumpulan fungsi yang memiliki peran pengolahan data suhu tubuh yang dikirimkan sensor. 

4. general-listener-service.service: Pengaturan untuk menjalankan aplikasi GeneralListener sebagai daemon service

## Past-Development Files

1. DBInitializer.py: create database, useful for future database reset needs

2. ListenerMQTT.py: listens to published messages from the server's mqtt broker (port 1883)

3. PublisherMQTT.py: mqtt client, publishes dummy data for testing purpose

4. SensorDataToDB.py: mqtt client, subscribes to certain topics then store data to database
<!-- 
Program listener di execute sebagai client listener, kemudian akan kirim data yang diterima ke function di file SensorDataToDB



Run listener as background process (https://janakiev.com/blog/python-background/):

1. Now you can run the script with nohup which ignores the hangup signal. This means that you can close the terminal without stopping the execution. Also, don’t forget to add & so the script runs in the background:

nohup /path/to/test.py &

2. The output will be saved in the nohup.out file, unless you specify the output file like here:

   nohup /path/to/test.py > output.log &

   nohup python /path/to/test.py > output.log &

3. You can find the process and its process Id with this command:

   ps ax | grep test.py

4. If you want to stop the execution, you can kill it with the kill command:

   kill PID

5. It is also possible to kill the process by using pkill, but make sure you check if there is not a different script running with the same name:

   pkill -f test.py -->
