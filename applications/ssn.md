# SSN Encryption 

When applications post or update includes SSN, it needs to be encrypted. We use RSA, asymmetric public key algorithm with key size of 2048. Steps for encrypting the SSN : 

## Steps for encyrpting SSN. 

1. Generate encryption key pair in LeaseQ dashboard. 

...Production : https://dashq.leaseq.com/profile

...Demo :  http://dashq-demo.leaseq.com/profile 

2. Download public encryption file. 

...Production : https://dashq.leaseq.com/profile

...Demo :  http://dashq-demo.leaseq.com/profile 

3. Remove all white spaces and special characters ( - )  from SSN.

***Example***

```ruby
    ssn = "999-99 970"
    ssn = ssn.gsub(/[^0-9]/, '')
    puts ssn

    result: "99999970"
```

4. Use downloaded RSA public file to encrypt the SSN. 

***Example***

```ruby
  
   public_key = OpenSSL::PKey::RSA.new(File.read(public_key_file_path))

   cipher_text = public_key.public_encrypt( ssn )
  
```

5. Encode the cipher text using base 64 module and replace new line characters 

***Example***

```ruby

  encoded_text = Base64.encode64(cipher_text).gsub(/\n/, '')

  puts encoded_text

  OAKIR4u/lTQwb/y//O+STQZLkLHsD+lTV4Q/KKfCZJ2Qr3Isw66zssQpowZNobcI93091o6gYpLaYOH8S9BCqnikBxQV342f/k14nrLSZqoYm6mwYaIZMvGVhyK5RIFhYvpOM6PFq12Qh9fCD2rPgf7eI8KNx74gY1dmD2CIdGKPkqA1IdEWIIGX29725apPZasvbbBeUpVVwpIq9De23uuJ/9dGb9hZtkwD4aps0Uv3ttZEv6+M4xYCnJ3U9ZWCBWE5wKng2OssBcb6u48P1cJz0t2rCxX6YrQ41UDj1225d1TCN/Nq4FcUPtL8IaQbWl7kq+08xeD3m77FUU1Dug==

```

6. This encoded/encrypted SSN string need to be passed with application data.


## Useful link

1. [Ruby 2.0.0 Doc] (https://ruby-doc.org/stdlib-2.0.0/libdoc/openssl/rdoc/OpenSSL/PKey/RSA.html)
