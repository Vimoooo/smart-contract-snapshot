import os
from web3 import Web3

RPC_URL = os.getenv("RPC_URL", "https://eth.llamarpc.com")
CONTRACT_ADDRESS = os.getenv("CONTRACT_ADDRESS")

w3 = Web3(Web3.HTTPProvider(RPC_URL))

if not w3.is_connected():
    raise ConnectionError("Unable to connect to RPC.")

if not :
    raise ValueError("Set CONTRACT_ADDRESS first.")

contract = Web3.to_checksum_address(CONTRACT_ADDRESS)

balance = w3.eth.get_balance(contract)
code = w3.eth.get_code(contract)
nonce = w3.eth.get_transaction_count(contract)

print("=" * 55)
print("SMART CONTRACT SNAPSHOT")
print("=" * 55)
print(f"Address:        {contract}")
print(f"Network ID:     {w3.eth.chain_id}")
print(f"Block:          {w3.eth.block_number}")
print(f"ETH Balance:    {w3.from_wei(balance, 'ether'):.8f} ETH")
print(f"Nonce:          {nonce}")
print(f"Bytecode Size:  {len(code)} bytes")
print(f"Is Contract:    {'YES' if code else 'NO'}")
print("=" * 55)

if code:
    print("\nContract bytecode detected.")
    print("This address has deployed EVM code.")
else:
    print("\nNo deployed bytecode found.")
