# Secure File Transfer System

A secure file transfer system with:
- AES encryption/decryption for files
- Two-way client-server TCP connection
- Google Drive integration for encrypted file storage
- GUI interface for easy file management

## Features

1. AES-256 encryption for all files
2. Client-server architecture for file transfer
3. Google Drive integration for cloud storage
4. GUI interface for easy operation
5. Secure key management

## Requirements

- Python 3.6 or higher
- Required Python packages (install using `pip install -r requirements.txt`):
  - pycryptodome
  - google-api-python-client
  - google-auth-httplib2
  - google-auth-oauthlib
  - PyQt5

## Setup

1. Clone this repository
2. Install the required packages:
   ```
   pip install -r requirements.txt
   ```
3. (Optional) Set up Google Drive API:
   - Go to the [Google Cloud Console](https://console.cloud.google.com/)
   - Create a new project
   - Enable the Google Drive API
   - Create OAuth 2.0 credentials
   - Download the credentials JSON file and save it as `credentials.json` in the root directory of the project

## Usage

### Running the Server

Start the server with:

```
python run_server.py
```

Server options:
- `--host`: Host address to bind to (default: 0.0.0.0)
- `--port`: Port to listen on (default: 5000)
- `--upload-dir`: Directory to store uploaded files (default: uploads)
- `--no-gdrive`: Disable Google Drive integration

Example:
```
python run_server.py --port 5001 --upload-dir my_uploads
```

### Running the Client GUI

Start the client GUI with:

```
python run_client.py
```

### Using the Client GUI

1. **Connect to Server**:
   - Enter the server host and port
   - Click "Connect"

2. **Upload Files**:
   - Go to the "Upload" tab
   - Click "Browse" to select a file
   - Click "Upload" to send it to the server
   - The file will be encrypted and uploaded to Google Drive (if enabled)

3. **Download Files**:
   - Go to the "Download" tab
   - Click "Refresh File List" to see available files
   - Select a file and click "Download Selected"
   - The file will be downloaded from Google Drive, decrypted, and saved to your downloads folder

4. **Manage Encryption Keys**:
   - Go to the "Encryption Keys" tab
   - View current keys
   - Save keys to a file for backup
   - Load keys from a backup file

## Security Notes

- Files are encrypted with AES-256 in CBC mode
- Encryption keys are generated randomly for each file
- Keys are stored only on the client side
- Only encrypted files are stored on Google Drive
- Files are deleted from the server immediately after upload

## Architecture

- **Encryption Module**: Handles AES encryption/decryption
- **Server**: Manages file transfers and Google Drive integration
- **Client**: Communicates with the server and handles file transfers
- **GUI**: Provides a user-friendly interface for the client

## License

This project is licensed under the MIT License - see the LICENSE file for details. 