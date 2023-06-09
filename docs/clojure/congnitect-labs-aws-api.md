# Congnitect Labs AWS API

[:fontawesome-brands-github: Congnitect Labs AWS API](https://github.com/cognitect-labs/aws-api){target=_blank .md-button}

[:fontawesome-brands-github: Congnitect Labs AWS API](https://github.com/cognitect-labs/aws-api){target=_blank} is an idiomatic, data-oriented Clojure library for invoking AWS APIs.

AWS APIs are described in data that specifies operations, inputs and outputs.

aws-api uses the data descriptions to expose a data-oriented interface, using service descriptions, documentation and specs generated from the source descriptions.

Data descriptions are versioned, e.g. `com.cognitect.aws/dynamo-db-653.2.351.0`

[:fontawesome-brands-github: AWS API Descriptors](https://github.com/aws/aws-sdk-js/tree/master/apis){target=_blank .md-button}

> AWS API uses data descriptions from [:fontawesome-brands-github: aws-sdk-js](https://github.com/aws/aws-sdk-js/) but does not wrap the any language SDK, which would tie you to that workflow

The main functions are

- `client` - create a client for a given service
- `invoke` - an operation on the service (assumption:? via the client), takes and returns a hash-map


Helper functions:


## Library Dependencies

[:fontawesome-brands-github: AWS API - latest-releases.edn](https://github.com/cognitect-labs/aws-api/blob/main/latest-releases.edn){target=_blank .md-button}

!!! EXAMPLE "S3 Bucket"
```clojure
com.cognitect.aws/api       {:mvn/version "0.8.666"}
com.cognitect.aws/endpoints {:mvn/version "1.1.12.456"}
com.cognitect.aws/s3        {:mvn/version "847.2.1365.0"}
```

## REPL workflow

Create a project with a `deps.edn` file that contains the library dependencies for Cognitect Labs AWS API.

Require the client API.

``` clojure
(require '[cognitect.aws.client.api :as aws])
```

Create a client

```clojure
(def s3 (aws/client {:api :s3}))
```

Ask what operations the client can perform

``` clojure
(aws/ops s3)
```

Request documentation for an operation

``` clojure
(aws/doc s3 :CreateBucket)
```

Instruct the client to validate requests, reporting when incorrect arguments are used

``` clojure
(aws/validate-requests s3 true)
```

List the S3 buckets

``` clojure
(aws/invoke s3 {:op :ListBuckets})
;; => {:Buckets [{:Name <name> :CreationDate <date> ,,,}]}

Get the meta data from the previous expression, i.e. list buckets
http-request and http-response are in the metadata
```clojure
(meta *1)
;; => {:http-request {:request-method :get,
;;                    :scheme :https,
;;                    :server-port 443,
;;                    :uri "/",
;;                    :headers {,,,},
;;                    :server-name "s3.amazonaws.com",
;;                    :body nil},
;;     :http-response {:status 200,
;;                     :headers {,,,},
;;                     :body <input-stream>}
```

Create bucket in the same region as client

```clojure
(aws/invoke s3 {:op :CreateBucket :request {:Bucket "my-unique-bucket-name"}})
```

Create a bucket in a region other than us-east-1

```clojure
(aws/invoke s3 {:op :CreateBucket :request {:Bucket "my-unique-bucket-name-in-us-west-1"
                                            :CreateBucketConfiguration
                                            {:LocationConstraint "us-west-1"}}})
```

> NOTE: be sure to create a client with region "us-west-1" when accessing that bucket.

```clojure
(aws/invoke s3 {:op :ListBuckets})
```
