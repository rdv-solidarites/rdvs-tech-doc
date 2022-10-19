# Vérification de signature

Voilà quelques exemples et informations très pratiques pour valider la signature des corps de requêtes envoyées par RDV-Solidarités.

* En Ruby

```ruby
require 'openssl'
secret = "secret"
data = "content"
mac = OpenSSL::HMAC.hexdigest("SHA256", secret, data)
puts(data) puts(mac)
```

* En Python

```python
import hashlib
import hmac
import sys

def main():
  content = sys.argv[len(sys.argv)-1]
  h = hmac.new(str.encode('secret'), digestmod='sha256')

  print(content)
  h.update(str.encode(content))
  print(h.hexdigest())

if __name__ == '__main__':
  main()
```

* En NodeJS

```javascript
const crypto = require('crypto')
const prefixIndex = process.argv.indexOf('--content') if (prefixIndex == -1 || process.argv.length <= prefixIndex + 1) { console.log('--content [content] are mandatory') process.exit(1) }
const hmac = crypto.createHmac('sha256', process.env.SHARED_SECRET) const content = process.argv[prefixIndex+1]
console.log(content)
hmac.update(content) console.log(hmac.digest('hex'))
```

* En C\#

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Security.Cryptography;
using System.IO;
using System.Runtime.Remoting.Metadata.W3cXsd2001;

namespace SignatureValidation
{
    class Program
    {
        // Pour l'utilisation de SoapHexBinary
        // cf.
        // https://stackoverflow.com/questions/311165/how-do-you-convert-a-byte-array-to-a-hexadecimal-string-and-vice-versa/2556329#2556329
        static void Main(string[] args)
        {
            int keyPrefix = Array.IndexOf(args, "--key");
            int contentPrefix = Array.IndexOf(args, "--content");
            int signaturePrefix = Array.IndexOf(args, "--signature");

            string key = args[keyPrefix+1];
            string content = args[contentPrefix+1];

            byte[] keyBytes = Encoding.UTF8.GetBytes(key);
            HMACSHA256 hash = new HMACSHA256(keyBytes);

            byte[] byteArray = Encoding.UTF8.GetBytes(content);
            MemoryStream stream = new MemoryStream(byteArray);

            byte[] signature = hash.ComputeHash(stream);

            SoapHexBinary shb = new SoapHexBinary(signature);
            string hexaRepresentation = shb.ToString();
            System.Console.WriteLine(hexaRepresentation);

            if (signaturePrefix>= 0) {
                string providedSignature = args[signaturePrefix+1];
                byte[] providedSignatureBytes = SoapHexBinary.Parse(providedSignature).Value;

                System.Console.WriteLine(providedSignatureBytes.SequenceEqual(signature));
            }

            return;
        }
    }
}
```

