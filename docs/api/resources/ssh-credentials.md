import SSHCredentialsCreateRequest from './examples/_ssh_credentials_create_request.md';
import SSHCredentialsCreateResponse from './examples/_ssh_credentials_create_response.md';
import SSHCredentialsDeleteRequest from './examples/_ssh_credentials_delete_request.md';
import SSHCredentialsGetRequest from './examples/_ssh_credentials_get_request.md';
import SSHCredentialsGetResponse from './examples/_ssh_credentials_get_response.md';
import SSHCredentialsListRequest from './examples/_ssh_credentials_list_request.md';
import SSHCredentialsListResponse from './examples/_ssh_credentials_list_response.md';
import SSHCredentialsUpdateRequest from './examples/_ssh_credentials_update_request.md';
import SSHCredentialsUpdateResponse from './examples/_ssh_credentials_update_response.md';

#  SSH Credentials
------------



## Create SSH Credential
Create a new ssh_credential from an uploaded public SSH key. This ssh credential can be used to start new tunnels via ngrok's SSH gateway.

### Request

POST /ssh_credentials

<SSHCredentialsCreateRequest />


#### Parameters

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `description` | string | human-readable description of who or what will use the ssh credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this ssh credential. Optional, max 4096 bytes. |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |
| `public_key` | string | the PEM-encoded public key of the SSH keypair that will be used to authenticate |


### Response

Returns a 201 response  on success

<SSHCredentialsCreateResponse />


#### Fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string | unique ssh credential resource identifier |
| `uri` | string | URI of the ssh credential API resource |
| `created_at` | string | timestamp when the ssh credential was created, RFC 3339 format |
| `description` | string | human-readable description of who or what will use the ssh credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this ssh credential. Optional, max 4096 bytes. |
| `public_key` | string | the PEM-encoded public key of the SSH keypair that will be used to authenticate |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |


## Delete SSH Credential
Delete an ssh_credential by ID

### Request

DELETE /ssh_credentials/{id}

<SSHCredentialsDeleteRequest />


### Response

Returns a 204 response with no body on success


## Get SSH Credential
Get detailed information about an ssh_credential

### Request

GET /ssh_credentials/{id}

<SSHCredentialsGetRequest />


### Response

Returns a 200 response  on success

<SSHCredentialsGetResponse />


#### Fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string | unique ssh credential resource identifier |
| `uri` | string | URI of the ssh credential API resource |
| `created_at` | string | timestamp when the ssh credential was created, RFC 3339 format |
| `description` | string | human-readable description of who or what will use the ssh credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this ssh credential. Optional, max 4096 bytes. |
| `public_key` | string | the PEM-encoded public key of the SSH keypair that will be used to authenticate |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |


## List SSH Credentials
List all ssh credentials on this account

### Request

GET /ssh_credentials

<SSHCredentialsListRequest />


### Response

Returns a 200 response  on success

<SSHCredentialsListResponse />


#### Fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `ssh_credentials` | [SSHCredential](#api-ssh-credentials-list-fields-ssh-credential) | the list of all ssh credentials on this account |
| `uri` | string | URI of the ssh credential list API resource |
| `next_page_uri` | string | URI of the next page, or null if there is no next page |

#### SSHCredential fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string | unique ssh credential resource identifier |
| `uri` | string | URI of the ssh credential API resource |
| `created_at` | string | timestamp when the ssh credential was created, RFC 3339 format |
| `description` | string | human-readable description of who or what will use the ssh credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this ssh credential. Optional, max 4096 bytes. |
| `public_key` | string | the PEM-encoded public key of the SSH keypair that will be used to authenticate |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |


## Update SSH Credential
Update attributes of an ssh_credential by ID

### Request

PATCH /ssh_credentials/{id}

<SSHCredentialsUpdateRequest />


#### Parameters

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string |  |
| `description` | string | human-readable description of who or what will use the ssh credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this ssh credential. Optional, max 4096 bytes. |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |


### Response

Returns a 200 response  on success

<SSHCredentialsUpdateResponse />


#### Fields

|&nbsp;| &nbsp;| &nbsp;|
|---|---|---|
| `id` | string | unique ssh credential resource identifier |
| `uri` | string | URI of the ssh credential API resource |
| `created_at` | string | timestamp when the ssh credential was created, RFC 3339 format |
| `description` | string | human-readable description of who or what will use the ssh credential to authenticate. Optional, max 255 bytes. |
| `metadata` | string | arbitrary user-defined machine-readable data of this ssh credential. Optional, max 4096 bytes. |
| `public_key` | string | the PEM-encoded public key of the SSH keypair that will be used to authenticate |
| `acl` | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains, addresses, and labels the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules for domains may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. Bind rules for labels may specify a wildcard key and/or value to match multiple labels. For example, you may specify a rule of `bind:*=example` which will allow `x=example`, `y=example`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |