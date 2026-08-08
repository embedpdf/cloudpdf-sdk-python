# Reference
## Deployment
<details><summary><code>client.deployment.<a href="src/cloudpdf/deployment/client.py">license_status</a>() -> DeploymentLicenseStatusResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.deployment.license_status()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc
<details><summary><code>client.doc.<a href="src/cloudpdf/doc/client.py">head</a>(...) -> DocHead200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.head(
    doc_id="docId",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.<a href="src/cloudpdf/doc/client.py">download</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.download(
    doc_id="docId",
    layer_name="layerName",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.<a href="src/cloudpdf/doc/client.py">manifest</a>(...) -> DocManifest200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.manifest(
    doc_id="docId",
    layer_name="layerName",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.<a href="src/cloudpdf/doc/client.py">render</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Render parameters (viewport, format) pass as flat dotted query keys, e.g. `?viewport.kind=width&viewport.width=800`; the full grammar is documented with the viewer.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.render(
    doc_id="docId",
    layer_name="layerName",
    pon=1,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `int` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.<a href="src/cloudpdf/doc/client.py">text</a>(...) -> DocText200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.text(
    doc_id="docId",
    layer_name="layerName",
    pon=1,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `int` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Tenants
<details><summary><code>client.tenants.<a href="src/cloudpdf/tenants/client.py">list</a>(...) -> TenantsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.tenants.list()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**limit:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tenants.<a href="src/cloudpdf/tenants/client.py">create</a>(...) -> TenantsCreate200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.tenants.create(
    id="id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tenants.<a href="src/cloudpdf/tenants/client.py">get</a>(...) -> TenantsGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.tenants.get(
    tenant_id="tenantId",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tenants.<a href="src/cloudpdf/tenants/client.py">delete</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Destroys the tenant and everything in its namespace — documents, layers, stored bytes, audit history. Irreversible.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.tenants.delete(
    tenant_id="tenantId",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Documents
<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">list</a>(...) -> DocumentsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.list(
    tenant_id="tenantId",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**state:** `typing.Optional[ListDocumentsRequestState]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">get</a>(...) -> DocumentsGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.get(
    tenant_id="tenantId",
    id="id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">delete</a>(...)</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.delete(
    tenant_id="tenantId",
    id="id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">commit</a>(...) -> DocumentsCommit200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.commit(
    tenant_id="tenantId",
    id="id",
    sha256="sha256",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**sha256:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">download</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.download(
    tenant_id="tenantId",
    id="id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">thumbnail</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.thumbnail(
    tenant_id="tenantId",
    id="id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">upload_direct</a>(...) -> DocumentsUploadDirect200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
client.documents.upload_direct(...)
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `typing.Union[bytes, typing.Iterator[bytes], typing.AsyncIterator[bytes]]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">init</a>(...) -> DocumentsInit200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.init(
    tenant_id="tenantId",
    content_length=1.1,
    content_sha256="contentSha256",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**content_length:** `float` 
    
</dd>
</dl>

<dl>
<dd>

**content_sha256:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` 
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**dedup_mode:** `typing.Optional[DocumentsInitRequestDedupMode]` 
    
</dd>
</dl>

<dl>
<dd>

**doc_id:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**upload_ttl_sec:** `typing.Optional[float]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Tokens
<details><summary><code>client.tokens.<a href="src/cloudpdf/tokens/client.py">issue</a>(...) -> TokensIssue200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

kind "tenant" requires the API token — authority mints only downward. Mounted only when the deployment can sign (HS256 mode); asymmetric deployments mint with their own private key.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi, TokensIssueRequest_Doc

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.tokens.issue(
    tenant_id="tenantId",
    request=TokensIssueRequest_Doc(
        sub="sub",
        doc_id="docId",
        scope=[
            "scope"
        ],
        expires_in=1,
    ),
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `TokensIssueRequest` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.tokens.<a href="src/cloudpdf/tokens/client.py">revoke</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Mounted only when the deployment enables token revocation.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.tokens.revoke(
    tenant_id="tenantId",
    jti="jti",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**tenant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**jti:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**reason:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**expires_at_seconds:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Annotations
<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">list</a>(...) -> DocAnnotationsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.list(
    doc_id="docId",
    layer_name="layerName",
    pon=1,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `int` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">create</a>(...) -> DocAnnotationsCreate200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Doc JWTs may instead carry collab scopes (annotations:create:self, …) that refine per-annotation authorship rules; the API token is exempt from both.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.create(
    doc_id="docId",
    layer_name="layerName",
    pon=1,
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `int` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocAnnotationsCreateRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">delete</a>(...) -> DocAnnotationsDelete200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.delete(
    doc_id="docId",
    layer_name="layerName",
    pon=1,
    annot_key="annotKey",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `int` 
    
</dd>
</dl>

<dl>
<dd>

**annot_key:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">update</a>(...) -> DocAnnotationsUpdate200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.update(
    doc_id="docId",
    layer_name="layerName",
    pon=1,
    annot_key="annotKey",
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**pon:** `int` 
    
</dd>
</dl>

<dl>
<dd>

**annot_key:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocAnnotationsUpdateRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Forms
<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">get</a>(...) -> DocFormsGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.get(
    doc_id="docId",
    layer_name="layerName",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">export_data</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.export_data(
    doc_id="docId",
    layer_name="layerName",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**format:** `typing.Optional[ExportDataFormsRequestFormat]` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">import_data</a>(...) -> DocFormsImportData200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.import_data(
    doc_id="docId",
    layer_name="layerName",
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocFormsImportDataRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">reset</a>(...) -> DocFormsReset200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.reset(
    doc_id="docId",
    layer_name="layerName",
    field_key="fieldKey",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**field_key:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">set_value</a>(...) -> DocFormsSetValue200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.set_value(
    doc_id="docId",
    layer_name="layerName",
    field_key="fieldKey",
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**field_key:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocFormsSetValueRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Metadata
<details><summary><code>client.doc.metadata.<a href="src/cloudpdf/doc/metadata/client.py">get</a>(...) -> DocMetadataGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.metadata.get(
    doc_id="docId",
    layer_name="layerName",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Pages
<details><summary><code>client.doc.pages.<a href="src/cloudpdf/doc/pages/client.py">delete</a>(...) -> DocPagesDelete200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.pages.delete(
    doc_id="docId",
    layer_name="layerName",
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocPagesDeleteRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.pages.<a href="src/cloudpdf/doc/pages/client.py">flatten</a>(...) -> DocPagesFlatten200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.pages.flatten(
    doc_id="docId",
    layer_name="layerName",
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocPagesFlattenRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.pages.<a href="src/cloudpdf/doc/pages/client.py">move</a>(...) -> DocPagesMove200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.pages.move(
    doc_id="docId",
    layer_name="layerName",
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocPagesMoveRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.doc.pages.<a href="src/cloudpdf/doc/pages/client.py">rotate</a>(...) -> DocPagesRotate200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.pages.rotate(
    doc_id="docId",
    layer_name="layerName",
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocPagesRotateRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Doc Redactions
<details><summary><code>client.doc.redactions.<a href="src/cloudpdf/doc/redactions/client.py">apply</a>(...) -> DocRedactionsApply200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudpdfApi

client = CloudpdfApi(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.redactions.apply(
    doc_id="docId",
    layer_name="layerName",
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocRedactionsApplyRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

