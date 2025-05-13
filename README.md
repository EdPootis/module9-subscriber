# Advanced Programming Module 9 Subscriber
**Nama: Edmond Christian**<br>
**NPM: 2306208363**

### Reflection 1
a. What is amqp?
- AMQP (Advanced Message Queuing Protocol) adalah standar protokol komunikasi untuk *message-oriented middleware* yang dibuat untuk memungkinkan pertukaran pesan antar aplikasi yang berbeda dalam sistem terdistribusi. AMQP mendefinisikan aturan komunikasi antara *messaging provider* dan *client*, sehingga berbagai implementasi dari protokol ini tetap dapat saling berkomunikasi secara konsisten dan aman walaupun dibuat dengan bahasa pemrograman/platform yang berbeda. AMQP menggunakan model komunikasi berbasis *exchange* dan *queue* yang fleskibel. Sebuah aplikasi akan mengirim/*publish* pesan ke *exchange*, lalu broker AMQP akan meneruskan pesan tersebut ke satu atau lebih *queue* berdasarkan *routing key* dan *binding* yang telah diatur. Selanjutnya, *consumer* akan mengambil pesan dari *queue*, memprosesnya, dan mengirimkan kembali "acknowledgment" ke broker. Contoh broker yang menggunakan AMQP adalah RabbitMQ, Apache Qpid, dan Apache ActiveMQ

b. What does it mean? `guest:guest@localhost:5672` , what is the first **guest**, and what is the second **guest**, and what is **localhost:5672** is for?
- `guest:guest@localhost:5672` adalah URL koneksi untuk menyambung ke AMQP broker seperti RabbitMQ yang dijalankan di lokal. **guest** pertama adalah username yang ingin digunakan untuk *login*. **guest** kedua adalah password yang ingin digunakan. Dan **localhost:5672** menunjukkan bahwa koneksi ditujukan ke komputer local (`localhost`) di port 5672, yang juga merpakan **default port** untuk protokol AMQP.

### Slow Subscriber Simulation
![Slow Subscriber Graph](SlowSubscriber.png)
Pada simulasi *slow subscriber* saat *publisher* mengirim pesan, maka juga akan terjadi lonjakan pada grafik pertama yang menandakan *queued messages*. Hal ini terjadi karena sekarang *subscriber* disimulasikan untuk lambat dalam memproses pesan atau event yang dikirim *publisher* sehingga  kecepatan *subscriber* meng-*consume* pesan lebih kecil dari kecepatan *publiher* meng-*publish* pesannya. Akibatnya saat saya jalankan publisher 8 kali, grafik mencatat *queued messages* terbanyak sebanyak 36 pesan.
