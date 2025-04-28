## Password + pepper + Bcrypt

Add pepper (saved outside the database) to the password and generate a hash with Bcrypt;

Why use Bcrypt:

- When generating a password with Bcrypt, even a weak password 12345 always generates different hashes in each encryption, because internally it uses random salts for each hash and also has a rounds mechanism, where it is possible to configure the number of steps necessary to compute a hash.

*https://bcrypt-generator.com/

Why user pepper:

- Pepper is a random hash that can be saved in an environment variable on the server (Never save the pepper in the database or hard coded, so that code or database leaks do not compromise security), when concatenated to a password, even if the database is leaked, part of the password information will not be exposed, making it practically impossible to discover the password;

### Steps to record a password

- Get the user's password;
- Concatenate the password with the pepper;
- Generate a Bcrypt hash of the password concatenated with the pepper;
- Save the final result in the database;

### Steps to validate the password

- Get the user's password;
- Concatenate the password with the pepper;
- Generate a Bcrypt hash of the password concatenated with the pepper;
- Compare with the database hash;
