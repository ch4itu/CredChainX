# CredChain

CredChain is a blockchain-based credential issuance and verification system that leverages zero‑value transactions and QR codes—without the need for a smart contract—to securely store and verify credential data. Instead of using a smart contract, the SHA‑256 hash of the credential data is stored in the input data field of a 0‑value transaction sent from an authorized wallet to a designated destination address. Later, a QR code embedding both the original data and the transaction ID is scanned, and the system retrieves the transaction to verify that the data remains authentic and originates from the authorized issuer.

## Features

- **Credential Issuance:**  
  - Collects credential details (e.g., name, date of birth, semester, subjects, marks, and a photo) via a web form.
  - Compresses the uploaded photo and converts it to Base64.
  - Generates a JSON payload with the credential data and computes its SHA‑256 hash.
  - Sends a 0‑value transaction from an authorized wallet to a designated destination address with the hash stored in the transaction's input data field.
  - Verifies that the issuing wallet matches the pre‑configured authorized address.
  - Generates a QR code embedding the JSON data and transaction ID after the transaction is confirmed on the blockchain.

- **Credential Verification:**  
  - Scans a QR code using a webcam or mobile camera (powered by the html5‑qrcode library).
  - Retrieves the corresponding transaction from the blockchain using the transaction ID.
  - Verifies that the transaction originates from the authorized issuer.
  - Compares the on‑chain hash (stored in the input data) with a locally computed hash of the credential JSON data to confirm authenticity.

## Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, etc.) that supports HTML5 and JavaScript.
- A local web server (or similar) to serve the HTML file (this is recommended to enable camera access for QR scanning).
- An internet connection (the project uses the public Polygon RPC endpoint: `https://polygon-rpc.com`).
- The mnemonic of the authorized issuing wallet.

### Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/CredChain.git
   cd CredChain
