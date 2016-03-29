akashic-storage supports a subset of [AWS S3 APIs](http://docs.aws.amazon.com/ja_jp/AmazonS3/latest/API/APIRest.html)

## I/O Operations

### Basic PUT/GET

| API Name | Status | Remarks |
|:--|:--|:--|
| GET Service | Supported | Conditional (If-Match, ...) and Range header is supported |
| PUT Bucket | Supported | |
| GET Bucket | Supported | |
| PUT Object | Supported | |
| GET Object | Supported | |
| HEAD Object | Supported | |
| HEAD Bucket | Supported | |


### Delete Bucket/Object

| API Name | Status | Remarks |
|:--|:--|:--|
| Delete Bucket | Supported | |
| Delete Object | Supported | |

### Multipart Upload

| API Name | Status | Remarks |
|:--|:--|:--|
| Initiate Multipart Upload | Supported | |
| Complete Multipart Upload | Supported | |
| List Multipart Upload | Supported | |
| Abort Multipart Upload | Supported | |
| List Parts | Supported | |

### POST Object

With Akka-HTTP (2.4.2) it's really hard (nearly impossible) to implement POST Object.
Also I don't think there are any potential users of this API.
I definitely won't support this.

| API Name | Status | Remarks |
|:--|:--|:--|
| POST Object | Not Supported | Never Supported |

## Subresources

## Access Control List (ACL)

ACL is used to grant permissions to resources.
As for the grantee type, both authenticated user and anonymous user
is supported.

| API Name | Status | Remarks |
|:--|:--|:--|
| PUT Bucket acl | Supported | |
| GET Bucket acl | Supported | |
| PUT Object acl | Supported | |
| GET Object acl | Supported | |

## Policy

Because I think having ACL is almost sufficient
I have no idea at the present to implement access control by Policy.

## Location
Location is supported but returns false us-east-1, the default location in AWS S3.

| API Name | Status | Remarks |
|:--|:--|:--|
| PUT Bucket acl | Supported | |

## Versioning
In v1.0, versioning isn't supported because of the implementation complexity.
I definitely will support this in beyond v1.0.

| API Name | Status | Remarks |
|:--|:--|:--|
| GET Bucket Object Versions | Supported | |

## Cross Origin Resource Sharing (CORS)

CORS is required when client issues AJAX requests to a server in a difference origin.
akashic-storage can theoretically support these APIs but
for the time being, I don't want to provide this because
proxy servers that stands ahead of akashic-storage often provides basic CORS settings.
Since S3's CORS specification is bit different from the standard, I don't have idea to
implement this in the future.

| API Name | Status | Remarks |
|:--|:--|:--|
| PUT Bucket cors | Not Supported | Unwilling |
| OPTIONS Object | Not Supported | Unwilling |





