# Secure Cloud-Based File Storage System

A client-server system that enables secure file storage on Google Drive using AES encryption, SSL/TLS for secure transmission, and TCP checksum verification for data integrity.

## Project Overview

This project implements a secure cloud-based file storage system where clients can securely store and retrieve encrypted files from Google Drive. The system ensures end-to-end encryption with client-side key management.

### Key Features

- **End-to-End Encryption**: Files are encrypted using AES before transmission
- **Secure Communication**: SSL/TLS encryption for client-server communication
- **Data Integrity**: TCP checksum verification ensures file integrity
- **User-Friendly Interface**: GUI for easy file management
- **Cloud Storage**: Integration with Google Drive for file storage
- **Client-Side Key Management**: Users maintain control of encryption keys

## System Requirements

- Python 3.x
- Required packages:
  ```
  pycryptodome
  google-auth google-auth-oauthlib google-auth-httplib2 google-api-python-client
  PyQt5
  cryptography
  ```

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/secure_transfer.git
   cd secure_transfer
   ```

2. Install required packages:
   ```
   pip install pycryptodome
   pip install google-auth google-auth-oauthlib google-auth-httplib2 google-api-python-client
   pip install PyQt5
   pip install cryptography
   ```

3. Generate SSL certificates (if not already included):
   ```
   openssl req -x509 -newkey rsa:4096 -keyout Server.key -out Server.crt -days 365 -nodes
   ```
4. Refer to CN Project Documentation.pdf for detailed explanation
5. Ensure that you have RSA Key, Certificate and have a valid Credentials.json file 

## Usage

### Starting the Server

1. Navigate to the server directory:
   ```
   cd Server
   ```

2. Run the server:
   ```
   python run_server.py
   ```

3. The server will start and display its IP address and port number

### Running the Client

1. Navigate to the client directory:
   ```
   cd Client
   ```

2. Ensure you have the Server.crt file in the Client directory

3. Start the client application:
   ```
   python run_client.py
   ```

4. Connect to the server by entering:
   - Server IP address
   - Server port number
   - Click "Connect"

### File Operations

1. **Uploading Files**:
   - Click "Upload" button
   - Select file to upload
   - Choose or generate an AES key
   - The file will be encrypted and uploaded to Google Drive

2. **Downloading Files**:
   - Select the file from the list
   - Provide the correct AES key
   - Click "Download"
   - The file will be decrypted and saved locally

3. **Key Management**:
   - Generate new AES keys using the "Generate Key" option
   - Store keys securely - they are required for decryption
   - Lost keys cannot be recovered

## Project Structure

```
Project Root/
├── Server/
│   ├── server.py
│   ├── run_server.py
│   ├── Server.crt
│   ├── Server.key
│   ├── encryption.py
│   ├── gdrive.py
│   ├── test_encryption.py
│   ├── Downloads/
│   └── Uploads/
└── Client/
    ├── gui.py
    ├── client.py
    ├── Server.crt
    └── run_client.py
```

## Security Considerations

- **Key Storage**: The client must store all AES keys locally. Loss of a key means the encrypted file cannot be decrypted.
- **Certificate Validation**: The client must have a valid server certificate to connect.
- **Server Security**: The server does not store any files; it only handles encryption/decryption operations.

## Troubleshooting

- **Connection Issues**: Verify server IP and port, check if server is running, ensure SSL certificate is valid
- **Authentication Errors**: Verify Google Drive credentials, check SSL certificate validity
- **File Transfer Issues**: Check network connectivity, verify file permissions, ensure sufficient storage space

## Developers

- Adyansh Aggarwal (PES1UG23AM028)
- Akash Madisetty (PES1UG23AM035)

## License

This project is licensed under the MIT License - see the LICENSE file for details. 
