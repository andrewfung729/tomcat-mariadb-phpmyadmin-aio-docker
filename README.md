# Tomcat-MariaDB-phpMyAdmin All-in-One Docker Template

This Docker Compose template includes MariaDB, phpMyAdmin, and Tomcat, specifically designed for SEHS4701(23/24)
classmates to facilitate their J2EE learning. It serves as an exemplary framework for anyone looking to utilize
MySQL/MariaDB and phpMyAdmin in a convenient manner.

用Mac的同學有福了，唔使再痛苦咁搞Tomcat、MariaDB、MySQL Workbench、OpenJDK。用Docker啦，即開即用！

## Disclaimer

This project consolidates different Docker images and Docker Compose configurations strictly for educational and
developmental purposes. It is explicitly not intended for use in production environments. This setup is designed to
streamline the deployment process for those learning about Docker, MariaDB, phpMyAdmin, and Tomcat.

Please consult the official Docker Hub documentation for in-depth details, particularly the phpMyAdmin Docker Official
Image, to understand the specifics and intended use of each component integrated within this template.

Users should thoroughly review and understand all terms, concepts, and procedures outlined in this guide before
utilization. By employing this template, you acknowledge and accept that I, as the author and contributor, bear no
liability for any potential errors, data loss, or damages that may occur as a result of using this guide. Your decision
to use this template is at your own risk, and it is recommended to proceed with caution and due diligence.

### References

- https://hub.docker.com/r/bitnami/mariadb
- https://hub.docker.com/r/bitnami/phpmyadmin
- https://docs.docker.com
- https://github.com/twtrubiks/docker-tutorial
- https://electrify.tw/archives/395/homebrew-for-mac/

## Prerequisites

### Windows Users

As I do not develop on Windows, I am unable to provide a specific setup guide for this platform. Contributions are
welcome; if you wish to add a Windows guide, please submit a pull request.

### macOS Users

1. Install [Homebrew](https://brew.sh) by executing the following command in your terminal:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
2. Install Docker Desktop using Homebrew:
    ```bash
    brew install --cask docker
    ```

### Linux Users (Ubuntu Tested)

The instructions are tested on Ubuntu. They may be applicable to other Linux distributions, but compatibility is not
guaranteed.

- Install Docker using the official script:
  ```bash
  curl -fsSL https://get.docker.com -o get-docker.sh
  sh get-docker.sh
  ```

## Usage

1. Clone this repository to your local machine.
2. Navigate to the root directory of the repository and run:
   ```bash
   docker compose up
   ```
3. FYI, the default username is `root` and the password is empty for the MariaDB server. You also need to create the
   database by yourself.
4. Access the Tomcat server at [http://localhost:8080](http://localhost:8080).
5. Access phpMyAdmin at [http://localhost:8081](http://localhost:8081).
6. Connect to the MariaDB server at `localhost:13306`.

## Additional Resources for SEHS4701(23/24) Classmates

This section is dedicated to classmates enrolled in the SEHS4701(23/24) course. The recommendations provided here
reflect my personal preferences. Please feel free to explore and utilize whatever tools and methods best suit your
learning style. The following guidelines are intended merely as suggestions.

### Integrated Development Environment (IDE)

For developing J2EE applications, I recommend using the IntelliJ IDEA Community Edition. It offers comprehensive support
for Java and other programming languages:

- Install IntelliJ IDEA Community Edition on macOS:
   ```bash
   brew install --cask intellij-idea-ce
   ```

### Java Development Kit (JDK)

It is essential to have the latest version of the Java Development Kit (JDK) for Java development. OpenJDK is an
open-source implementation that is compatible with most Java applications:

- Install the latest OpenJDK using Homebrew:
   ```bash
   brew install openjdk
   ```

After installing OpenJDK, you may need to configure your IDE to use the installed JDK. This ensures your development
environment is set up correctly for compiling and running Java applications.

## Known Issues and Workarounds

### Compatibility with Apple Silicon

The official phpMyAdmin Docker image may exhibit instability on Apple Silicon. A community-provided image from VMware is
recommended as it has been tested for stability on this architecture.

### Charset Configuration

A known charset issue with the latest official phpMyAdmin image can lead to connection errors with the MariaDB server,
displaying: `mysqli_real_connect(): (HY000/1130): Host 'X.X.X.X' is not allowed to connect to this MariaDB server`. To
mitigate this, configure the MariaDB server to use `utf8mb4` charset by adding the necessary configurations.

#### References

1. https://github.com/php/php-src/issues/13452
2. https://gist.github.com/w0rldart/aa472db45c3817d937a1870a32f77820
3. https://devops.stackexchange.com/questions/6148/how-to-create-a-mariadb-mysql-image-using-utf8-instead-of-the-default-latin1-cha

## Support and Contributions

If you encounter any problems while using this Docker template, please open an issue in this repository. I am committed
to providing assistance. Contributions to improve the setup or documentation are highly appreciated and can be made
through pull requests.