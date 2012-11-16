Lufthansa Passbook Passes

Lufthansa Pass files follow the following naming convention:

lufthansa_xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx.pkpass

xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx is Version 4 UUID (http://en.wikipedia.org/wiki/Universally_unique_identifier#Version_4_.28random.29)

They are stored on disk as a zipped package with the pkpass file extension. 

The top level of the package contains the following files:

    icon.png 

The pass’s icon. This is displayed in notifications and in emails that have a pass attached, and on the lock screen. When it is displayed, the icon gets a shine effect and rounded corners.

    logo.png 

The image displayed on the front of the pass in the top left.

    manifest.json 

A JSON dictionary. Each key is the path to a file (relative to the top level of the bundle) and the key’s value is the SHA-1 hash for that file. Every file in the bundle appears in the manifest, except for the manifest itself and the signature.

    pass.json 

A JSON (JavaScript Object Notation) dictionary that defines the pass. Its contents are described in detail in “Top-Level Keys.”

    signature 

A detached PKCS#7 signature of the manifest.json file.

Get Worldwide Developer Relations Certificate from http://www.apple.com/certificateauthority/

Get Apple Pass Certificate from iOS Provisiong Portal

openssl pkcs12 -passin pass:"somepass" -in "mycert.p12" -clcerts -nokeys -out certificate.pem
openssl pkcs12 -passin pass:"somepass" -in "mycert.p12" -nocerts -out key.pem -passout pass:"somepass"
openssl smime -binary -sign -certfile WWDR.pem -signer certificate.pem -inkey key.pem -in manifest.json -out signature -outform DER -passin pass:"somepass"


Note: All of the pass’s images are loaded using standard UIImage image-loading methods. This means, for example, the file name of high resolution (retina) version of the image ends with @2x.png. 