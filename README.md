# Signing Overview

This is my own first exploration into stand alone document signing, a pillar of blockchain technology and an amazing technology in it's own right.

This repo is simply a document that gives some example code you can run right in the browser to both sign and verify a signed document.

The key concept here is that only a particular individual can sign, because they alone hold the private key, but that any one else can verify the signature, using the public key.  In this example we are going to use the power of Metamask - it is both a wallet plugin that holds your private key on your behalf, and (at the time of writing this) also injects the `web3` library which gives access to the Ethereum blockchain and also gives us the ability to sign which we want for this exercise.


#### Ensure you have a Metamask enabled browser (install the plugin) 

[https://metamask.io/](https://metamask.io/)

#### Open up your browser console window now

On a Mac : `Command+Option+j`

#### Signing a message

Enter this code into your console  window

```
// We need to encode the sting to Hex to do the signing 
function toHex(s) {
    // utf8 to latin1
    var s = unescape(encodeURIComponent(s))
    var h = ''
    for (var i = 0; i < s.length; i++) {
        h += s.charCodeAt(i).toString(16)
    }
    return h
}
function fromHex(h) {
    var s = ''
    for (var i = 0; i < h.length; i+=2) {
        s += String.fromCharCode(parseInt(h.substr(i, 2), 16))
    }
    return decodeURIComponent(escape(s))
}
```
And then this code   

```
var msg = "Here is my test message to sign !"
var hex_msg = "0x"+toHex(msg)
web3.personal.sign( 
   hex_msg ,  
   web3.eth.coinbase , 
   (err, res) => { 
        console.log( 'Errors :', err, 'Signed message :', res) 
   } 
)

```

Once you run that, Metamask should pop up confirming the signature of this message.  
In the console it will return the hash which is that signed message.

#### Verify the signature of a signed message

... TODO ...

This will likely help : https://ethereum.stackexchange.com/a/2866/19779.   
But currently will not work in-browser.



## Going further

This was just so awesome and I stumbled across it while doing the above, so I'm including this link here :      
[https://programtheblockchain.com/posts/2018/02/17/signing-and-verifying-messages-in-ethereum/](https://programtheblockchain.com/posts/2018/02/17/signing-and-verifying-messages-in-ethereum/)


