# Monzo Pebble Plugin

A Pebble phone-side plugin that connects to the Monzo Developer API to provide real-time bank account balances, daily spending, savings pots, and recent transactions to Pebble watchapps, watchfaces, and the Index assistant using the new Pebble Plugins API. The plugin can move funds between pots, but never out of your account due to API limitations (not that it should be able to).

## Features

- **Sources**:
  - `finance/account`: Real-time account balances, spend today, total balances, and currency.
  - `finance/pot`: Active savings pots and their balances.
  - `finance/transaction`: Recent account transactions and merchant details.
  - `finance/configured`: Connection status indicator.
- **Actions**:
  - `deposit_pot`: Deposit funds into a designated savings pot.
  - `withdraw_pot`: Withdraw funds from a savings pot.

## Setup & Configuration

To connect the plugin to your Monzo account, you need API credentials from the Monzo Developer Portal:

1. Visit the [Monzo Developer Portal](https://developers.monzo.com/) and sign in.
2. Under **Clients**, click **New Client**.
3. Set the following fields:
   - **Name**: `Monzo Pebble Plugin` (or your choice)
   - **Redirect URLs**: A callback page URL (e.g. `https://benbjd.github.io/monzo-pebble-plugin/callback.html` or your own)
   - **Description**: Personal Pebble watch plugin (or your choice)
   - **Confidentiality**: Confidential
4. Save the client and copy your **Client ID** and **Client Secret**.
5. Open the plugin settings in the Pebble mobile companion app:
   - Enter your **Client ID**, **Client Secret**, and **Redirect URI**.
   - Tap **Authorize on Monzo** to open the login page in your browser.
   - Approve the login request in your Monzo mobile app.
   - Copy the authorization code shown on the callback page, paste it into settings, and tap **Connect & Save Credentials**.

## Building from Source

### Prerequisites

- Python 3.10 to 3.13
- Node.js and npm
- [`uv`](https://astral.sh/uv) (recommended)

### Install Pebble Tool & SDK

```bash
# Install pebble-tool via uv
uv tool install pebble-tool --python 3.13

# Install the latest Pebble SDK
pebble sdk install latest
```

### Build & Install

```bash
# Build the .pbw package
pebble build

# Install onto watch locally or through CloudPebble
pebble install --phone <PHONE_IP>
# Or
pebble install --cloudpebble

# Or run in the emulator
pebble install --emulator basalt
```

## License

MIT