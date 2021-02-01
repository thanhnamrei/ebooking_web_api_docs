# Create order

Show a single Account if current User has access permissions to it.

**URL** : `/api​/Cost​/GetOrderCostAndSurchargeMultiService`

**Method** : `POST`

**Auth required** : NONE

**Permissions required** : Anonymous

**Data**:

| Property | Type | Validate | Description |
|:---------|:-----|:------ |:------------|
| OrderWeight   | double |  | Tổng khối lượng kiện hàng
| FromProvinceCode | string | Required | Mã tỉnh gửi
| ToProvinceCode | string | Required | Mã tỉnh nhận
| CustomerCode | string | Required | Mã khách hàng
| ServiceCode | string | Required
| FromDistrictCode | string
| ToDistrictCode | string
| HasWooded | bool | | Kiện hàng đóng gỗ (mặc định false)
| IsHighValue | bool| | Hàng giá trị cao
| PackageItems| Collection([PackageItem](..)) | | Kích thước kiện hàng
| InsuranceValue | decimal | | Giá trị bảo hiểm đơn hàng
| PackupTypeCode | int | | Loại đóng gói

## Success Response

**Code** : `200 OK`

**Request body**:

```json
{
  "orderWeight": 1,
  "fromProvinceCode": "50",
  "toProvinceCode": "50",
  "serviceCode": "0203",
  "customerCode": "19006663",
  "fromDistrictCode": "5017",
  "toDistrictCode": "5017",
  "hasWooded": false,
  "isHighValue": false,
  "packageItems": [
    {
      "width": 1,
      "length": 1,
      "height": 1,
      "numberOfItem": 1,
      "weight": 1
    }
  ],
  "insuranceValue": 0,
  "packupTypeCode": 1
}
```

**Response data**:

```json
{
    "data": {
        "primaryCost": 84700.0,
        "promotionCost": 0.0,
        "remoteFee": 16940.0,
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
        "totalCost": 101640.0
    },
    "isSuccess": true,
    "message": "Success",
    "code": "01"
}
```

## Error Responses

**Condition** : if model request is invalid

**Code** : `400 BAD REQUEST`

**Content** : `{}`

### Or

**Condition** :

**Code** : `500 INTERNAL SERVER`

**Content** :

```json
```

## Notes

There are security issues:

* This view allows existing users to test for existence of accounts that exist
    but that they do not have access to.
* Account IDs are sequential so an authorized user can count all the Accounts
    on the system.
