# Tomcat-MariaDB-phpMyAdmin All-in-One Docker Template

This Docker Compose template includes MariaDB, phpMyAdmin, and Tomcat, specifically designed for SEHS4701(23/24)
classmates to facilitate their J2EE learning. It serves as an exemplary framework for anyone looking to utilize
MySQL/MariaDB and phpMyAdmin in a convenient manner.

## Versions Matrix

| Component  | Version | Image Source |
|------------|---------|--------------|
| Tomcat     | 10.1.19 | official     |
| MariaDB    | 11.2.3  | bitnami      |
| phpMyAdmin | 5.2.1   | bitnami      |

## Usage

1. Clone this repository to your local machine.
   ```bash
   git clone https://github.com/andrewfung729/tomcat-mariadb-phpmyadmin-aio-docker.git
   ```
2. Navigate to the root directory of the repository and run:
   ```bash
   docker compose up
   ```
3. Access the Tomcat server at [http://localhost:8080](http://localhost:8080).
4. Access phpMyAdmin at [http://localhost:8081](http://localhost:8081).
5. Connect to the MariaDB server at `localhost:3306`.
6. FYI, the default username is `root` and the password is empty for the MariaDB server. You can edit the login info and
   ports in compose file yourself.
7. You need to create the database by yourself.

### Configuration Ref

- https://hub.docker.com/r/bitnami/mariadb
- https://hub.docker.com/r/bitnami/phpmyadmin
- https://hub.docker.com/_/tomcat
- https://github.com/bitnami/containers

## Known Issues and Workarounds

### Compatibility with Apple Silicon

The official phpMyAdmin Docker image may exhibit instability on Apple Silicon. A community-provided image from VMware is
recommended as it has been tested for stability on this architecture.

### Charset Configuration

A known charset issue with the latest official phpMyAdmin image can lead to connection errors with the MariaDB server,
displaying: `mysqli_real_connect(): (HY000/1130): Host 'X.X.X.X' is not allowed to connect to this MariaDB server`. To
mitigate this, configure the MariaDB server to use `utf8mb4` charset by adding the necessary configurations.

#### References

- https://github.com/php/php-src/issues/13452
- https://gist.github.com/w0rldart/aa472db45c3817d937a1870a32f77820
- https://devops.stackexchange.com/questions/6148/how-to-create-a-mariadb-mysql-image-using-utf8-instead-of-the-default-latin1-cha

## Disclaimer

This project consolidates different Docker images and Docker Compose configurations strictly for educational and
developmental purposes. It is explicitly not intended for use in production environments. This setup is designed to
streamline the deployment process for those learning about Docker, MariaDB, phpMyAdmin, and Tomcat.

Please consult the official Docker Hub documentation for in-depth details, particularly the phpMyAdmin Docker Official
Image, to understand the specifics and intended use of each component integrated within this template.

## Support and Contributions

If you encounter any problems while using this Docker template, please open an issue in this repository. I am committed
to providing assistance. Contributions to improve the setup or documentation are highly appreciated and can be made
through pull requests.
