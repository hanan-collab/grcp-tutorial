# Reflection Tutorial-9 
## 1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?
1. **Unary:**
Metode paling sederhana, client mengirimkan satu permintaan dan menerima satu respon. Biasa digunakan untuk operasi singkat dan sederhana.
2. **Server-streaming:**
Server mengirimkan aliran data sebagai respon terhadap satu permintaan client. Ideal untuk skenario dimana server perlu mengirimkan banyak data secara bertahap, seperti streaming video atau log.
3. **Bi-directional streaming:**
Client dan server dapat saling mengirim dan menerima aliran data secara bersamaan. Cocok untuk aplikasi real-time seperti chat atau game online.

## 2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?
1. **Autentikasi:** Memastikan identitas client yang mengakses service. Metode umum seperti token atau sertifikat dapat digunakan.
2. **Otorisasi:** Mengontrol akses client ke resource tertentu berdasarkan level izin mereka.
3. **Enkripsi data:** Melindungi data yang dikirim antara client dan server dengan menggunakan teknik enkripsi seperti TLS.

## 3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?
1. **Kompleksitas pengelolaan aliran data:** Memastikan aliran data berjalan lancar dan menghindari masalah seperti buffer overflow.
2. **Penanganan backpressure:** Mengatur kecepatan pengiriman data untuk menghindari server kewalahan.
3. **Sinkronisasi:** Menjaga konsistensi data ketika kedua pihak mengirim dan menerima pesan secara simultan.

## 4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?
-  **Keuntungan:** Memungkinkan pengiriman respon secara bertahap, mengurangi beban memory server.
- **Kekurangan:** Menambah kompleksitas kode client untuk menangani aliran respon.

## 5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?
1. **Memisahkan service definition:** Gunakan file terpisah untuk mendefinisikan service dan message types.
2. **Membuat service struct terpisah:** Implementasikan logika service dalam struct khusus untuk setiap service.
3. **Menggunakan dependency injection:** Memudahkan pengujian dan penggantian komponen service.

## 6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?
1. **Integrasi dengan payment gateway:** Menghubungkan gRPC service dengan layanan pihak ketiga untuk memproses pembayaran.
2. **Validasi data pembayaran:** Memastikan informasi pembayaran yang diterima valid dan sesuai format.
3. **Penanganan error dan pengembalian status:** Menangani kemungkinan error dalam proses pembayaran dan memberikan respon yang sesuai.

## 7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?
1. **Meningkatkan interoperabilitas:** Memudahkan komunikasi antar service yang ditulis dalam bahasa pemrograman berbeda.
2. **Mengoptimalkan kinerja:** Protokol HTTP/2 yang mendasari gRPC lebih efisien dibandingkan HTTP/1.1.

## 8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?
- **HTTP/2:** Lebih efisien, mendukung multiplexing request/respon, dan kompresi header. Namun, belum didukung universal oleh semua browser.
- **HTTP/1.1/WebSocket:** Lebih kompatibel dengan browser, namun kurang efisien dan tidak mendukung multiplexing.

## 9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?
- **REST:** Komunikasi searah, client mengirim request dan menunggu respon. Kurang cocok untuk real-time communication.
- **gRPC:** Komunikasi dua arah, memungkinkan pengiriman dan penerimaan data secara simultan. Ideal untuk aplikasi real-time.

## 10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?
- **Protocol Buffers:** Lebih efisien dan ketat, namun membutuhkan definisi schema yang eksplisit.
- **JSON:** Lebih fleksibel dan mudah digunakan, namun kurang efisien dan berpotensi menimbulkan ambiguitas.
