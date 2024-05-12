# GmSSL

[![CMake-Ubuntu/macOS](https://github.com/guanzhi/GmSSL/workflows/CMake/badge.svg)](https://github.com/guanzhi/GmSSL/actions/workflows/cmake.yml)

[![CMake-Windows](https://github.com/guanzhi/GmSSL/workflows/CMake-windows/badge.svg)](https://github.com/guanzhi/GmSSL/actions/workflows/cmake-windows.yml)

[![CMake-Android](https://github.com/guanzhi/GmSSL/actions/workflows/android-ci.yml/badge.svg)](https://github.com/guanzhi/GmSSL/actions/workflows/android-ci.yml)

[![CMake-iOS](https://github.com/guanzhi/GmSSL/actions/workflows/ios.yml/badge.svg)](https://github.com/guanzhi/GmSSL/actions/workflows/ios.yml)

GmSSL is a domestic commercial cryptographic open-source library independently developed by Peking University. It fully covers the functionality of national cryptographic algorithms, standards, and secure communication protocols, supports mainstream operating systems and processors including mobile devices, supports typical domestic cryptographic hardware such as cryptographic keys and cards, and provides feature-rich command-line tools and programming interfaces in various programming languages.

## Main Features

* Ultra-lightweight: GmSSL 3 significantly reduces memory requirements and binary code size, does not depend on dynamic memory, and can be used in low-power embedded environments without an operating system (MCU, SOC, etc.). Developers can also more easily embed national cryptographic algorithms and SSL protocols into existing projects.

* More compliant: GmSSL 3 can be configured to only include national cryptographic algorithms and protocols (TLCP protocol), making it easier for cryptographic applications that depend on GmSSL to meet the requirements of cryptographic product model testing and avoid security and compliance issues caused by mixing non-national cryptographic algorithms and insecure algorithms.

* More secure: TLS 1.3 has greatly improved security and communication latency compared to previous TLS protocols. GmSSL 3 supports the TLS 1.3 protocol and the national cryptographic suites in RFC 8998. GmSSL 3 supports encrypted protection of keys by default, enhancing the side-channel attack resistance of cryptographic algorithms.

* Cross-platform: GmSSL 3 is easier to use across platforms. The build system no longer depends on Perl. The default CMake build system can easily work with default compilation tools such as Visual Studio and Android NDK. Developers can also manually write Makefiles to compile and tailor in special environments.

## Download

* The main branch version of GmSSL is [GmSSL-3.1.1](https://github.com/guanzhi/GmSSL/releases/tag/v3.1.1), which mainly adds cross-platform features, especially support for Windows/Visual Studio. Developers on Windows, Android, and iOS platforms need to use this version.

## Compilation and Installation

GmSSL 3 uses the CMake build system. After downloading the source code and extracting it, enter the source code directory and execute:

```bash
mkdir build
cd build
cmake ..
make
make test
sudo make install
```

After `make install` is completed, GmSSL will install the `gmssl` command-line tool in the default installation directory, create a `gmssl` directory in the header file directory, and install library files such as `libgmssl.a` and `libgmssl.so` in the library directory.

### Compiling in Visual Studio Environment

Execute the following in the Visual Studio command prompt:

```bash
mkdir build
cd build
cmake .. -G "NMake Makefiles" -DWIN32=ON
nmake
```

## Main Functions

### Cryptographic Algorithms

* Block ciphers: SM4 (CBC/CTR/GCM), AES (CBC/CTR/GCM)
* Stream ciphers: ZUC/ZUC-256, ChaCha20, RC4
* Hash functions: SM3, SHA-224/256/384/512, SHA-1, MD5
* Public key cryptography: SM2 encryption/signature, SM9 encryption/signature
* MAC algorithms: HMAC, GHASH
* Key derivation functions: PBKDF2, HKDF
* Random number generators: Intel RDRAND, HASH_DRBG (NIST.SP.800-90A)

### Certificates and Digital Envelopes

* Digital certificates: X.509 certificates, CRL (certificate revocation lists), CSR (PKCS #10) certificate signing requests
* Private key encryption: PEM format private keys encrypted with SM4/SM3 password (PKCS #8)
* Digital envelopes: SM2 cryptographic messages (GM/T 0010-2012)

### SSL Protocols

* TLCP 1.1, supports cipher suite `TLS_ECC_SM4_CBC_SM3 {0xE0,0x13}` (GB/T 38636-2020, GM/T 0024-2014)
* TLS 1.2, supports cipher suite `TLS_ECDHE_SM4_CBC_SM3 {0xE0,0x11}` (GB/T 38636-2020, GM/T 0024-2014)
* TLS 1.3, supports cipher suite `TLS_SM4_GCM_SM3 {0x00,0xC6}` (RFC 8998)

### Multi-Language Interfaces

GmSSL provides bindings for various programming languages through sub-projects
* [GmSSL-Java](https://github.com/GmSSL/GmSSL-Java) Java language binding implemented using JNI
* [GmSSL-PHP](https://github.com/GmSSL/GmSSL-PHP) PHP language binding implemented as a PHP extension
* [GmSSL-Go](https://github.com/GmSSL/GmSSL-Go) Go language binding implemented using CGO
* [GmSSL-Python](https://github.com/GmSSL/GmSSL-Python) Python language binding implemented using ctypes
* [GmSSL-JS](https://github.com/guanzhi/GmSSL-JS) Pure JavaScript implementation of the national cryptographic algorithm library

## Typical Applications

#### Nginx-with-GmSSL3.0
GmSSL supports adaptation to Nginx and provides a Docker implementation. For details, see the [Nginx-with-GmSSL3.0](https://github.com/zhaoxiaomeng/Nginx-with-GmSSLv3) project.

## Roadmap

- [X] Add Windows Visual Studio support
- [X] Add Windows Cygwin support 
- [X] Add iOS support
- [X] Add Android support
- [x] **Version 3.1.0 release**
- [ ] Add GCC specific optimization
- [ ] Add X86_64 assembly implementation
- [ ] Add GPU implementation
- [ ] Add performance benchmark tool
- [ ] Add GCM cipher suites
- [ ] Release official open interfaces
- [ ] **Version 3.2.0 release**

## Developers
<a href="https://github.com/guanzhi/GmSSL/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=guanzhi/GmSSL" />
</a>

## Stargazers over time
[![Stargazers over time](https://starchart.cc/guanzhi/GmSSL.svg)](https://starchart.cc/guanzhi/GmSSL)
