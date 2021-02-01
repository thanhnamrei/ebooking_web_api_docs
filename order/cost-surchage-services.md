# Create order

Show a single Account if current User has access permissions to it.

**URL** : `/api​/Cost​/GetOrderCostAndSurchargeServices`

**Method** : `POST`

**Auth required** : NONE

**Permissions required** : Anonymous

**Data**:

| Property | Type | Validate | Description |
|:---------|:-----|:------ |:------------|
| OrderWeight   | double |  | Tổng khối lượng kiện hàng
| WeightOfDoc | double | RequiredIf(DOC) | Khối lượng doc (nếu có thư từ)
| FromProvinceCode | string | Required | Mã tỉnh gửi
| ToProvinceCode | string | Required | Mã tỉnh nhận
| CustomerCode | string | Required | Mã khách hàng
| FromDistrictCode | string
| ToDistrictCode | string
| HasWooded | bool | | Kiện hàng đóng gỗ (mặc định false)
| IsHighValue | bool| | Hàng giá trị cao
| PackageItems| Collection([PackageItem](..)) | | Kích thước kiện hàng
| InsuranceValue | decimal | | Giá trị bảo hiểm đơn hàng
| PackupTypeCode | int | | Loại đóng gói

## Success Response

**Status** : `200 OK`

**Request body**:
<div style="page-break-after: always;"></div>

```json
{
  "weightOfDoc": 1,
  "fromProvinceCode": "50",
  "toProvinceCode": "50",
  "customerCode": "19006663",
  "fromDistrict": "5017",
  "toDistrict": "5017",
  "hasWooded": false,
  "isHighValue": false,
  "packageItems": [
    {
      "width": 1,
      "length": 1,
      "height": 1,
      "numberOfItem": 1,
      "weight": 10
    }
  ]
}
```

**Response data**:

```json
{
    "data": {
        "0203": {
            "primaryCost": 212960.0,
            "promotionCost": 0.0,
            "remoteFee": 0.0,
            "bulkyFee": 0.0,
            "codFee": 0.0,
            "doubleCheckFee": 0.0,
            "fuelFee": 0.0,
            "highValueFee": 0.0,
            "insuranceFee": 0.0,
            "packupFee": 0.0,
            "vatFee": 0.0,
            "woodenBaleFee": 0.0,
            "addedWoodenWeight": 0.0,
            "liquidFee": 0.0,
            "returnFee": 0.0,
            "otherFee": 0.0,
            "totalCost": 212960.0
        },
        "0201": {
            "primaryCost": 84700.0,
            "promotionCost": 0.0,
            "remoteFee": 0.0,
            "bulkyFee": 0.0,
            "codFee": 0.0,
            "doubleCheckFee": 0.0,
            "fuelFee": 0.0,
            "highValueFee": 0.0,
            "insuranceFee": 0.0,
            "packupFee": 0.0,
            "vatFee": 0.0,
            "woodenBaleFee": 0.0,
            "addedWoodenWeight": 0.0,
            "liquidFee": 0.0,
            "returnFee": 0.0,
            "otherFee": 0.0,
            "totalCost": 84700.0
        },
        "0202": {
            "primaryCost": 74536.0,
            "promotionCost": 0.0,
            "remoteFee": 0.0,
            "bulkyFee": 0.0,
            "codFee": 0.0,
            "doubleCheckFee": 0.0,
            "fuelFee": 0.0,
            "highValueFee": 0.0,
            "insuranceFee": 0.0,
            "packupFee": 0.0,
            "vatFee": 0.0,
            "woodenBaleFee": 0.0,
            "addedWoodenWeight": 0.0,
            "liquidFee": 0.0,
            "returnFee": 0.0,
            "otherFee": 0.0,
            "totalCost": 74536.0
        },
        "0205": {
            "primaryCost": 60500.0,
            "promotionCost": 0.0,
            "remoteFee": 0.0,
            "bulkyFee": 0.0,
            "codFee": 0.0,
            "doubleCheckFee": 0.0,
            "fuelFee": 0.0,
            "highValueFee": 0.0,
            "insuranceFee": 0.0,
            "packupFee": 0.0,
            "vatFee": 0.0,
            "woodenBaleFee": 0.0,
            "addedWoodenWeight": 0.0,
            "liquidFee": 0.0,
            "returnFee": 0.0,
            "otherFee": 0.0,
            "totalCost": 60500.0
        },
        "0210": {
            "primaryCost": 79860.0,
            "promotionCost": 0.0,
            "remoteFee": 0.0,
            "bulkyFee": 0.0,
            "codFee": 0.0,
            "doubleCheckFee": 0.0,
            "fuelFee": 0.0,
            "highValueFee": 0.0,
            "insuranceFee": 0.0,
            "packupFee": 0.0,
            "vatFee": 0.0,
            "woodenBaleFee": 0.0,
            "addedWoodenWeight": 0.0,
            "liquidFee": 0.0,
            "returnFee": 0.0,
            "otherFee": 0.0,
            "totalCost": 79860.0
        }
    },
    "isSuccess": true,
    "message": "Success",
    "code": "01"
}
```

## Error Responses

**Condition** : if model request is invalid

**Status** : `400 BAD REQUEST`

**Request body** :

```json
{
  "weightOfDoc": 1,
  "customerCode": "19006663",
  "fromDistrict": "5017",
  "toDistrict": "5017",
  "hasWooded": false,
  "isHighValue": false
}
```

**Response data** :

```json
{
    "errors": {
        "ToProvinceCode": [
            "The ToProvinceCode field is required."
        ],
        "FromProvinceCode": [
            "The FromProvinceCode field is required."
        ]
    },
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "|2ae33c92-4c16861900273638."
}
```

### Or

**Condition** :

**Status** : `500 INTERNAL SERVER`

**Response data** :

```json
{
    "data": null,
    "isSuccess": false,
    "message": "Error message",
    "code": null
}
```

## Notes

There are error issues:

<!-- * This view allows existing users to test for existence of accounts that exist
    but that they do not have access to.
* Account IDs are sequential so an authorized user can count all the Accounts
    on the system. -->
