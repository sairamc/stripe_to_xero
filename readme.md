This is a script for porting all the Stripe data you care about into Xero as a bank statement, which means you can easily reconcile invoices, bank transfers, fees, etc. The script pulls directly from your Stripe account, with no messy intermediate steps.

# Configuration

## Configuration in Xero
Create a `Stripe` bank account in Xero. It should be a manual account. Also, create a new `bot` user, who will handle uploading bank statements.

## Environment Variables
Use these environment variables as configuration
    STRIPE_SECRET="api key from stripe"
    XERO_USER="username for xero"
    XERO_PASSWORD="password for xero"
    XERO_ACCT_ID="account id from Xero"
    BANK_NAME="the name of your transfer bank"
    STX_COUNT=50 #optional, but recommended

Be sure to `bundle install` to install the `stripe` gem. You should also install `casperjs` with `npm install -g casperjs` if you'd like to use the `auto_import.sh` script.

# Dependencies

- `stripe` gem

# Recommended tools
- `casperjs` npm module (`casper.coffee` automagically uploads the bank statement into Xero, even though Xero doesn't provide an API.)
- `foreman` (recommended for easily running the script with environment variables)

# Usage

- Run `auto_import.sh` to automatically import your Stripe data into Xero. (If you have `casperjs` installed)
- Or, just run the `stripe_to_xero.rb` script to generate `xero.csv` which you can upload manually.
- Reconcile away.

# Notes

We use `foreman` to easily set up environment variables. You might find it handy too.

Requires ruby 1.9.

# Changelog

v1 - Implements new refund calculation, adds better echoed text, uses Stripe's newish `expand` option to make 50 less API calls, and increase speed A LOT.

# License

Copyright (c) 2013, Vidpresso, Inc.
All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
Neither the name of the company nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
