# `salesforce-expense` README


[![PyPI version](https://badge.fury.io/py/salesforce-expense.svg)](https://badge.fury.io/py/salesforce-expense)
[![Build Status](https://api.travis-ci.org/giuliocalzolari/salesforce-expense.svg?branch=master)](https://travis-ci.org/giuliocalzolari/salesforce-expense/)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=giuliocalzolari_salesforce-expense&metric=bugs)](https://sonarcloud.io/dashboard?id=giuliocalzolari_salesforce-expense)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=giuliocalzolari_salesforce-expense&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=giuliocalzolari_salesforce-expense)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=giuliocalzolari_salesforce-expense&metric=security_rating)](https://sonarcloud.io/dashboard?id=giuliocalzolari_salesforce-expense)
[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=giuliocalzolari_salesforce-expense&metric=vulnerabilities)](https://sonarcloud.io/dashboard?id=giuliocalzolari_salesforce-expense)

This Python package provides a CLI tool which can submit expense claims to
SalesForce programmatically.

## Installation

To install the tool from PyPI, just use `pip`:

```bash
pip install salesforce-expense
```

To install from local source for development (if not using `pipenv` then ensure
that `setupext-janitor` is installed locally first, so that `setup.py`
correctly cleans up the `dist` directory):

```bash
./setup.py clean --all
./setup.py bdist_wheel
pip install dist/salesforce_expense-*.whl
```

## Configuration

The script requires a local configuration file with your SalesForce credentials
included in it, located at `~/.pse.json`. It should look like:

```json
{
  "username": "your-salesforce-email@example.com",
  "password": "fdgdhrx6MA==",
  "token": "afghfyfgbgnegrfbgdhtd"
}
```

`password` must be `base64` encoded as follows:

```bash
echo -n "my-password" | base64
```

To obtain the security token for your Salesforce account, follow
[this guide](https://onlinehelp.coveo.com/en/ces/7.0/administrator/getting_the_security_token_for_your_salesforce_account.htm).

## Usage

```
(salesforce-expense) bash-3.2$ expense add --help
Usage: expense add [OPTIONS]

Options:
  -p, --project TEXT              Project Name
  -d, --description TEXT          Description to add
  -a, --amount FLOAT              amount to add
  --date TEXT                     Date
  --currency [EUR|USD|GBP]        currency
  --category [Client entertainment|Car hire|Flights|Fuel|Internet|IT consumables|IT services (subscription &amp; licences)|Mileage|Office supplies and comsumables|Other|Parking & Tolls|Per Diem|Private Accommodation|Professional training & Exam|Staff entertainment|Staff welfare|Subsistence|Taxi|Trains|Transport - other|Weekly Groceries|Telephony]
                                  category
  --noreceipt                     Lost receipt
  --billable / --non-billable     billable flag
  --inpolicy [Yes|No]             In Policy
  --help                          Show this message and exit.

```

## TODO

-   Clean up remaining documentation
-   Run linter over the code
-   Add additional currencies
-   Add submission
-   Add listing
-   Support the dry-run flag
-   Add OCR for receipt files to determine the date and amount
-   Integrate with billing systems
-   Port to Android?

## License

`salesforce-expense` is licensed under the [WTFPL](LICENSE).
