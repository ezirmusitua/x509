# x509
Pure JavaScript X509 certificate tools for Node.js, includes PEM, ASN1 with DER.

[![NPM version][npm-image]][npm-url]
[![Build Status][travis-image]][travis-url]
[![Coverage Status][coveralls-image]][coveralls-url]
[![Downloads][downloads-image]][downloads-url]

## Inspired by https://github.com/digitalbazaar/forge

## example

```js
const fs = require('fs')
const { Certificate } = require('@fidm/x509')

const crtData = fs.readFileSync('./test/cert/github.crt')
const cert = Certificate.fromPEM(crtData)
console.log(cert)
// <Certificate { version: 2,
//   serialNumber: '0a0630427f5bbced6957396593b6451f',
//   signatureOID: '1.2.840.113549.1.1.11',
//   signatureAlgorithm: 'sha256WithRSAEncryption',
//   signatureParameters: null,
//   siginfo: { algorithmOID: '1.2.840.113549.1.1.11' },
//   signature: <Buffer 70 0f 5a 96 a7 58 e5 bf 8a 9d a8 27 98 2b 00 7f 26 a9 07 da ba 7b 82 54 4f af 69 cf bc f2 59 03 2b f2 d5 74 58 25 d8 1e a4 20 76 62 60 29 73 2a d7 dc ... >,
//   validFrom: '2018-05-08T00:00:00.000Z',
//   validTo: '2020-06-03T12:00:00.000Z',
//   issuer:
//    { C: 'US',
//      O: 'DigiCert Inc',
//      OU: 'www.digicert.com',
//      CN: 'DigiCert SHA2 Extended Validation Server CA',
//      uniqueId: null,
//      attributes:
//       [ { oid: '2.5.4.6',
//           value: 'US',
//           valueTag: 19,
//           name: 'countryName',
//           shortName: 'C' },
//         { oid: '2.5.4.10',
//           value: 'DigiCert Inc',
//           valueTag: 19,
//           name: 'organizationName',
//           shortName: 'O' },
//         { oid: '2.5.4.11',
//           value: 'www.digicert.com',
//           valueTag: 19,
//           name: 'organizationalUnitName',
//           shortName: 'OU' },
//         { oid: '2.5.4.3',
//           value: 'DigiCert SHA2 Extended Validation Server CA',
//           valueTag: 19,
//           name: 'commonName',
//           shortName: 'CN' } ] },
//   subject:
//    { C: 'US',
//      ST: 'California',
//      L: 'San Francisco',
//      O: 'GitHub, Inc.',
//      CN: 'github.com',
//      uniqueId: null,
//      attributes:
//       [ { oid: '2.5.4.15',
//           value: 'Private Organization',
//           valueTag: 12,
//           name: 'businessCategory',
//           shortName: '' },
//         { oid: '1.3.6.1.4.1.311.60.2.1.3',
//           value: 'US',
//           valueTag: 19,
//           name: 'jurisdictionC',
//           shortName: '' },
//         { oid: '1.3.6.1.4.1.311.60.2.1.2',
//           value: 'Delaware',
//           valueTag: 19,
//           name: 'jurisdictionST',
//           shortName: '' },
//         { oid: '2.5.4.5',
//           value: '5157550',
//           valueTag: 19,
//           name: 'serialName',
//           shortName: '' },
//         { oid: '2.5.4.6',
//           value: 'US',
//           valueTag: 19,
//           name: 'countryName',
//           shortName: 'C' },
//         { oid: '2.5.4.8',
//           value: 'California',
//           valueTag: 19,
//           name: 'stateOrProvinceName',
//           shortName: 'ST' },
//         { oid: '2.5.4.7',
//           value: 'San Francisco',
//           valueTag: 19,
//           name: 'localityName',
//           shortName: 'L' },
//         { oid: '2.5.4.10',
//           value: 'GitHub, Inc.',
//           valueTag: 19,
//           name: 'organizationName',
//           shortName: 'O' },
//         { oid: '2.5.4.3',
//           value: 'github.com',
//           valueTag: 19,
//           name: 'commonName',
//           shortName: 'CN' } ] },
//   extensions:
//    [ { id: '2.5.29.35',
//        critical: false,
//        value: <Buffer 30 16 80 14 3d d3 50 a5 d6 a0 ad ee f3 4a 60 0a 65 d3 21 d4 f8 f8 d6 0f>,
//        name: 'authorityKeyIdentifier',
//        authorityKeyIdentifier: '3dd350a5d6a0adeef34a600a65d321d4f8f8d60f' },
//      { id: '2.5.29.14',
//        critical: false,
//        value: <Buffer 04 14 c9 c2 53 61 66 9d 5f ab 25 f4 26 cd 0f 38 9a a8 49 ea 48 a9>,
//        name: 'subjectKeyIdentifier',
//        subjectKeyIdentifier: 'c9c25361669d5fab25f426cd0f389aa849ea48a9' },
//      { id: '2.5.29.17',
//        critical: false,
//        value: <Buffer 30 1c 82 0a 67 69 74 68 75 62 2e 63 6f 6d 82 0e 77 77 77 2e 67 69 74 68 75 62 2e 63 6f 6d>,
//        name: 'subjectAltName',
//        altNames:
//         [ { tag: 2,
//             value: <Buffer 67 69 74 68 75 62 2e 63 6f 6d>,
//             dnsName: 'github.com' },
//           { tag: 2,
//             value: <Buffer 77 77 77 2e 67 69 74 68 75 62 2e 63 6f 6d>,
//             dnsName: 'www.github.com' } ] },
//      { id: '2.5.29.15',
//        critical: true,
//        value: <Buffer 03 02 05 a0>,
//        name: 'keyUsage',
//        digitalSignature: true,
//        nonRepudiation: false,
//        keyEncipherment: true,
//        dataEncipherment: false,
//        keyAgreement: false,
//        keyCertSign: false,
//        cRLSign: false,
//        encipherOnly: false,
//        decipherOnly: false },
//      { id: '2.5.29.37',
//        critical: false,
//        value: <Buffer 30 14 06 08 2b 06 01 05 05 07 03 01 06 08 2b 06 01 05 05 07 03 02>,
//        name: 'extKeyUsage',
//        serverAuth: true,
//        clientAuth: true },
//      { id: '2.5.29.31',
//        critical: false,
//        value: <Buffer 30 6c 30 34 a0 32 a0 30 86 2e 68 74 74 70 3a 2f 2f 63 72 6c 33 2e 64 69 67 69 63 65 72 74 2e 63 6f 6d 2f 73 68 61 32 2d 65 76 2d 73 65 72 76 65 72 2d ... >,
//        name: 'cRLDistributionPoints' },
//      { id: '2.5.29.32',
//        critical: false,
//        value: <Buffer 30 42 30 37 06 09 60 86 48 01 86 fd 6c 02 01 30 2a 30 28 06 08 2b 06 01 05 05 07 02 01 16 1c 68 74 74 70 73 3a 2f 2f 77 77 77 2e 64 69 67 69 63 65 72 ... >,
//        name: 'certificatePolicies' },
//      { id: '1.3.6.1.5.5.7.1.1',
//        critical: false,
//        value: <Buffer 30 7a 30 24 06 08 2b 06 01 05 05 07 30 01 86 18 68 74 74 70 3a 2f 2f 6f 63 73 70 2e 64 69 67 69 63 65 72 74 2e 63 6f 6d 30 52 06 08 2b 06 01 05 05 07 ... >,
//        name: 'authorityInfoAccess',
//        authorityInfoAccessOcsp: 'http://ocsp.digicert.com',
//        authorityInfoAccessIssuers: 'http://cacerts.digicert.com/DigiCertSHA2ExtendedValidationServerCA.crt' },
//      { id: '2.5.29.19',
//        critical: true,
//        value: <Buffer 30 00>,
//        name: 'basicConstraints',
//        isCA: false,
//        maxPathLen: -1,
//        basicConstraintsValid: true },
//      { id: '1.3.6.1.4.1.11129.2.4.2',
//        critical: false,
//        value: <Buffer 04 82 01 6a 01 68 00 76 00 a4 b9 09 90 b4 18 58 14 87 bb 13 a2 cc 67 70 0a 3c 35 98 04 f9 1b df b8 e3 77 cd 0e c8 0d dc 10 00 00 01 63 41 62 6d 0a 00 ... >,
//        name: 'timestampList' } ],
//   subjectKeyIdentifier: 'c9c25361669d5fab25f426cd0f389aa849ea48a9',
//   authorityKeyIdentifier: '3dd350a5d6a0adeef34a600a65d321d4f8f8d60f',
//   ocspServer: 'http://ocsp.digicert.com',
//   issuingCertificateURL: 'http://cacerts.digicert.com/DigiCertSHA2ExtendedValidationServerCA.crt',
//   isCA: false,
//   maxPathLen: -1,
//   basicConstraintsValid: true,
//   dnsNames: [ 'github.com', 'www.github.com' ],
//   emailAddresses: [],
//   ipAddresses: [],
//   uris: [],
//   publicKey:
//    { n: 'c63caaf23c970c3ac14f28ad72707dd3ceb9b56073a4749b8a7746fd7a98424cc53019579aa9330be15d4d1058ca7799c393f3f97590bcbfbbe095ba2ec58d736105d31084a8b389b82f738cf02a6ebeeeae834b8211b161fd7761da9b1b9a23ff8c7ea20106ddd17f539608c15afae7c0cac8448c57a7a8615f660d57d3b896acb64a9cc1eae8fb964029f61530b504b0cc05b684c32459957fa26590e5b0b31a7559c43f31140ad5ccaa3a8505520632960761df27820cf785db6031f00950c5b71a23e1b07d02f5141ec9cbe87e2a3304f6513f529815e90b76475c4d4a6bc50815aef8d157e9ea7014ffc945b90c7cbcf46de60552f98c80bb7056910f4b',
//      e: 65537 },
//   publicKeyRaw: <Buffer 30 82 01 22 30 0d 06 09 2a 86 48 86 f7 0d 01 01 01 05 00 03 82 01 0f 00 30 82 01 0a 02 82 01 01 00 c6 3c aa f2 3c 97 0c 3a c1 4f 28 ad 72 70 7d d3 ce ... > }>
```

## API

### Class: PEM

### Class: ASN1

### Class: RSAPublicKey

### Class: Certificate

[npm-url]: https://www.npmjs.com/package/@fidm/x509
[npm-image]: https://img.shields.io/npm/v/@fidm/x509.svg

[travis-url]: https://travis-ci.org/fidm/x509
[travis-image]: https://img.shields.io/travis/fidm/x509.svg

[coveralls-url]: https://coveralls.io/r/fidm/x509
[coveralls-image]: https://coveralls.io/repos/fidm/x509/badge.svg

[downloads-url]: https://npmjs.org/package/@fidm/x509
[downloads-image]: https://img.shields.io/npm/dm/@fidm/x509.svg?style=flat-square
