# demo_QLHS
# demo_QLHS
* Cấu trúc thư mục dự án
```
project-root/
│
├── app/
│   │
│   ├── Controllers/
│   │   ├── AuthController.php
│   │   ├── StudentController.php
│   │   ├── ClassController.php
│   │   └── HomeController.php
│   │
│   ├── Models/
│   │   ├── User.php
│   │   ├── Student.php
│   │   ├── ClassRoom.php
│   │   ├── Role.php
│   │   └── Permission.php
│   │
│   ├── Services/
│   │   ├── AuthService.php
│   │   ├── StudentService.php
│   │   ├── ClassService.php
│   │   └── PermissionService.php
│   │
│   ├── Repositories/
│   │   ├── UserRepository.php
│   │   ├── StudentRepository.php
│   │   ├── ClassRepository.php
│   │   ├── RoleRepository.php
│   │   └── PermissionRepository.php
│   │
│   ├── Views/
│   │   │
│   │   ├── auth/
│   │   │   ├── login.php
│   │   │   └── register.php
│   │   │
│   │   ├── students/
│   │   │   ├── index.php
│   │   │   ├── create.php
│   │   │   ├── edit.php
│   │   │   └── detail.php
│   │   │
│   │   ├── classes/
│   │   │   ├── index.php
│   │   │   ├── create.php
│   │   │   ├── edit.php
│   │   │   └── detail.php
│   │   │
│   │   ├── layouts/
│   │   │   ├── main.php
│   │   │   ├── header.php
│   │   │   ├── footer.php
│   │   │   └── sidebar.php
│   │   │
│   │   └── home/
│   │       └── index.php
│   │
│   ├── Middlewares/
│   │   ├── AuthMiddleware.php
│   │   ├── GuestMiddleware.php
│   │   ├── AdminMiddleware.php
│   │   └── PermissionMiddleware.php
│   │
│   ├── Requests/
│   │   ├── LoginRequest.php
│   │   ├── RegisterRequest.php
│   │   ├── StoreStudentRequest.php
│   │   ├── UpdateStudentRequest.php
│   │   ├── StoreClassRequest.php
│   │   └── UpdateClassRequest.php
│   │
│   ├── Helpers/
│   │   ├── functions.php
│   │   ├── auth.php
│   │   └── response.php
│   │
│   └── Exceptions/
│       ├── ValidationException.php
│       ├── DatabaseException.php
│       ├── AuthenticationException.php
│       └── NotFoundException.php
│
├── core/
│   │
│   ├── App.php
│   ├── Router.php
│   ├── Request.php
│   ├── Response.php
│   ├── Controller.php
│   ├── Model.php
│   ├── Database.php
│   ├── Session.php
│   ├── Validator.php
│   ├── Middleware.php
│   ├── View.php
│   ├── Auth.php
│   ├── Container.php
│   └── Config.php
│
├── config/
│   ├── app.php
│   ├── database.php
│   ├── auth.php
│   └── session.php
│
├── database/
│   │
│   ├── migrations/
│   │   ├── create_users_table.sql
│   │   ├── create_roles_table.sql
│   │   ├── create_permissions_table.sql
│   │   ├── create_role_permissions_table.sql
│   │   ├── create_students_table.sql
│   │   └── create_classes_table.sql
│   │
│   └── seeders/
│       ├── RoleSeeder.php
│       ├── PermissionSeeder.php
│       └── UserSeeder.php
│
├── public/
│   │
│   ├── assets/
│   │   │
│   │   ├── css/
│   │   ├── js/
│   │   ├── images/
│   │   └── uploads/
│   │
│   ├── .htaccess
│   └── index.php
│
├── routes/
│   ├── web.php
│   └── api.php
│
├── storage/
│   │
│   ├── logs/
│   ├── cache/
│   └── sessions/
│
├── tests/
│   ├── Unit/
│   └── Feature/
│
├── vendor/
│
├── .env
├── .env.example
├── .gitignore
├── composer.json
├── README.md
└── phpunit.xml
```

* giải thích tổng quan kiến trúc dự án

dự án gồm 2 phần chính: Core Framework và Application Layer

Core Framework là phần nền tảng của hệ thống, chịu trách nhiệm quản lý request lifecycle, routing, middleware, session, validation, database abstraction và các thành phần cốt lõi để application hoạt động. là bộ máy vận hành hệ thống thuộc phần `Core` trong cấu trúc dự án. 

Application Layer là nơi chứa business logic và các module nghiệp vụ của hệ thống như Authentication, Student Management và Class Management. là nơi chứa logic nghiệp vụ thuộc phần `app` trong cấu trúc dự án

* giải thích chi tiết từng thành phần

trong `app` sẽ có:

Controllers: giữ vai trò là nhận request đứng giữa request và business logic, phần này chỉ nhận request gọi service và trả view/response 

trong `Controllers` có:

AuthController.php xử lý login, register, logout 

StudentController.php xử lý create, update, delete, read, search student 

ClassController.php xử lý create, update, delete, read, search class

HomeController.php là trang dashboard

Models: giữ vai trò đại diện cho các thực thể có trong hệ thống (user, student, class) phần này chứa getter/setter,  realation, properties

trong `Models` có:

ClassRoom.php đại diện cho bảng class

Permission.php

Role.php phân quyền

Student.php đại diện cho bảng students

User.php đại diện cho bảng users

Services: giữ vai trò chứa logic nghiệp vụ hệ thống, xử lý logic đăng nhập, đăng xuất,...

trong `Services` có:

AuthService.php xử lý logic login, register, session, password verify

StudentService.php xử lý thêm, sửa, xóa, xem, tìm kiếm học sinh

ClassService.php  xử lý thêm, sửa, xóa, xem, tìm kiếm lớp học

PermissionService.php xử lý logic phân quyền.

Repositories: chịu trách nghiệm làm việc với phần database tách ra như này để SQL không nằm trong controller hay service giúp dễ bảo trì hay sửa dổi DB

trong `Repositories` có:

UserRepository.php query đến bảng users

StudentRepository.php query đến bảng students

ClassRepository.php query đến bảng classes

RoleRepository.php query đến bảng Role

PermissionRepository.php query đến bảng Permission

Views: chứa giao diện hệ thống

trong `Views` có:

auth chứa giao diện đăng nhập, đăng ký

classes chứa UI classes module có index.php chứa danh sách học sinh, thêm sửa xóa xem lớp

home chứa giao diện trang chủ

layouts chứa layout chung hệ thống

students chứa UI student module có index.php chứa danh sách học sinh, thêm sửa xóa xem học sinh

Middlewares: Lớp chặn request chạy trước Controller, ví dụ user muốn vào admin để quản lý hệ thống thì middleware kiểm tra xem đã login hay chưa, nếu chưa chưa thì chuyển đến login

trong `Middleware` có:

AuthMiddleware.php chỉ cho user đã login truy cập

GuestMiddleware.php chặn user đã login

AdminMiddleware.php chỉ admin truy cập

PermissionMiddleware.php kiểm tra permission

Requests: là Validation Layer tồn tại để tập trung validate, dễ tái sử dụng và controller gọn hơn

trong `Request` có:

LoginRequest.php để Validate login form.

RegisterRequest.php để Validate register form.

StoreStudentRequest.php Validate tạo student.

UpdateStudentRequest.php Validate update student.

StoreClassRequest.php Validate tạo class.

UpdateClassRequest.php Validate update class.

Helpers: là Function dùng chung toàn hệ thống

Exception: là nơi xử lý lỗi custom của hệ thống, nơi xử lý ngoại lệ.

Sang phần `core` có: 

App.php là Application Kernel trái tim hệ thống có vai trò khởi động toàn bộ hệ thống, nhiệm vụ start app, load cònig, routes,..

Auth.php

Config.php

Container.php

Controller.php base controller để các controller khác sẽ extends 

Database.php PDO connect, query, transaction

Middleware.php base middleware

Model.php base model 

Request.php 

Response.php

Router.php Nhiệm vụ Map URL sang Controller

Session.php

Validator.php

View.php render view

Sang phần `config` là nơi chứa cấu hình hệ thống

Sang phần `database` là nơi chứa dữ liệu database

Sang phần `seeders` là nơi chứa dữ liệu mẫu

Sang phần `public` là nơi apache trỏ vào

Sang phần `routes` có:

Sang phần `storage` là nơi lưu log, cache,..

Sang phần `test` để test feature,..

Sang phần `vendor` có:

tóm lại: Hệ thống được xây theo layered MVC architecture. Request đi qua Front Controller trong public/index.php, sau đó Router điều hướng đến Controller. Controller gọi Service để xử lý business logic, Service sử dụng Repository để thao tác database. Kết quả được trả về View để render giao diện. Core framework chịu trách nhiệm routing, request lifecycle, middleware, validation, session và database abstraction.
