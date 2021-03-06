# WebCrypto QR

This is a WebCrypto example demonstrating the following:

- A user visits the page and is prompted for a password and a message
- The message is encrypted with the password
- A code is displayed showing the resulting buffer
- Another user scans the code and is prompted for a password
- The message is decrypted with the password

It demonstrates hard boundaries which are not respected in many WebCrypto
examples making them useless as aids in implementing a problem such as this
one.

The first boundary is the password being also prompted for anew. It is not
stored anywhere. We have to derive the key from the password each time and
we do not get to store it. We also don't get to generate it for the sake
of an example, leaving out the derivation completely!

The second boundary is the transfer of the cypher buffer over the QR code.
We don't get to pass more context around (like intermediate values) nor do
we get to rely on a structured data or any shared global state. The only
thing we are privy to across this channel is the standalone cypher buffer.

## To-Do

### Wait for the Shape Detection API to be available in Firefox and prototype

I could use something like [jsQR](https://github.com/cozmo/jsQR), but I don't
want to play with this if it means to use libraries and the browser support for
Shape Detection API is still poor. Similarly, I don't want to bother with this
if I can't use Firefox to explore it, so I'll wait for Firefox to implement the
`BarcodeDetection` API and use that once it is available.
