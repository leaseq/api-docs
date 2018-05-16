# Encryption of Sensitive Data

LeaseQ requires certain data/fields be encrypted to ensure sensitive data remains private. LeaseQ use RSA - asymmetric public key algorithm with key size of 4096.

## Steps to perform encryption

#### 1. Download the key
  * Demo: http://dashq-demo.leaseq.com/profile 
  * Production: https://dashq.leaseq.com/profile

#### 2. Load the key file
```ruby
public_key = OpenSSL::PKey::RSA.new(File.read(public_key_file_path))
```

#### 2. Encrypt

```ruby
cipher_text = public_key.public_encrypt( sensitive_data )
```

#### 3. Encode

```ruby
encoded_text = Base64.encode64(cipher_text).gsub(/\n/, '')
```

JSON cannot handle the raw output of `public_encrypt`, so base64-encode it and remove any line breaks.

## Example

```ruby
require 'openssl'
require 'base64'
require 'net/http'
require 'json'


def encrypt(sensitive_data, public_key_file_path)

  public_key = OpenSSL::PKey::RSA.new(File.read(public_key_file_path))

  cipher_text = public_key.public_encrypt(sensitive_data)

  encoded_text = Base64.encode64(cipher_text).gsub(/\n/, '')

  return encoded_text

end


ssn = encrypt("000-00-0000", "public_key.pem")


URI('https://localhost:8080/api/endpoint')
req = Net::HTTP::Post.new(uri.path, initheader = {'Content-Type' =>'application/json'})
req.body = { :ssn => encoded_text }.to_json
response = https.request(req)


puts ssn
puts response
```
## Useful links

1. [Ruby 2.0.0 Doc](https://ruby-doc.org/stdlib-2.0.0/libdoc/openssl/rdoc/OpenSSL/PKey/RSA.html)
