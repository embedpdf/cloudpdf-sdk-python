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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

<details><summary><code>client.doc.<a href="src/cloudpdf/doc/client.py">changes</a>(...) -> DocChanges200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Each change stands on its own and names itself by `opId`: a refused change rolls back alone, and the answer lists every change in order, applied with its result or refused with its error. Asked again under its `opId`, a change gets the same answer, refusals included; a different change under an answered `opId` is refused (IdempotencyKeyReused). `{ opId, undoOf }` undoes an earlier change of the caller, here or in an earlier request; an undo leaves alone what was changed since, and the undo of an undo redoes. A redaction, a flatten, a form repair or a completed signature ends undo for the changes before it (UndoUnavailable). Each op is checked against its own capability: annotation ops need `doc.annotate.modify`, form values `doc.forms.fill`, form structure `doc.forms.modify`, metadata `doc.metadata.modify`, outline `doc.outline.modify`, pages `doc.pages.assemble`, embedded files `doc.attachments.modify`. Bytes (a stamp's drawing, an attached file, a signature's artwork, a PDF whose pages come in) travel as multipart: a JSON `body` part, each op naming its files by role as `resources: { <role>: '<key>' }`, and each file as the part `resource:<key>`. At most 64 changes per request and 512 ops per change.
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
from cloudpdf import CloudPDFClient
from cloudpdf.doc import DocChangesRequestChangesItem

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.changes(
    doc_id="docId",
    layer_name="layerName",
    changes=[
        DocChangesRequestChangesItem(
            op_id="opId",
        )
    ],
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

**changes:** `typing.List[DocChangesRequestChangesItem]` 
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

<details><summary><code>client.doc.<a href="src/cloudpdf/doc/client.py">download_link</a>(...) -> DocDownloadLink200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The link opens the layer as it is when created: once the layer changes, it answers 404, so create it right before handing it over. It downloads that one file and nothing else, and a password-protected document is checked when the link is created. Deployments that verify tokens with their own keys (JWKS) mint links on their backend: a doc token with `layer_name`, a `download: { docVersion, mode: "incremental" }` claim and a short `exp`, passed as `link` on the versioned download URL.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.download_link(
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

**expires_in:** `typing.Optional[int]` 
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.render(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.text(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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

## Grants
<details><summary><code>client.grants.<a href="src/cloudpdf/grants/client.py">exchange</a>(...) -> GrantsExchange200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Unauthenticated, but requires a browser Origin header, checked against the grant allowlist. Unknown, deleted, paused and archived grants are indistinguishable (404). Passphrase-protected grants return 422 GrantPassphraseRequired until `passphrase` is supplied. A grant that asks its visitors who they are on open returns 422 VisitorIdentityRequired until the required answers are given; `error.details` carries `fields` (what the grant asks), `missing`, `invalid`, `purpose` and `privacyUrl`. A grant that asks before the first change issues the session at once with `visitor.identityRequest`, and writes answer 403 VisitorIdentityRequired with the same details until the visitor exchanges again with their answers. Answers that can not be taken answer 422 on any grant. Mounted only when the deployment can sign (HS256 mode).
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.grants.exchange(
    grant="grant",
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

**grant:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**passphrase:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**visitor_handle:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**restart:** `typing.Optional[bool]` 
    
</dd>
</dl>

<dl>
<dd>

**visitor_identity:** `typing.Optional[GrantsExchangeRequestVisitorIdentity]` 
    
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

<details><summary><code>client.grants.<a href="src/cloudpdf/grants/client.py">list</a>(...) -> GrantsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.grants.list(
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

**doc_id:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**archived:** `typing.Optional[bool]` 
    
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

<details><summary><code>client.grants.<a href="src/cloudpdf/grants/client.py">create</a>(...) -> GrantsCreate200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The returned id is what a link page or an embed opens. Mounted only when the deployment can sign (HS256 mode) — exchange mints session JWTs, so grants exist only where minting does.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.grants.create(
    tenant_id="tenantId",
    doc_id="docId",
    scope=[
        "scope"
    ],
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

**doc_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**scope:** `typing.List[str]` 
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**layer_mode:** `typing.Optional[GrantsCreateRequestLayerMode]` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**keep_visitor_layers:** `typing.Optional[bool]` 
    
</dd>
</dl>

<dl>
<dd>

**visitor_idle_seconds:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**visitor_identity:** `typing.Optional[GrantsCreateRequestVisitorIdentity]` 
    
</dd>
</dl>

<dl>
<dd>

**identity:** `typing.Optional[Identity]` 
    
</dd>
</dl>

<dl>
<dd>

**origins:** `typing.Optional[typing.List[str]]` 
    
</dd>
</dl>

<dl>
<dd>

**passphrase:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**session_ttl_seconds:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**expires_at:** `typing.Optional[int]` 
    
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

<details><summary><code>client.grants.<a href="src/cloudpdf/grants/client.py">get</a>(...) -> GrantsGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.grants.get(
    tenant_id="tenantId",
    grant_id="grantId",
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

**grant_id:** `str` 
    
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

<details><summary><code>client.grants.<a href="src/cloudpdf/grants/client.py">delete</a>(...)</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.grants.delete(
    tenant_id="tenantId",
    grant_id="grantId",
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

**grant_id:** `str` 
    
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

<details><summary><code>client.grants.<a href="src/cloudpdf/grants/client.py">update</a>(...) -> GrantsUpdate200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.grants.update(
    tenant_id="tenantId",
    grant_id="grantId",
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

**grant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**layer_mode:** `typing.Optional[GrantsUpdateRequestLayerMode]` 
    
</dd>
</dl>

<dl>
<dd>

**layer_name:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**keep_visitor_layers:** `typing.Optional[bool]` 
    
</dd>
</dl>

<dl>
<dd>

**visitor_idle_seconds:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**visitor_identity:** `typing.Optional[GrantsUpdateRequestVisitorIdentity]` 
    
</dd>
</dl>

<dl>
<dd>

**identity:** `typing.Optional[Identity]` 
    
</dd>
</dl>

<dl>
<dd>

**scope:** `typing.Optional[typing.List[str]]` 
    
</dd>
</dl>

<dl>
<dd>

**origins:** `typing.Optional[typing.List[str]]` 
    
</dd>
</dl>

<dl>
<dd>

**passphrase:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**session_ttl_seconds:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**disabled:** `typing.Optional[bool]` 
    
</dd>
</dl>

<dl>
<dd>

**expires_at:** `typing.Optional[int]` 
    
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

<details><summary><code>client.grants.<a href="src/cloudpdf/grants/client.py">archive</a>(...) -> GrantsArchive200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Archiving is final: an archived grant never exchanges again, and to give access again you create a new grant. Pausing (`disabled`) is the reversible stop. An archived grant no longer counts as using its shared layer, so that layer can be deleted.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.grants.archive(
    tenant_id="tenantId",
    grant_id="grantId",
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

**grant_id:** `str` 
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

<details><summary><code>client.tenants.<a href="src/cloudpdf/tenants/client.py">resume</a>(...)</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.tenants.resume(
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

<details><summary><code>client.tenants.<a href="src/cloudpdf/tenants/client.py">suspend</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Instantly reversible with resume. The API token is exempt, so a suspended tenant can still be inspected, exported, resumed, or deleted.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.tenants.suspend(
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

**reason:** `typing.Optional[str]` 
    
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

<details><summary><code>client.tenants.<a href="src/cloudpdf/tenants/client.py">usage</a>(...) -> TenantsUsage200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Facts only — no limits or billing state. Views count grant exchanges plus authorized /v1/access requests, deduplicated across the two.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.tenants.usage(
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

**period:** `typing.Optional[str]` 
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

**state:** `typing.Optional[ListDocumentsRequestState]` — Only documents in this state. Without it, every state except deleting.
    
</dd>
</dl>

<dl>
<dd>

**q:** `typing.Optional[str]` — Only documents whose name contains this text, ignoring case.
    
</dd>
</dl>

<dl>
<dd>

**folder_id:** `typing.Optional[str]` — Only documents directly in this folder (root: the top level). Without it, documents in every folder.
    
</dd>
</dl>

<dl>
<dd>

**sort:** `typing.Optional[ListDocumentsRequestSort]` — createdAt (default), name (ignoring case), or size (stored bytes; 0 while pending).
    
</dd>
</dl>

<dl>
<dd>

**order:** `typing.Optional[ListDocumentsRequestOrder]` — Defaults to the reading order of the sort: A to Z for name, newest and largest first otherwise.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">update</a>(...) -> DocumentsUpdate200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A document that is being deleted answers 404.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.update(
    tenant_id="tenantId",
    id="id",
    name="name",
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

**name:** `str` — What people call the document: shown in dashboards, searched and sorted by. 1 to 255 characters, no control characters, no leading or trailing whitespace. Names need not be unique.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">upload_proxy</a>(...) -> DocumentsUploadProxy200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

This bounded origin-mediated fallback must only be used after documents.init returns upload.kind=proxy. Auto mode prefers a presigned object-store PUT whenever available.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.upload_proxy(
    tenant_id="tenantId",
    id="id",
    file="example_file",
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

**file:** `core.File` 
    
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

<details><summary><code>client.documents.<a href="src/cloudpdf/documents/client.py">import_from</a>(...) -> DocumentsImportFrom200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Default mode is synchronous and bounded: the response returns only after the transfer verified and committed (or failed). mode=async (connection sources only) answers 202 immediately and an in-process worker performs the transfer with leased, fenced retries; poll the document until ready/failed. The deployment import policy gates scheme, network range, and size; sources must declare a length. CloudPDF copies and owns the bytes — the source is never referenced in place. A 502 marks a retryable upstream failure: retry with the same idempotencyKey to resume the same document. URL sources are capabilities and never echoed back. Connection sources name operator-registered storage (bucket/prefix scope, allowed credential classes, and tenant bindings are deployment configuration); `revision` is provider-interpreted (S3 VersionId, GCS generation, Azure version id).
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
from cloudpdf import CloudPDFClient
from cloudpdf.documents import DocumentsImportFromRequestSource_Url

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.import_from(
    tenant_id="tenantId",
    source=DocumentsImportFromRequestSource_Url(
        url="url",
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

**source:** `DocumentsImportFromRequestSource` — Where CloudPDF pulls the bytes from. The two shapes differ in who supplies the authority to read, not in which storage vendor holds the file.
    
</dd>
</dl>

<dl>
<dd>

**expected:** `typing.Optional[DocumentsImportFromRequestExpected]` — Integrity pins, enforced when present. When absent, the server-observed values become authoritative.
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` — What people call the document: shown in dashboards, searched and sorted by. 1 to 255 characters, no control characters, no leading or trailing whitespace. Names need not be unique.
    
</dd>
</dl>

<dl>
<dd>

**folder_id:** `typing.Optional[str]` — A folder id, or root for the top level.
    
</dd>
</dl>

<dl>
<dd>

**metadata:** `typing.Optional[typing.Dict[str, typing.Any]]` 
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Retrying with the same key resumes the same document rather than importing a second copy — including after a 502.
    
</dd>
</dl>

<dl>
<dd>

**dedup_mode:** `typing.Optional[DocumentsImportFromRequestDedupMode]` — always-create (default) creates a new document every time. reuse-existing returns a document that already holds the same content instead of storing it twice.
    
</dd>
</dl>

<dl>
<dd>

**doc_id:** `typing.Optional[str]` 
    
</dd>
</dl>

<dl>
<dd>

**mode:** `typing.Optional[DocumentsImportFromRequestMode]` — sync (default) holds the response open for the whole transfer. async answers 202 with the document pending and transfers in the background; it requires a connection source, and filesystem connections additionally require expected.sha256.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

**name:** `typing.Optional[str]` — What people call the document: shown in dashboards, searched and sorted by. 1 to 255 characters, no control characters, no leading or trailing whitespace. Names need not be unique.
    
</dd>
</dl>

<dl>
<dd>

**folder_id:** `typing.Optional[str]` — A folder id, or root for the top level.
    
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

**dedup_mode:** `typing.Optional[DocumentsInitRequestDedupMode]` — always-create (default) creates a new document every time. reuse-existing returns a document that already holds the same content instead of storing it twice.
    
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

**upload_preference:** `typing.Optional[DocumentsInitRequestUploadPreference]` 
    
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

## Folders
<details><summary><code>client.folders.<a href="src/cloudpdf/folders/client.py">list</a>(...) -> FoldersList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.folders.list(
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

**parent_id:** `typing.Optional[str]` — Only the folders directly in this folder (root: the top level). Without it, every folder.
    
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

<details><summary><code>client.folders.<a href="src/cloudpdf/folders/client.py">create</a>(...) -> FoldersCreate200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

409 Conflict carries `details.reason`: `name-taken` (a sibling has the name, ignoring case; `details.name`) or `too-deep` (folders nest at most 100 levels; `details.maxDepth`). 404 when the parent folder does not exist.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.folders.create(
    tenant_id="tenantId",
    name="name",
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

**name:** `str` — What people call the folder: 1 to 255 characters, no control characters, no leading or trailing whitespace, and unique among the folder's siblings, ignoring case.
    
</dd>
</dl>

<dl>
<dd>

**parent_id:** `typing.Optional[str]` — A folder id, or root for the top level.
    
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

<details><summary><code>client.folders.<a href="src/cloudpdf/folders/client.py">get</a>(...) -> FoldersGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.folders.get(
    tenant_id="tenantId",
    folder_id="folderId",
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

**folder_id:** `str` 
    
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

<details><summary><code>client.folders.<a href="src/cloudpdf/folders/client.py">delete</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Without recursive, a folder with anything inside is refused: 409 Conflict with `details.reason` `not-empty` and what it holds, counted over every level below, in `details.folders` and `details.documents`. With recursive=true, the folder and every folder under it go at once, and every document in them stops opening, leaves every list and stops answering its grants at once; their stored files and grants are removed in the background. Uploads into those folders that have not committed cannot commit.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.folders.delete(
    tenant_id="tenantId",
    folder_id="folderId",
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

**folder_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**recursive:** `typing.Optional[bool]` — true deletes everything in the folder too. Never the default.
    
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

<details><summary><code>client.folders.<a href="src/cloudpdf/folders/client.py">update</a>(...) -> FoldersUpdate200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

409 Conflict with `details.reason` `name-taken` when a sibling has the name, ignoring case.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.folders.update(
    tenant_id="tenantId",
    folder_id="folderId",
    name="name",
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

**folder_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**name:** `str` — What people call the folder: 1 to 255 characters, no control characters, no leading or trailing whitespace, and unique among the folder's siblings, ignoring case.
    
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

<details><summary><code>client.folders.<a href="src/cloudpdf/folders/client.py">move_into</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Up to 1,000 ids in total. A folder moves with everything in it. 404 NotFound names the ids that do not exist or are being deleted in `details.documentIds` and `details.folderIds`. 409 Conflict carries `details.reason`: `cycle` (the destination is a moved folder or inside one; `details.folderId`), `too-deep` (the move would nest folders deeper than 100 levels; `details.maxDepth`) or `name-taken` (a moved folder's name is taken in the destination, ignoring case; `details.name`).
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.folders.move_into(
    tenant_id="tenantId",
    folder_id="folderId",
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

**folder_id:** `str` — A folder id, or root for the top level.
    
</dd>
</dl>

<dl>
<dd>

**document_ids:** `typing.Optional[typing.List[str]]` 
    
</dd>
</dl>

<dl>
<dd>

**folder_ids:** `typing.Optional[typing.List[str]]` 
    
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
from cloudpdf import CloudPDFClient, TokensIssueRequest_Doc

client = CloudPDFClient(
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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
<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">list_all</a>(...) -> DocAnnotationsListAll200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns one entry per page plus the audit-log cursor for reconciling subsequent document events. Page order is unspecified; join by `page` (a `PageRef`) when display order matters.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.list_all(
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

<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">list</a>(...) -> DocAnnotationsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.list(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.create(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.delete(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annot_key:** `str` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.update(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annot_key:** `str` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
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

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">read_appearance</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.read_appearance(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annot_key:** `str` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
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

<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">read_file</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A file that decodes past the server's limit is refused (PayloadTooLarge).
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.read_file(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annot_key:** `str` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
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

<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">export_appearance</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.export_appearance(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
    request={
        "string": {"key": "value"}
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocAnnotationsExportAppearanceRequest` 
    
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

<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">flatten</a>(...) -> DocAnnotationsFlatten200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.flatten(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**request:** `DocAnnotationsFlattenRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.annotations.<a href="src/cloudpdf/doc/annotations/client.py">reorder</a>(...) -> DocAnnotationsReorder200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient, AnnotationRef_ObjectNumber, PageRef

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.annotations.reorder(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
    refs=[
        AnnotationRef_ObjectNumber(
            page=PageRef(
                kind="objectNumber",
                object_number=1,
            ),
            object_number=1,
        )
    ],
    position="start",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**refs:** `typing.List[AnnotationRef]` 
    
</dd>
</dl>

<dl>
<dd>

**position:** `AnnotationPosition` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

## Doc Attachments
<details><summary><code>client.doc.attachments.<a href="src/cloudpdf/doc/attachments/client.py">download</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A file that decodes past the server's limit is refused (PayloadTooLarge).
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.attachments.download(
    doc_id="docId",
    layer_name="layerName",
    file_key="fileKey",
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

**file_key:** `str` — The embedded file's name-tree key (its `ref.key`), token-text encoded, as `fieldKey` is.
    
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

<details><summary><code>client.doc.attachments.<a href="src/cloudpdf/doc/attachments/client.py">list</a>(...) -> DocAttachmentsList200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A file-attachment annotation's file is listed with the annotation; read its bytes with `doc.annotations.readFile`.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.attachments.list(
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

## Doc Forms
<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">list</a>(...) -> DocFormsList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.list(
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

<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">reorder_calculations</a>(...) -> DocFormsReorderCalculations200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient, FormFieldRef_ObjectNumber

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.reorder_calculations(
    doc_id="docId",
    layer_name="layerName",
    fields=[
        FormFieldRef_ObjectNumber(
            object_number=1,
        )
    ],
    position="start",
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

**fields:** `typing.List[FormFieldRef]` 
    
</dd>
</dl>

<dl>
<dd>

**position:** `FieldPosition` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.reset(
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

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**refs:** `typing.Optional[typing.List[FormFieldRef]]` 
    
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

<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">delete_widget</a>(...) -> DocFormsDeleteWidget200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.delete_widget(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annot_key:** `str` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">update_widget</a>(...) -> DocFormsUpdateWidget200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient, WidgetPatch

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.update_widget(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
    annot_key="annotKey",
    patch=WidgetPatch(),
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**annot_key:** `str` — The annotation's address on the page: `obj:N`, its indirect object number, or `base:N` for an annotation the uploaded file stored inline (without an object number of its own), the position it was born at in the page's /Annots. The name the annotation's `ref` carries for life.
    
</dd>
</dl>

<dl>
<dd>

**patch:** `WidgetPatch` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.forms.<a href="src/cloudpdf/doc/forms/client.py">reorder_widgets</a>(...) -> DocFormsReorderWidgets200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient, AnnotationRef_ObjectNumber, PageRef

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.forms.reorder_widgets(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
    widgets=[
        AnnotationRef_ObjectNumber(
            page=PageRef(
                kind="objectNumber",
                object_number=1,
            ),
            object_number=1,
        )
    ],
    position="start",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**widgets:** `typing.List[AnnotationRef]` 
    
</dd>
</dl>

<dl>
<dd>

**position:** `AnnotationPosition` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

## Doc Outline
<details><summary><code>client.doc.outline.<a href="src/cloudpdf/doc/outline/client.py">get</a>(...) -> DocOutlineGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.outline.get(
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
<details><summary><code>client.doc.pages.<a href="src/cloudpdf/doc/pages/client.py">set_scale</a>(...) -> DocPagesSetScale200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.pages.set_scale(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**measure:** `typing.Optional[DocPagesSetScaleRequestMeasure]` 
    
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

<details><summary><code>client.doc.pages.<a href="src/cloudpdf/doc/pages/client.py">viewports</a>(...) -> DocPagesViewports200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.pages.viewports(
    doc_id="docId",
    layer_name="layerName",
    page_key="pageKey",
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

**page_key:** `str` — The page's address, `obj:N`: the page's indirect object number, the durable identity every `PageLayout.ref` carries. Mirrors `annotKey` and `fieldKey`.
    
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

<details><summary><code>client.doc.pages.<a href="src/cloudpdf/doc/pages/client.py">extract</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A read, not a mutation: the source document is untouched and no event is published. Body is `{"pages": PageRef[], "flatten"?: {"usage"?: "display" | "print"}, "includeAnnotations"?: boolean, "includeFormFields"?: boolean}`; the response body is the new PDF. With `flatten` the copy is the pages as they draw for `usage` (`"print"`: a print copy): the annotations and form fields painted in, nothing interactive left, layers in their state for the usage. A flattened copy takes `doc.download` or `doc.download.flattened`, and paints only what the caller may read; `includeAnnotations` and `includeFormFields` choose what it paints, and are refused without `flatten`.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.pages.extract(
    doc_id="docId",
    layer_name="layerName",
    request={
        "string": {"key": "value"}
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

**request:** `DocPagesExtractRequest` 
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
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

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.pages.<a href="src/cloudpdf/doc/pages/client.py">set_name</a>(...) -> DocPagesSetName200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.pages.set_name(
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

**request:** `DocPagesSetNameRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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

<details><summary><code>client.doc.pages.<a href="src/cloudpdf/doc/pages/client.py">remove_name</a>(...) -> DocPagesRemoveName200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.pages.remove_name(
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

**request:** `DocPagesRemoveNameRequest` 
    
</dd>
</dl>

<dl>
<dd>

**document_password:** `typing.Optional[str]` — Base64-encoded password for an encrypted document. Valid only with the API token (403 anywhere else). An encrypted document answers 422 DocPasswordRequired when the header is absent. Viewer doc JWTs use the SDK password-session flow instead.
    
</dd>
</dl>

<dl>
<dd>

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.redactions.apply(
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

**idempotency_key:** `typing.Optional[str]` — Names the change: 1 to 255 printable ASCII characters. A retry under the same key on the same layer answers with what the first request committed, and changes nothing.
    
</dd>
</dl>

<dl>
<dd>

**pages:** `typing.Optional[typing.List[PageRef]]` 
    
</dd>
</dl>

<dl>
<dd>

**annotations:** `typing.Optional[typing.List[AnnotationRef]]` 
    
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

## Doc Signatures
<details><summary><code>client.doc.signatures.<a href="src/cloudpdf/doc/signatures/client.py">list</a>(...) -> DocSignaturesList200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Describes the bytes the layer is over: the base version's signatures plus the layer's own edits as the last revision. Signed bytes (contents, digests, revision prefixes) are served per base version under /versions.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.signatures.list(
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

<details><summary><code>client.doc.signatures.<a href="src/cloudpdf/doc/signatures/client.py">cancel</a>(...) -> DocSignaturesCancel200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.signatures.cancel(
    doc_id="docId",
    layer_name="layerName",
    signing_id="signingId",
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

**signing_id:** `str` 
    
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

<details><summary><code>client.doc.signatures.<a href="src/cloudpdf/doc/signatures/client.py">complete</a>(...) -> DocSignaturesComplete200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

`cms` is the detached CMS over the prepared digest, base64. `expectedVersion` must be what prepare returned. Idempotent by signing id: the same CMS again answers `already-completed`. The new version is the layer's own: only this layer moves to it, and the document and every other layer stay as they were. Refetch the manifest after a completion.
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
from cloudpdf import CloudPDFClient
from cloudpdf.doc.signatures import DocSignaturesCompleteRequestExpectedVersion

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.signatures.complete(
    doc_id="docId",
    layer_name="layerName",
    signing_id="signingId",
    cms="cms",
    expected_version=DocSignaturesCompleteRequestExpectedVersion(
        base_sha256="baseSha256",
        edits_version=1,
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

**signing_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**cms:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**expected_version:** `DocSignaturesCompleteRequestExpectedVersion` 
    
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

<details><summary><code>client.doc.signatures.<a href="src/cloudpdf/doc/signatures/client.py">analysis</a>(...) -> DocSignaturesAnalysis200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Exactly one of `since.signature=<index>` or `since.revision=<index>`; the layer's pending edits are the end. `level=fill|annotate|lta|none` evaluates exploratorily and never becomes a verdict. For history between two base revisions use the version analysis.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.signatures.analysis(
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

**since_signature:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**since_revision:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**level:** `typing.Optional[AnalysisSignaturesRequestLevel]` 
    
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

<details><summary><code>client.doc.signatures.<a href="src/cloudpdf/doc/signatures/client.py">prepare</a>(...) -> DocSignaturesPrepare200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Multipart: a JSON `body` part (field, subFilter, digest, contentsSize, signer, certify, lock), naming the appearance PDF it may carry as `resources: { appearance: '<key>' }`, and that PDF as the part `resource:<key>`. A certification (`certify.permission`) additionally requires `doc.sign.certify`. The layer is read-only until the signing completes, is cancelled, or expires (15 minutes). The signature is made over the layer's own base: the upload, or the version its last signature made.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.signatures.prepare(
    doc_id="docId",
    layer_name="layerName",
    file="example_file",
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

**file:** `core.File` 
    
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

## Doc Versions
<details><summary><code>client.doc.versions.<a href="src/cloudpdf/doc/versions/client.py">list</a>(...) -> DocVersionsList200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Every completed signature makes a new version of its layer; another layer's versions are never listed. Never cached: the list grows.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.versions.list(
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

<details><summary><code>client.doc.versions.<a href="src/cloudpdf/doc/versions/client.py">analysis</a>(...) -> DocVersionsAnalysis200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Exactly one of `since.signature` / `since.revision`; `until=<revision>` defaults to the last. The same answer for every caller.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.versions.analysis(
    doc_id="docId",
    layer_name="layerName",
    sha="sha",
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

**sha:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**since_signature:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**since_revision:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**level:** `typing.Optional[AnalysisVersionsRequestLevel]` 
    
</dd>
</dl>

<dl>
<dd>

**until:** `typing.Optional[int]` 
    
</dd>
</dl>

<dl>
<dd>

**policy:** `typing.Optional[int]` 
    
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

<details><summary><code>client.doc.versions.<a href="src/cloudpdf/doc/versions/client.py">download</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.versions.download(
    doc_id="docId",
    layer_name="layerName",
    sha="sha",
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

**sha:** `str` 
    
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

<details><summary><code>client.doc.versions.<a href="src/cloudpdf/doc/versions/client.py">revision</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.versions.revision(
    doc_id="docId",
    layer_name="layerName",
    sha="sha",
    index=1,
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

**sha:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**index:** `int` 
    
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

<details><summary><code>client.doc.versions.<a href="src/cloudpdf/doc/versions/client.py">signatures</a>(...) -> DocVersionsSignatures200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.versions.signatures(
    doc_id="docId",
    layer_name="layerName",
    sha="sha",
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

**sha:** `str` 
    
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

<details><summary><code>client.doc.versions.<a href="src/cloudpdf/doc/versions/client.py">signature_contents</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

`fieldKey` is the field's fully qualified name, token-text encoded (the same encoding attachment keys use).
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.versions.signature_contents(
    doc_id="docId",
    layer_name="layerName",
    sha="sha",
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

**sha:** `str` 
    
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

<details><summary><code>client.doc.versions.<a href="src/cloudpdf/doc/versions/client.py">signature_digest</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

What a CMS verifier compares its message digest to.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.versions.signature_digest(
    doc_id="docId",
    layer_name="layerName",
    sha="sha",
    field_key="fieldKey",
    algorithm="sha1",
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

**sha:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**field_key:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**algorithm:** `SignatureDigestVersionsRequestAlgorithm` 
    
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

## Doc Metadata Custom
<details><summary><code>client.doc.metadata.custom.<a href="src/cloudpdf/doc/metadata/custom/client.py">get</a>(...) -> DocMetadataCustomGet200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.doc.metadata.custom.get(
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

## Documents Layers
<details><summary><code>client.documents.layers.<a href="src/cloudpdf/documents/layers/client.py">list</a>(...) -> DocumentsLayersList200Response</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.layers.list(
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

**grant_id:** `typing.Optional[str]` 
    
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

<details><summary><code>client.documents.layers.<a href="src/cloudpdf/documents/layers/client.py">delete</a>(...)</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.documents.layers.delete(
    tenant_id="tenantId",
    id="id",
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

**layer_name:** `str` 
    
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

## Grants Visitors
<details><summary><code>client.grants.visitors.<a href="src/cloudpdf/grants/visitors/client.py">list</a>(...) -> GrantsVisitorsList200Response</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

An archived grant's visitors are listed too.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.grants.visitors.list(
    tenant_id="tenantId",
    grant_id="grantId",
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

**grant_id:** `str` 
    
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

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.grants.visitors.<a href="src/cloudpdf/grants/visitors/client.py">delete</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Their handle brings them back as a new visitor, who is asked again. Deleting a visitor already deleted changes nothing.
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
from cloudpdf import CloudPDFClient

client = CloudPDFClient(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.grants.visitors.delete(
    tenant_id="tenantId",
    grant_id="grantId",
    visitor_id="visitorId",
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

**grant_id:** `str` 
    
</dd>
</dl>

<dl>
<dd>

**visitor_id:** `str` 
    
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

