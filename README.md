# goamz - An Amazon Library for Go 

[![Build Status](https://travis-ci.org/henrysher/goamz.svg)](https://travis-ci.org/henrysher/goamz)

Current API documentation: [![GoDoc](https://godoc.org/github.com/henrysher/goamz?status.svg)](https://godoc.org/github.com/henrysher/goamz)

This is a fork of [https://launchpad.net/goamz](https://launchpad.net/goamz)
that adds some missing API calls to certain packages.

This library is *incomplete*, but implements a large amount of the AWS API.
It is heavily used in projects such as
[Terraform](https://github.com/hashicorp/terraform) and
[Packer](https://github.com/mitchellh/packer). 
If you find anything missing from this library, 
please [file an issue](https://github.com/mitchellh/goamz).

## Example Usage

```go
package main

import (
  "github.com/mitchellh/goamz/aws"
  "github.com/mitchellh/goamz/s3"
  "log"
  "fmt"
)

func main() {
  auth, err := aws.EnvAuth()
  if err != nil {
    log.Fatal(err)
  }
  client := s3.New(auth, aws.USEast)
  resp, err := client.ListBuckets()

  if err != nil {
    log.Fatal(err)
  }

  log.Print(fmt.Sprintf("%T %+v", resp.Buckets[0], resp.Buckets[0]))
}
```
