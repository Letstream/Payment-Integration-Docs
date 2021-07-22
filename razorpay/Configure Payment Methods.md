# Configure Payment Methods

These docs refer to Standard Checkout Process of RazorPay using Javascript Integration

Ref: https://razorpay.com/docs/payment-gateway/web-integration/standard/configure-payment-methods/

### Customise what payment methods are visible to User

The parameters below needs to be passed to the Config during Razorpay initialization i.e.

``` 
let config = {
  "key": 12345,
  "amount": 400 * 100, # RZP accepts it in Paisa
  "currency": "INR",
  "order_id": "rzp_hujsdasa"
  "prefill": {
      "name": "XYZ,
      "contact": "+919521379346"
      "email": "support@theletstream.com"
  },
  "readonly": { 'email': True, 'contact': True },
  "theme": {
    "color": "#000"
  },
  "handler": function(response){
    console.log("Payment Success", response)
},
"modal": {
    "ondismiss": function(){
        console.log('Checkout form closed');
    }
},
"config": {
  // Pass parameters here
}

let rzp = new window.Razorpay(config)
```


#### Show only Netbanking
```
{ 
    "display": {
        "block": {
            "highlighted": "banks"
        },
        "blocks": {
            "banks": {
                "name": "Pay via Net Banking",
                "instruments": [
                    {
                        "method": "netbanking",
                        // "banks": ["HDFC", "ICIC"]
                    }
                ]
            }
        },
        "sequence": ["block.banks"],
        "preferences": {
            "show_default_blocks": false
        }
    }
}
```
To allow only certain banks, refer to https://razorpay.com/docs/payment-gateway/web-integration/standard/configure-payment-methods/#supported-banks, and pass bank codes in "banks" key.


#### Show only UPI
```
{ 
    "display": {
        "block": {
            "highlighted": "banks"
        },
        "blocks": {
            "banks": {
                "name": "Pay via UPI",
                "instruments": [
                    {
                        "method": "upi",
                        // flows: [ "qr"],
                        // apps: ["google_pay", "phonepe"]
                    }
                ]
            }
        },
        "sequence": ["block.banks"],
        "preferences": {
            "show_default_blocks": false
        }
    }
}
```
To allow only certain flows, refer to https://razorpay.com/docs/payment-gateway/web-integration/standard/configure-payment-methods/#supported-upi-flows, and pass flow codes in "flows" key.
To allow only certain apps, refer to https://razorpay.com/docs/payment-gateway/web-integration/standard/configure-payment-methods/#supported-upi-apps, and pass app codes in "apps" key.

### Show only Wallets
```
{ 
    "display": {
        "block": {
            "highlighted": "banks"
        },
        "blocks": {
            "banks": {
                "name": "Pay via Wallets",
                "instruments": [
                    {
                        "method": "wallet",
                        // "wallets": ["olamoney", "freecharge"]
                    }
                ]
            }
        },
        "sequence": ["block.banks"],
        "preferences": {
            "show_default_blocks": false
        }
    }
}
```
To allow only certain wallets, refer to https://razorpay.com/docs/payment-gateway/web-integration/standard/configure-payment-methods/#supported-wallets, and pass wallet coodes in "wallets" key.

#### Show Only Debit Cards

```
{ 
    "display": {
        "block": {
            "highlighted": "banks"
        },
        "blocks": {
            "banks": {
                "name": "Pay via Debit Cards",
                "instruments": [
                    {
                        "method": "card",
                        "types": ["debit"],
                        //"issuers": ["UTIB"],
                        //"networks": ["MasterCard"],
                    }
                ]
            }
        },
        "sequence": ["block.banks"],
        "preferences": {
            "show_default_blocks": false
        }
    }
}
```
To allow only certain issuers, refer to https://razorpay.com/docs/payment-gateway/web-integration/standard/configure-payment-methods/#supported-banks, and pass bank coodes in "issuers" key.
To allow only certain cart types such as Visa or Master, refer to https://razorpay.com/docs/payment-gateway/web-integration/standard/configure-payment-methods/#supported-card-networks, and pass network codes in "networks" key.

#### Show Only Credit Cards

```
{ 
    "display": {
        "block": {
            "highlighted": "banks"
        },
        "blocks": {
            "banks": {
                "name": "Pay via Credit Cards",
                "instruments": [
                    {
                        "method": "card",
                        "types": ["credit"],
                        //"issuers": ["UTIB"],
                        //"networks": ["MasterCard"],
                    }
                ]
            }
        },
        "sequence": ["block.banks"],
        "preferences": {
            "show_default_blocks": false
        }
    }
}
```
To allow only certain issuers, refer to https://razorpay.com/docs/payment-gateway/web-integration/standard/configure-payment-methods/#supported-banks, and pass bank coodes in "issuers" key.
To allow only certain cart types such as Visa or Master, refer to https://razorpay.com/docs/payment-gateway/web-integration/standard/configure-payment-methods/#supported-card-networks, and pass network codes in "networks" key.

