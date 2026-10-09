Create test-cases/authorization-tests.md.

Test ID

Test scenario

Expected result

AUTHZ-001

User A accesses User B's resource

Access denied

AUTHZ-002

Standard user invokes an admin endpoint

Access denied

AUTHZ-003

User changes a protected role field

Role remains unchanged or request is rejected

AUTHZ-004

Expired token accesses a protected endpoint

Request rejected

AUTHZ-005

User accesses another tenant's records

Access denied

AUTHZ-006

User attempts an unauthorized DELETE operation

Request rejected

AUTHZ-007

API returns sensitive properties to a restricted user

Sensitive fields excluded

AUTHZ-008

User attempts to modify a resource they do not own

Modification rejected

Example: IDOR/BOLA test
Create examples/idor-bola-example.http:

http
### Authorized user's resource
GET https://api.example.test/v1/orders/1001
Authorization: Bearer {{user_a_token}}
Accept: application/json

### Test access to a different user's resource
GET https://api.example.test/v1/orders/1002
Authorization: Bearer {{user_a_token}}
Accept: application/json
Replace the example hostname and resource IDs with values from your authorized test environment. Configure user_a_token using a local environment variable or your HTTP client's secret store. Never commit real credentials or production tokens.

Pass condition: User A cannot read or modify User B's order without explicit authorization.
