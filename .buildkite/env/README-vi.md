
[ejson](https://github.com/Shopify/ejson) and
[ejson2env](https://github.com/Shopify/ejson2env) are used to manage access
tokens and other secrets required for CI.

#### Cài đặt
```bash
$ sudo gem install ejson ejson2env
```

Sau đó lấy "keypair" và đặt nó vào `/opt/ejson/keys/`.

#### Sử dụng
Chạy dòng lệnh sau để giải mã secrets ra môi trường:
```bash
$ eval $(ejson2env secrets.ejson)
```

#### Quản lý secrets.ejson
Để giải mã  `secrets.ejson` cho mục đích chỉnh sửa, chạy:
```bash
$ ejson decrypt secrets.ejson -o secrets_unencrypted.ejson
```

Chỉnh sửa, và chạy lệnh sau để mã hóa lại file **TRƯỚC KHI BẠN ĐƯA MÃ NGUỒN
THAY ĐỔI LÊN**:
```bash
$ ejson encrypt secrets_unencrypted.ejson
$ mv secrets_unencrypted.ejson secrets.ejson
```

