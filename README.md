# mofo-transaction-storage

Pull down Coinbase & PayPal transactions into a database for various sundry porpoises

## Requirements

* node.js 4
* postgres 9.4
* PayPal Classic API credentials

## Setup

### Database

Run the following SQL to create the necessary table:

```sql
CREATE TABLE paypal (
  id TEXT PRIMARY KEY,
  timestamp TIMESTAMP WITH TIME ZONE,
  type TEXT,
  email TEXT,
  name TEXT,
  status TEXT,
  amount MONEY,
  settle_amount MONEY,
  fee_amount MONEY,
  currency TEXT,
  country_code TEXT,
  thunderbird BOOLEAN NOT NULL DEFAULT FALSE
);

CREATE TABLE stripe (
  id TEXT PRIMARY KEY,
  timestamp TIMESTAMP WITH TIME ZONE,
  amount MONEY,
  settle_amount MONEY,
  refunded MONEY,
  currency TEXT,
  status TEXT,
  country_code TEXT,
  name TEXT,
  email TEXT,
  recurring BOOLEAN NOT NULL DEFAULT FALSE,
  thunderbird BOOLEAN NOT NULL DEFAULT FALSE
);
```

### Environment

Create a file named `.env` to place configuration options in.

* PAYPAL_DB_CONNECTION_STRING
* PAYPAL_USERNAME
* PAYPAL_PASSWORD
* PAYPAL_SIGNATURE
* PAYPAL_START_DATE
* PAYPAL_STEP_MINUTES
* SERVER_PORT
* SERVER_DB_CONNECTION_STRING
* SERVER_START_DATE
* SERVER_END_DATE
* SERVER_STRIPE_SECRET
* STRIPE_API_KEY
* OXR_APP_ID
* STRIPE_DB_CONNECTION_STRING
