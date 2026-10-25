# Web Programming Project

A food e-commerce web application built with JSP/Servlet. Customers can browse and search products, manage a cart and wishlist, check out, read blog posts, and manage their account. Admins get a back-office for managing products, users, admins, bills and blogs.

## Technology

- Java 8, JSP / Servlet (`javax.servlet-api` 4.0.1), JSTL 1.2
- MySQL (`mysql-connector-java` 5.1.49)
- JavaMail 1.6.0 (account verification and password reset emails)
- Maven (WAR packaging), Apache Tomcat
- CKEditor 5 for the admin blog editor

## Features

**Customer**

- Register, login/logout, email verification code, forgot / create new password
- Browse products, product details, search, filter by category
- Session-based cart (add, decrease, remove) and wishlist
- Checkout, order history, edit profile
- Blog list, blog categories, blog details

**Admin**

- Manage products, users, admins, bills and blogs (add / edit / delete)

## Project structure

```
src/main/java/vn/edu/nlu/
├── beans/        Data objects (Product, User, Bill, Blog, Role, ...)
├── controller/   Customer-facing servlets (login, cart, wishlist, checkout, blog, ...)
├── management/   Admin servlets (CRUD for products, users, admins, bills, blogs)
├── entity/       Database access classes
├── model/        Session models (Cart, Whishlist, Account)
├── db/           ConnectionDB (JDBC connection)
└── mail/         Mail sender (JavaMail)
src/main/webapp/
├── *.jsp         Customer pages
├── admin/        Admin pages
└── css, js, img, fonts, assets
```

## Getting started

### Prerequisites

- JDK 8+
- Maven
- MySQL
- Apache Tomcat 9 (Servlet 4.0)

### Setup

1. Clone the repository.
2. Create a MySQL database named `group12` and import the project's schema/data. No SQL dump is included in this repository, so get it from the team.
3. Check the connection settings in [ConnectionDB.java](src/main/java/vn/edu/nlu/db/ConnectionDB.java). The defaults are `jdbc:mysql://localhost:3306/group12`, user `root`, empty password.
4. Configure the SMTP sender in [Mail.java](src/main/java/vn/edu/nlu/mail/Mail.java) with your own email account (for Gmail, use an app password).
5. Build the WAR:
   ```bash
   mvn clean package
   ```
6. Deploy `target/WebProgrammingProject-1.0-SNAPSHOT.war` to Tomcat, or run the project from IntelliJ IDEA with a Tomcat run configuration.
7. Open `http://localhost:8080/<context-path>/` in your browser.

## Notes

- Database and SMTP credentials are currently hard-coded in source. Move them to environment variables or a config file before deploying anywhere public, and rotate any credential already committed.
