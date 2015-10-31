Create a new user

    CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
	CREATE USER 'wp'@'localhost' IDENTIFIED BY 'Renielle0214';

Grant privileges on the new user

    GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
    GRANT ALL PRIVILEGES ON * . * TO 'wp'@'localhost';

    FLUSH PRIVILEGES;

Create Database

    