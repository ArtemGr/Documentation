**************
tokencancelbid
**************

To cancel any bid/buy order that you created
============================================

All you need is the specific ``tokenid`` & ``bidtxid`` which can be found on the order.

Usage: 
------

``tokencancelbid tokenid bidtxid``

Step 1: Issue the call and get your raw transaction HEX value
=============================================================

Example Command:
----------------

.. code-block:: shell

	./komodo-cli -ac_name=ATEST tokencancelbid 9217014eae0a83a0b64632f379c1b474859794f9eaf1cf1eecf5804ed6124a5e 7194ae293330af80fdbe4b4b2c8b51194f12e334b4a0489288288c1b7336a65c

Output:
-------

.. code-block:: json

    {
        "result": "success",
        "hex": "010000000234c335a46dadea8e42420b0e284f5577cfbcb7764a8d5c3b61312b71c5b14d0800000000494830450221009f365d429d03df66b34cad764368092498ebd7340587c558ea19c4248202317b0220531524ef076f9e5b26ec5aa38b3078c041f8d0603b85552177ef14d00b0e499601ffffffff5ca636731b8c28889248a0b434e3124f19518b2c4b4bbefd80af303329ae9471000000007b4c79a276a072a26ba067a565802102adf84e0e075cf90868bd4e3d34a03420e034719649c41f371fc70d8e33aa2702814066f6a9d580da0ac901ada8c61922d93da005e92c9e419a44c1bcbf9ec8ad43790dfc8ca71b5c21b79a58aa173fb71e1ab0b82c590dc883359de60f743fabda16a100af038001e3a10001ffffffff030a00000000000000302ea22c8020bc485b86ffd067abe520c078b74961f6b25e4efca6388c6bfd599ca3f53d8dae8103120c008203000401ccf078724e18090000232103fe754763c176e1339a3f62ee6b9484720e17ee4646b65a119e9f6370c7004abcac0000000000000000246a22e3789217014eae0a83a0b64632f379c1b474859794f9eaf1cf1eecf5804ed6124a5e00000000"
    }

Step 2: Send raw transaction / broadcast the HEX value from above
=================================================================

Example Command:
----------------

.. code-block:: shell

	./komodo-cli -ac_name=ATEST sendrawtransaction 010000000234c335a46dadea8e42420b0e284f5577cfbcb7764a8d5c3b61312b71c5b14d0800000000494830450221009f365d429d03df66b34cad764368092498ebd7340587c558ea19c4248202317b0220531524ef076f9e5b26ec5aa38b3078c041f8d0603b85552177ef14d00b0e499601ffffffff5ca636731b8c28889248a0b434e3124f19518b2c4b4bbefd80af303329ae9471000000007b4c79a276a072a26ba067a565802102adf84e0e075cf90868bd4e3d34a03420e034719649c41f371fc70d8e33aa2702814066f6a9d580da0ac901ada8c61922d93da005e92c9e419a44c1bcbf9ec8ad43790dfc8ca71b5c21b79a58aa173fb71e1ab0b82c590dc883359de60f743fabda16a100af038001e3a10001ffffffff030a00000000000000302ea22c8020bc485b86ffd067abe520c078b74961f6b25e4efca6388c6bfd599ca3f53d8dae8103120c008203000401ccf078724e18090000232103fe754763c176e1339a3f62ee6b9484720e17ee4646b65a119e9f6370c7004abcac0000000000000000246a22e3789217014eae0a83a0b64632f379c1b474859794f9eaf1cf1eecf5804ed6124a5e00000000

Output:
-------

::

	AssetValidate (x)
	vin1 10, vout0 10, AssetValidateBuyvin
	Got 0.00000010 to origaddr.(RANyPgfZZLhSjQB9jrzztSw66zMMYDZuxQ)
	21d152480275568e3f82a5049d8b30308e3739ebd98171e075a75fea504364cd

Step 3: Decode the raw transaction (optional to check if the values are sane)
=============================================================================

Example Command:
----------------

.. code-block:: shell

	./komodo-cli -ac_name=ATEST decoderawtransaction 010000000234c335a46dadea8e42420b0e284f5577cfbcb7764a8d5c3b61312b71c5b14d0800000000494830450221009f365d429d03df66b34cad764368092498ebd7340587c558ea19c4248202317b0220531524ef076f9e5b26ec5aa38b3078c041f8d0603b85552177ef14d00b0e499601ffffffff5ca636731b8c28889248a0b434e3124f19518b2c4b4bbefd80af303329ae9471000000007b4c79a276a072a26ba067a565802102adf84e0e075cf90868bd4e3d34a03420e034719649c41f371fc70d8e33aa2702814066f6a9d580da0ac901ada8c61922d93da005e92c9e419a44c1bcbf9ec8ad43790dfc8ca71b5c21b79a58aa173fb71e1ab0b82c590dc883359de60f743fabda16a100af038001e3a10001ffffffff030a00000000000000302ea22c8020bc485b86ffd067abe520c078b74961f6b25e4efca6388c6bfd599ca3f53d8dae8103120c008203000401ccf078724e18090000232103fe754763c176e1339a3f62ee6b9484720e17ee4646b65a119e9f6370c7004abcac0000000000000000246a22e3789217014eae0a83a0b64632f379c1b474859794f9eaf1cf1eecf5804ed6124a5e00000000

Output:
-------

.. code-block:: json

    {
        "txid": "21d152480275568e3f82a5049d8b30308e3739ebd98171e075a75fea504364cd",
        "size": 434,
        "version": 1,
        "locktime": 0,
        "vin": [
            {
                "txid": "084db1c5712b31613b5c8d4a76b7bccf77554f280e0b42428eeaad6da435c334",
                "vout": 0,
                "scriptSig": {
                    "asm": "30450221009f365d429d03df66b34cad764368092498ebd7340587c558ea19c4248202317b0220531524ef076f9e5b26ec5aa38b3078c041f8d0603b85552177ef14d00b0e499601",
                    "hex": "4830450221009f365d429d03df66b34cad764368092498ebd7340587c558ea19c4248202317b0220531524ef076f9e5b26ec5aa38b3078c041f8d0603b85552177ef14d00b0e499601"
                },
                "sequence": 4294967295
            },
            {
                "txid": "7194ae293330af80fdbe4b4b2c8b51194f12e334b4a0489288288c1b7336a65c",
                "vout": 0,
                "scriptSig": {
                    "asm": "a276a072a26ba067a565802102adf84e0e075cf90868bd4e3d34a03420e034719649c41f371fc70d8e33aa2702814066f6a9d580da0ac901ada8c61922d93da005e92c9e419a44c1bcbf9ec8ad43790dfc8ca71b5c21b79a58aa173fb71e1ab0b82c590dc883359de60f743fabda16a100af038001e3a10001",
                    "hex": "4c79a276a072a26ba067a565802102adf84e0e075cf90868bd4e3d34a03420e034719649c41f371fc70d8e33aa2702814066f6a9d580da0ac901ada8c61922d93da005e92c9e419a44c1bcbf9ec8ad43790dfc8ca71b5c21b79a58aa173fb71e1ab0b82c590dc883359de60f743fabda16a100af038001e3a10001"
                },
                "sequence": 4294967295
            }
        ],
        "vout": [
            {
                "value": 0.00000010,
                "valueSat": 10,
                "n": 0,
                "scriptPubKey": {
                    "asm": "a22c8020bc485b86ffd067abe520c078b74961f6b25e4efca6388c6bfd599ca3f53d8dae8103120c008203000401 OP_CHECKCRYPTOCONDITION",
                    "hex": "2ea22c8020bc485b86ffd067abe520c078b74961f6b25e4efca6388c6bfd599ca3f53d8dae8103120c008203000401cc",
                    "reqSigs": 1,
                    "type": "cryptocondition",
                    "addresses": [
                        "RRPpWbVdxcxmhx4xnWnVZFDfGc9p1177ti"
                    ]
                }
            },
            {
                "value": 99999.99990000,
                "valueSat": 9999999990000,
                "n": 1,
                "scriptPubKey": {
                    "asm": "03fe754763c176e1339a3f62ee6b9484720e17ee4646b65a119e9f6370c7004abc OP_CHECKSIG",
                    "hex": "2103fe754763c176e1339a3f62ee6b9484720e17ee4646b65a119e9f6370c7004abcac",
                    "reqSigs": 1,
                    "type": "pubkey",
                    "addresses": [
                        "RANyPgfZZLhSjQB9jrzztSw66zMMYDZuxQ"
                    ]
                }
            },
            {
                "value": 0.00000000,
                "valueSat": 0,
                "n": 2,
                "scriptPubKey": {
                    "asm": "OP_RETURN e3789217014eae0a83a0b64632f379c1b474859794f9eaf1cf1eecf5804ed6124a5e",
                    "hex": "6a22e3789217014eae0a83a0b64632f379c1b474859794f9eaf1cf1eecf5804ed6124a5e",
                    "type": "nulldata"
                }
            }
        ]
    }

