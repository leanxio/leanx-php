## LeanxSdk, PHP SDK for LeanX Integration

LeanxSdk is a PHP SDK designed to simplify integration with the LeanX payment API. This SDK provides easy-to-use methods for generating payment links, validating payments, and checking payment statuses.

API Docs : https://docs.leanx.io/api-docs

*   Easy setup and usage for LeanX payment integration.
*   Flexible configuration with dynamic base URLs and endpoints.
*   Comprehensive support for generating and managing payments.

## Basic Usage

To get started with `LeanxSdk`, follow these steps:

### Instantiate the SDK

```php
use Leanx\LeanxSdk\LeanxSdk;

// Base URL for LeanX API (use sandbox or live URL as needed)
$baseUrl = 'https://api.leanx.dev';
// Replace 'your-auth-token' with your actual LeanX auth token
$authToken = 'LP-922AFF8C-MM|cdffb385-7f8b-4fa8-9bdf-5563c7b6c2cb|a59592d0bf0620ac09ee406b91f7006b59b96a35d1406dc3101e383dfa9abf820686064e7b281adc71a3a3a36eed5xxxxxxxxxxxxe41ad25a0d07axxxxx';
// Replace 'hashKey' with your actual LeanX Hash Key
$hashKey = 'a59592d0bf0620ac09ee406b91f7006b59b96a35d1406dc3101e383dfa9abf820686064e7b281adc71a3a3xxxxxxxe1ae77b39e41ad25a0d07a2525531';
// Replace 'UUID' with your actual LeanX UUID
$UUID = 'cdffb385-7f8b-xxxxxxx-c7b6c2cb';

// Create a new instance of the SDK
$sdk = new LeanxSdk($baseUrl, $authToken, $hashKey, $UUID);

// PARAMETER INITIALIZATION
$invoiceNo = 'INV123450003';
$parameters = [
    'collection_uuid' => "Dc-A9A12F67CF-Lx",
    'amount' => 51.00,
    'full_name' => 'John Doe',
    'email' => 'john.doe@example.com',
    'phone_number' => '0123456789',
    'invoice_no' => $invoiceNo,
    'redirect_url' => 'https://webhook.site/b3312afa-8b27-49b1-a05f-482e7a5c764e',
    'callback_url' => 'https://webhook.site/b3312afa-8b27-49b1-a05f-482e7a5c764e'
];

$callback = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpbnZvaWNlX25vIjoiSU5WMTIzNDUwMDAzIiwiY2xpZW50X2RhdGEiOnsibWVyY2hhbnRfaW52b2ljZV9ubyI6IklOVjEyMzQ1MDAwMyIsInV1aWQiOiJjZGZmYjM4NS03ZjhiLTRmYTgtOWJkZi01NTYzYzdiNmMyY2IiLCJvcmRlcl9pZCI6Ik5vbmUifSwiaW52b2ljZV9zdGF0dXNfaWQiOjIsImludm9pY2VfdHlwZV9pZCI6MSwiaW52b2ljZV90eXBlIjoiTk9STUFMX0NPTExFQ1RJT04iLCJpbnZvaWNlX3N0YXR1cyI6IlNVQ0NFU1MiLCJhbW91bnQiOiI1MS4wMCIsInBheW1lbnRfbW9kZWxfcmVmZXJlbmNlX2lkIjoxLCJyYXRlX3R5cGVfcmVmZXJlbmNlX2lkIjoxLCJwYXltZW50X3NlcnZpY2VfaWQiOjI5LCJjbGllbnRfcmVkaXJlY3RfdXJsIjoiaHR0cHM6Ly93ZWJob29rLnNpdGUvYjMzMTJhZmEtOGIyNy00OWIxLWEwNWYtNDgyZTdhNWM3NjRlIiwiY2xpZW50X2NhbGxiYWNrX3VybCI6Imh0dHBzOi8vc3RhZy1hcGkubGVhbnBheS5teS9hcGkvdjEvY2FsbGJhY2stdXJsL2NhbGxiYWNrLXJlZGlyZWN0P191dWlkPWNkZmZiMzg1LTdmOGItNGZhOC05YmRmLTU1NjNjN2I2YzJjYiZvcmRlcl9pZD1Ob25lIiwiY2xpZW50X3RyYW5zYWN0aW9uX2RldGFpbHMiOm51bGwsInByZWZ1bmRfY29sbGVjdGlvbiI6eyJpdGVtIjpudWxsLCJyZXNwb25zZV9jb2RlIjoyMTAwfSwiZGVzY3JpcHRpb24iOm51bGwsImNhcmRfdG9rZW4iOm51bGwsImZweF9kZWJpdF9hdXRoX2NvZGUiOm51bGwsImZweF9jcmVkaXRfYXV0aF9jb2RlIjpudWxsLCJmcHhfZGViaXRfc3RhdHVzIjoiIiwidHJhbnNhY3Rpb25fcmVzcG9uc2VfdGltZSI6IjIxIEF1Z3VzdCAyNCAwMzoxNjozMSBQTSIsIm9yaWdpbmFsX3RyYW5zYWN0aW9uX3Jlc3BvbnNlX3RpbWUiOiIyMDI0LTA4LTIxIDE1OjE2OjMxIn0.1DQSTWKPoiIhzYfHzLrtqAeokUoR59AofSJnAOvDTuc";

$GETPAYMENTSERVICESLIST = [
    "payment_type" => "WEB_PAYMENT",
    "payment_status" => "active",
    "payment_model_reference_id" => 1,
];

$CREATEPAYMENTCOLLECTION = [
    "title" => "Public API Collection Creation Test",
    "description" => "This is public API collection description",
    "enable_billing_address" => true
];
$UPDATECOLLECTION = [
    "id" => 353,
    "title" => "TEST COLLECTION 2",
    "description" => "collecetion description"
];

$UPDATEBILL = [
    "id" => 2521,
    "full_name" => "JOHN DOE UPDATE",
    "email" => "johndoe2@email.com",
    "phone_number" => "0133456789"
];

$GETCOLLECTIONLIST = '{
    "start_date": "01-01-1970",
    "end_date": "31-12-2050",
    "record_status": 1,
    "search": {
      "search_enable": false,
      "search_key": "TEST COLLECTION",
      "search_column": "title"
    },
    "sort": {
      "sort_type": "desc",
      "parameter_name": "created_at"
    }
  }';
$GETCOLLECTIONLISTBODY = json_decode($GETCOLLECTIONLIST);
$SKIP = 0;
$LIMIT = 100;

$PAYOUTTRANSACTIONLIST = '{
    "start_date": "01-01-1970",
    "end_date": "31-12-2050",
    "record_status": 1,
    "search": {
      "search_enable": false,
      "search_key": "TEST COLLECTION",
      "search_column": "title"
    },
    "sort": {
      "sort_type": "desc",
      "parameter_name": "created_at"
    }
  }';
$PAYOUTTRANSACTIONLISTBODY = json_decode($PAYOUTTRANSACTIONLIST);

$CREATEPAYOUT = '{
    "virtual_pool_reference": "VA-741009-120852777560-PAYOUT",
    "payout_service_id": 23,
    "amount": 13.00,
    "recipient_name": "John Doe",
    "client_callback_url": "https://www.yourdomain.com/api-callback-url",
    "third_party_account_no": "8011408168",
    "external_invoice_ref": "INVOICE1234",
    "recipient_reference": "test"
}';
$CREATEPAYOUTBODY = json_decode($CREATEPAYOUT);

$BANKACCOUNTVALIDATION = '{
    "client_identifier": "LEANPAY",
    "payout_service_id": 1,
    "third_party_account_no": "9011426016"
}';
$BANKACCOUNTVALIDATIONBODY = json_decode($BANKACCOUNTVALIDATION);

$GETBILLLIST = '{
    "start_date": "01-01-1970",
    "end_date": "31-12-2050",
    "record_status": 1,
    "search": {
      "search_enable": true,
      "search_key": "dp-23A3CEDEB7-lx",
      "search_column": "invoice_no"
    },
    "sort": {
      "sort_type": "desc",
      "parameter_name": "created_at"
    }
  }';
$GETBILLLISTBODY = json_decode($GETBILLLIST);

$CREATEBILL = '{
    "collection_uuid": "Dc-A9A12F67CF-Lx",
    "amount": 10.00,
    "redirect_url": "https://www.yourdomain.com/return-page",
    "callback_url": "https://www.yourdomain.com/api-callback-url",
    "full_name": "John Doe",
    "email": "johndoe@email.com",
    "phone_number": "0123456789",
    "invoice_ref": "UNIQUEREF2"
}';
$CREATEBILLBODY = json_decode($CREATEBILL);

// UTILIZATION SAMPLE ...........
// GENERAL FEATURES
// $response = $sdk->GeneratePaymentLinkv1($parameters);
// $response = $sdk->GeneratePaymentLinkv1WithHashmac($parameters);
// $response = $sdk->CreateAutoBillPagev1WithHashmac($parameters);
// $response = $sdk->CheckPaymentStatusV1WithHmac($invoiceNo);
// $response = $sdk->DecodeCallback($callback);
// $response = $sdk->GetPaymentServices($GETPAYMENTSERVICESLIST);
// $response = $sdk->GetPaymentServicesHmac($GETPAYMENTSERVICESLIST);

// POOL BALANCE
// $response = $sdk->GetPoolBalance();

// COLLECTIONS
// $response = $sdk->CreateCollection($CREATEPAYMENTCOLLECTION);
// $response = $sdk->GetCollectionList($GETCOLLECTIONLISTBODY, $SKIP, $LIMIT, false);
// $response = $sdk->GetSpecificCollection(353, false);
// $response = $sdk->UpdateCollection($UPDATECOLLECTION, false);
// $response = $sdk->ActivateCollection(353, false);
// $response = $sdk->DeactivateCollection(353, false);
// $response = $sdk->TransactionList(0, 100, "01-01-1970", "31-01-2099", "SUCCESS", false);

// BILLS
// $response = $sdk->GetBillList($GETCOLLECTIONLISTBODY, $SKIP, $LIMIT, false);
// $response = $sdk->GetSpecificBill(2503, false);
// $response = $sdk->GetBillTransactionStatus("UNIQUEREF", false);
// $response = $sdk->CreateBill($CREATEBILLBODY, false);
// $response = $sdk->UpdateBill($UPDATEBILL, false);

// PAYOUTS
// $response = $sdk->PayoutServiceList([], false);
// $response = $sdk->PayoutTransactionList($PAYOUTTRANSACTIONLISTBODY, $SKIP, $LIMIT, false);
// $response = $sdk->CreatePayout($CREATEPAYOUTBODY, false);
// $response = $sdk->PayoutStatus("PAYOUT-A9D5:174307-LEANX", false);
$response = $sdk->BankAccountValidation($BANKACCOUNTVALIDATIONBODY, false);

print_r($response);
```

### Generate a Payment Link

```php
$parameters = [
    'amount' => 100.00,
    'full_name' => 'John Doe',
    'email' => 'john.doe@example.com',
    'phone_number' => '0123456789',
    'invoice_no' => 'INV12345',
    'redirect_url' => 'https://yourwebsite.com/redirect',
    'callback_url' => 'https://yourwebsite.com/callback'
];

$response = $sdk->GeneratePaymentLinkv1($parameters);
print_r($response);
```

### Check Payment Status

```php
$invoiceNo = 'INV12345';

$response = $sdk->CheckPaymentStatusV1($invoiceNo);
print_r($response);
```

### Payment Services List

```php
$parameters = [
  "payment_type" => "WEB_PAYMENT",
  "payment_status" => "active",
  "payment_model_reference_id" => 1,
];

$response = $sdk->GetPaymentServices($parameters);
print_r($response);
```

---

## HMAC Endpoints

---

### Generate a Payment Link

```php
$parameters = [
    'amount' => 100.00,
    'full_name' => 'John Doe',
    'email' => 'john.doe@example.com',
    'phone_number' => '0123456789',
    'invoice_no' => 'INV12345',
    'redirect_url' => 'https://yourwebsite.com/redirect',
    'callback_url' => 'https://yourwebsite.com/callback'
];

$response = $sdk->GeneratePaymentLinkv1WithHashmac($parameters);
print_r($response);
```

### Generate Auto Bill Page

```php
$parameters = [
    'amount' => 100.00,
    'full_name' => 'John Doe',
    'email' => 'john.doe@example.com',
    'phone_number' => '0123456789',
    'invoice_no' => 'INV12345',
    'redirect_url' => 'https://yourwebsite.com/redirect',
    'callback_url' => 'https://yourwebsite.com/callback'
];

$response = $sdk->CreateAutoBillPagev1WithHashmac($parameters);
print_r($response);
```

### Check Payment Status

```php
$invoiceNo = 'INV12345';

$response = $sdk->CheckPaymentStatusV1WithHmac($invoiceNo);
print_r($response);
```

### Payment Services List

```php
$parameters = [
  "payment_type" => "WEB_PAYMENT",
  "payment_status" => "active",
  "payment_model_reference_id" => 1,
];

$response = $sdk->GetPaymentServicesHmac($parameters);
print_r($response);
```

---

## Callback Decode Helper

---

```php
$callbackData = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpbnZvaWNlX25vIjoiSU5WMTIzNDUwMDAzIiwiY2xpZW50X2RhdGEiOnsibWVyY2hhbnRfaW52b2ljZV9ubyI6IklOVjEyMzQ1MDAwMyIsInV1aWQiOiJjZGZmYjM4NS03ZjhiLTRmYTgtOWJkZi01NTYzYzdiNmMyY2IiLCJvcmRlcl9pZCI6Ik5vbmUifSwiaW52b2ljZV9zdGF0dXNfaWQiOjIsImludm9pY2VfdHlwZV9pZCI6MSwiaW52b2ljZV90eXBlIjoiTk9STUFMX0NPTExFQ1RJT04iLCJpbnZvaWNlX3N0YXR1cyI6IlNVQ0NFU1MiLCJhbW91bnQiOiI1MS4wMCIsInBheW1lbnRfbW9kZWxfcmVmZXJlbmNlX2lkIjoxLCJyYXRlX3R5cGVfcmVmZXJlbmNlX2lkIjoxLCJwYXltZW50X3NlcnZpY2VfaWQiOjI5LCJjbGllbnRfcmVkaXJlY3RfdXJsIjoiaHR0cHM6Ly93ZWJob29rLnNpdGUvYjMzMTJhZmEtOGIyNy00OWIxLWEwNWYtNDgyZTdhNWM3NjRlIiwiY2xpZW50X2NhbGxiYWNrX3VybCI6Imh0dHBzOi8vc3RhZy1hcGkubGVhbnBheS5teS9hcGkvdjEvY2FsbGJhY2stdXJsL2NhbGxiYWNrLXJlZGlyZWN0P191dWlkPWNkZmZiMzg1LTdmOGItNGZhOC05YmRmLTU1NjNjN2I2YzJjYiZvcmRlcl9pZD1Ob25lIiwiY2xpZW50X3RyYW5zYWN0aW9uX2RldGFpbHMiOm51bGwsInByZWZ1bmRfY29sbGVjdGlvbiI6eyJpdGVtIjpudWxsLCJyZXNwb25zZV9jb2RlIjoyMTAwfSwiZGVzY3JpcHRpb24iOm51bGwsImNhcmRfdG9rZW4iOm51bGwsImZweF9kZWJpdF9hdXRoX2NvZGUiOm51bGwsImZweF9jcmVkaXRfYXV0aF9jb2RlIjpudWxsLCJmcHhfZGViaXRfc3RhdHVzIjoiIiwidHJhbnNhY3Rpb25fcmVzcG9uc2VfdGltZSI6IjIxIEF1Z3VzdCAyNCAwMzoxNjozMSBQTSIsIm9yaWdpbmFsX3RyYW5zYWN0aW9uX3Jlc3BvbnNlX3RpbWUiOiIyMDI0LTA4LTIxIDE1OjE2OjMxIn0.1DQSTWKPoiIhzYfHzLrtqAeokUoR59AofSJnAOvDTuc';

$response = $sdk->DecodeCallback($callbackData);
print_r($response);
```