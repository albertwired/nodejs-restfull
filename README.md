# Simple RESTfull API with Nodejs, express, Postgresql, and Sequelize

How to [Install Rails](http://installrails.com/)
## Requirement
- [NodeJS](https://nodejs.org),
- [Express](https://expressjs.com)
- [Postgresql](https://www.postgresql.org/download),
- [Sequelize](http://docs.sequelizejs.com)
- [bcrypt](https://www.npmjs.com/package/bcrypt)


## Installation

```
git clone REPOSITORY
cd nodejs-restfull
npm install
sequelize db:migrate
npm start
```

## Integration Testing
```
npm run test
```

### Test Result
```
 Products Routes
    [GET] /api/v1/product list
GET /api/v1/products 200 10.759 ms - 647
      ✓ Should get list of products
    [GET] /api/v1/product/:id 
GET /api/v1/products/1 200 7.150 ms - 238
      ✓ Should get one product
    [POST] /api/v1/product/ 
POST /api/v1/products 201 20.894 ms - 238
      ✓ Should create a product
    [PUT] /api/v1/product/:id 
Executing (default): INSERT INTO "Products"
PUT /api/v1/products/1 201 12.599 ms - 238
      ✓ Should update a product
    [DELETE] /api/v1/product/:id 
DELETE /api/v1/products/1 200 10.557 ms - 60
      ✓ Should delete a product

  Users Routes
    [POST] /auth/signup
POST /auth/signup 201 88.024 ms - 243
      ✓ should create user (90ms)
    [POST] /auth/login Positive
true
POST /auth/login 200 86.559 ms - 193
      ✓ should do login (89ms)
    [POST] /auth/login Negative
POST /auth/login 401 86.571 ms - 47
      ✓ should do login (91ms)


  8 passing (3s)

```
### Postman Result
#### Sign up

![N|Solid(http://preview.ibb.co/fGDUZn/Screenshot_from_2018_04_02_19_21_16.png)

#### Log in

![N|Solid(http://preview.ibb.co/nN93un/Screenshot_from_2018_04_02_19_20_59.png)

#### Get Products

![N|Solid(http://preview.ibb.co/e1Ok77/Screenshot_from_2018_04_02_19_20_32.png)

#### Get Single Product

![N|Solid(http://preview.ibb.co/kCWGEn/Screenshot_from_2018_04_02_19_20_03.png)

#### Create Product

![N|Solid(http://preview.ibb.co/d1CdS7/Screenshot_from_2018_04_02_19_19_49.png)

#### Update Product

![N|Solid(http://preview.ibb.co/fNcZ0S/Screenshot_from_2018_04_02_19_19_27.png)

#### Delete Product
![N|Solid(http://preview.ibb.co/n4hZ0S/Screenshot_from_2018_04_02_19_18_57.png)


### Question & Answer
1. Desain Stack and tools
	- Desain aplikasi
	![N|Solid(http://image.ibb.co/dafU0S/microserv.jpg)
    
    Desain tersebut menjelaskan alur komunikasi data dari _mobile phone_ ke server menggunakan protokol HTTP dengan arsitektur RESTFull. Pilihan tersebut dikarenakan saat ini metode standar yang digunakan untuk interaksi antar aplikasi menggunakan API.
    Pada _Auth Service_ digunkan untuk proses registrasi dan login guna mendapatkan akses token. Dan pada _Auth Gateway_ digunakan untuk proses otentifikasi kedalam servis product dengan model _token based_.
    
    - Stack Backend:
    	- Programming Language : NodeJS
    	
        NodeJS merupakan bahasa pemrograman yang cukup populer dengan performa yang cepat dan cocok baik untuk microservice ataupun monolitik untuk backend.
    	- Framework: Express
    	
        Saya gunakan karena support yang bagus sehingga kedepan tidak akan kesulitan bila memerlukan update dan maintenance
      
    	- Database: PostgreSQL
    	
        Pilihan menggunakan PostgreSQL sebagai dibanding dengan yang lain karenan kecepatan dan kapabilitasnya yang cukup bisa diandalkan ketika nanti akan terjadi proses _scaling_
    	
     - Tools pendukung lain:
     	- Mocha Sebagai test framework yang banyak digunakan
     	- chai sebagai module test yang cukup membantu dengan library yang mudah dipahami dan digunakan
     	- chai-http sebagai request engine untuk chai
     	- jsonwebtoken sebagai token generator
     	- bcrypt senbagai encryptor untuk password
     	- morgan untuk logger
     	- sequelize untuk mengatasi penggunaan ORM dan database migration
     	- body-parser untuk mengatasi parsing json unuk response
     	- cors untuk handle cross domain request
     	- pg dan pg-hstore untuk menghubungkan dan proses database
     	
2. Keamanan pengiriman data pada sistem
	
    Keamanan pengiriman data seperti di jelaskan di atas menggunakan token base yang dihandle oleh Json Web Token (JWT) sebagai encryptor. (JWT) Sudah cukup untuk mengakomodasi kebutuhan untuk aplikasi ini karena tidak memerlukan konfigurasi tambahan seperti yang digunakan pada OAuth.
3. Panduan Aplikasi

Disebutkan di atas.

4. Kekurangan dari dokumen
	- pada /auth/register Tidak perlu dikeluarkan password_digest
	- Tidak ada negative test documentation