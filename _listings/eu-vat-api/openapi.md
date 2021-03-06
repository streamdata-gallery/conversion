swagger: "2.0"
x-collection-name: EU VAT API
x-complete: 1
info:
  title: VAT API
  description: a-developer-friendly-api-to-help-your-business-achieve-vat-compliance
  version: "1"
host: vatapi.com
basePath: /v1
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /currency-conversion:
    get:
      summary: Convert a currency
      description: Convert a currency.
      operationId: currency_conversion
      x-api-path-slug: currencyconversion-get
      parameters:
      - in: query
        name: amount
        description: Optional, an amount you are wanting to convert
      - in: query
        name: currency_from
        description: The currency code you are converting from
      - in: query
        name: currency_to
        description: The currency code you are converting to
      - in: header
        name: Response-Type
        description: The default response type is application/json if you would like
          to receive an XML response then set this to XML
      responses:
        200:
          description: OK
      tags:
      - Convert
      - Currency
  /vat-price:
    get:
      summary: Convert a price to or from VAT price.
      description: Convert a price to or from vat price..
      operationId: convert_price
      x-api-path-slug: vatprice-get
      parameters:
      - in: query
        name: code
        description: The 2 digit country code
      - in: query
        name: country_rate
        description: The VAT rate to get the price for
      - in: query
        name: price
        description: The price you want converting
      - in: header
        name: Response-Type
        description: The default response type is application/json if you would like
          to receive an XML response then set this to XML
      - in: query
        name: type
        description: Optional, if the price is including VAT set the type to incl
      responses:
        200:
          description: OK
      tags:
      - Convert
      - Price
      - To
      - From
      - VAT
      - Price