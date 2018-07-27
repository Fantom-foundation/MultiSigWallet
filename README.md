Ethereum Multisignature Wallet
===================

Allows multiple parties to agree on transactions before execution. Features a disaster recovery mode, where after a predefined period of inactivity the number of key holders to sign a transaction is reduced by one each round.

Based off [danny-wu/MultiSigWallet](https://github.com/danny-wu/MultiSigWallet).

Limitations
-------------
This implementation does not allow the creation of smart contracts via multisignature transactions.
Adding additional owners (or changing owners) are not allowed.


Security
-------------
All contracts are WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


License
-------------
[GPL v3](https://www.gnu.org/licenses/gpl-3.0.txt)
