# Monzo Pebble Plugin

A Pebble phone-side plugin that connects to the Monzo Developer API to provide real-time bank account balances, daily spending, savings pots, and recent transactions to Pebble watchapps, watchfaces, and the Index assistant using the new Pebble Plugins API.

## Features

- **Sources**:
  - `finance/account`: Real-time account balances, spend today, total balances, and currency.
  - `finance/pot`: Active savings pots and their balances.
  - `finance/transaction`: Recent account transactions and merchant details.
  - `finance/configured`: Connection status indicator.
- **Actions**:
  - `deposit_pot`: Deposit funds into a designated savings pot.
  - `withdraw_pot`: Withdraw funds from a savings pot.
- **Standalone Distribution**: Can be installed independently on the phone companion app without requiring a C watchface or watchapp binary.

## Setup & Configuration

To connect the plugin to your Monzo account, you need API credentials from the Monzo Developer Portal:

1. Visit the [Monzo Developer Portal](https://developers.monzo.com/) and sign in.
2. Under **Clients**, click **New Client**.
3. Set the following fields:
   - **Name**: `Monzo Pebble Plugin` (or your choice)
   - **Redirect URLs**: Your hosted callback page URL (e.g. `https://benbjd.github.io/monzo-pebble/callback.html` or `https://benbjd.github.io/monzo-pebble-plugin/callback.html`)
   - **Description**: Personal Pebble watch plugin
   - **Confidentiality**: Confidential
4. Save the client and copy your **Client ID** and **Client Secret**.
5. Open the plugin settings in the Pebble mobile companion app:
   - Enter your **Client ID**, **Client Secret**, and **Redirect URI**.
   - Tap **Authorize on Monzo** to open the login page in your browser.
   - Approve the login request in your Monzo mobile app.
   - Copy the authorization code shown on the callback page, paste it into settings, and tap **Connect & Save Credentials**.

## Building & Installing

### Prerequisites

- Python 3.10 to 3.13
- Node.js and npm
- `pebble-tool` (installed via `uv tool install pebble-tool`)
- Pebble SDK (`pebble sdk install latest`)

### Build

```bash
pebble build
```

This generates `build/monzo-pebble-plugin.pbw` containing only the phone-side plugin script and configuration page.

### Test in Emulator

```bash
# Start an emulator (e.g. emery) and install the plugin
pebble install --emulator emery
```

## License

MIT
