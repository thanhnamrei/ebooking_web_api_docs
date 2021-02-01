# Create order

Show a single Account if current User has access permissions to it.

**URL** : `/api/Order/CreateOrder`

**Method** : `POST`

**Auth required** : NONE

**Permissions required** : Anonymous

**Data**:

| Property | Type | Validate | Description |
|:---------|:-----|:------ |:------------|
| Sender   | [ContactInfoViewModel](../resources/order-info.md)| Required |
| Receiver | [ContactInfoViewModel](../resources/order-info.md) | Required |
| OrderInfo | [OrderInfoViewModel](../resources/order-info.md) | Required |
| Cost | [OrderCostViewModel](../resources/order-info.md) |  |

## Success Response

**Code** : `200 OK`

**Request example**:

**Response example**:

```json
{
    "id": 345,
    "name": "Super Account",
    "enterprise": false,
    "url": "http://testserver/api/accounts/345/"
}
```

## Error Responses

**Condition** :

**Code** : `400 BAD REQUEST`

**Content** : `{}`

### Or

<!-- **Condition** : If Account exists but Authorized User does not have required
permissions.

**Code** : `403 FORBIDDEN`

**Content** :

```json
{"detail": "You do not have permission to perform this action."}
``` -->

## Notes

There are security issues:

* This view allows existing users to test for existence of accounts that exist
    but that they do not have access to.
* Account IDs are sequential so an authorized user can count all the Accounts
    on the system.
