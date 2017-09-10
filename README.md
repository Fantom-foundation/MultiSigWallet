Ethereum Multisignature Wallet
===================

Allows multiple parties to agree on transactions before execution. Features a disaster recovery mode, where after a predefined period of inactivity any party will be able to spend from the wallet.

Based off (gnosis/MultiSigWallet)[https://github.com/gnosis/MultiSigWallet]. This smart contract features the following key differences:

* Changing of owners is not allowed, in order to minimise the attack surface.
* Time-activated disaster recovery mode / dead man's switch
* Only owners can execute transactions - fixes certain replay attacks reported with the base contract

Install
-------------
```
git clone https://github.com/danny-wu/MultiSigWallet.git
cd MultiSigWallet
vagrant up
```

Deploy
-------------

### Deploy multisig wallet:

1. Change `contracts/deploy/MultiSig.json` with the addresses of the owners, the quroum reqired for transactions to be executed, and the inactivity time in seconds. 86400 seconds = 1 day.

2. If you don't have a local ethereum node running, sign up for an API key with http://infura.io/

3. Deposit at least 0.1 ETH into a new Ethereum address, which will be used to create the contract. This address doesn't have to be an owner.

4. In the vagrant box (`vagrant ssh`), execute the following:

```
cd /vagrant/contracts/
python deploy.py -f deploy/MultiSig.json -protocol https -host mainnet.infura.io/<YOUR_INFURA_API_KEY> -port 80 -private_key <PRIVATE_KEY_OF_CONTRACT_CREATOR>
```

5. You should see the contract address in the output.

Test
-------------
### Run single test:
```
cd /vagrant/contracts/
python -m unittest tests.test_multisig_wallet
```
### Run all tests:
```
cd /vagrant/contracts/
python -m unittest discover tests
```

Limitations
-------------
This implementation does not allow the creation of smart contracts via multisignature transactions.
Transactions to address 0 cannot be done. Any other transaction can be done.

Security
-------------
All contracts are WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Reviewers
-------------
The following people have reviewed the code at the time of the linked commit:
- Stefan George ([Georgi87](https://github.com/Georgi87)): [b9405cc30de4615e325b1d46c71cdef670bdeadc](https://github.com/ConsenSys/MultiSigWallet/tree/b9405cc30de4615e325b1d46c71cdef670bdeadc)

License
-------------
[GPL v3](https://www.gnu.org/licenses/gpl-3.0.txt)
