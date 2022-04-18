from hashlib import sha256
MAX_NONCE = 100000000000

def SHA256(text):
    return sha256(text.encode("ascii")). hexdigest()

def mine(block_number, transactions, prefix_hase, prefix_zeros): 
    prefix_str = '0'*prefiz_zeros
    for nonce in range (MAX_NONCE):
        text = str(block_number) + transaction + previous_hash + str(nonce)
        new_hash = SHA256(text)
        if new_hash.stratswith(prefix_str):
        print(f"Yay! Successfully mined bitdollars with nonce value:{nonce}")
        return new_hash 

    raise BaseException(f"Couldn't find correct has after trying {MAX_NONCE} times")

if __name__=='__main__':
    transactions='''
    David->Bastin->20,
    Marrie->Caroline->45
    '''
    difficulty=4 # try changing this to higher number and you will see it will take more time for mining as difficulty increases
    import time
    start = time.time()
    print("start mining")
    new_hash =
mine(5,transaction,'0000000xa036944e29568d0cff17edbe038f81208fecf9a66be9a2b8321c6ec7',difficulty)
    total_time = str((time.time() - start))
    print(f"end mining. mining took: {total_time}  second")
    print(new_hash )from datetime import datetime
from hashlib import sha256

class Block:
    def __init__(self,transactions,previous_hash,nonce=0):
        self.timestamp=datetime.now()
        self.transactions=transactions
        self.nonce=nonce
        self.previous_hash=previous_hash
        self.hash=self.generate_hash()
#print block contents
    def print_block(self):
        print("Timestamp:",self.timestamp)
        print("Transactions:",self.transactions)
        print("Currenthash:",self.generate_hash ())
        print("Previoushash:",self.previous_hash)
#generate hash        
        
    def generate_hash(self):
        block_contents=str(self.timestamp)+str(self.transactions)+str(self.nonce)+str(self.previous_hash)
        block_hash=sha256(block_contents.encode())
        return block_hash.hexdigest()
#Block chain class

class Blockchain:
    def __init__(self):
        self.chain=[]
        self.all_transactions=[]
        self.genesis_block()
#genesis block
    def genesis_block(self):
        transactions={}
        genesis_block=Block(transactions,'0')
        self.chain.append(genesis_block)
        return self.chain
 #print block contents in chain       
        
    def print_blocks(self):
        for i in range(len(self.chain)):
            current_block=self.chain[i]
            print("Block{}{}".format(i,current_block))
            current_block.print_block()
#adding block to chain
            
    def add_block(self,transactions):
        previous_block_hash = self.chain[len(self.chain)-1].hash
        new_block=Block(transactions,previous_block_hash)
        proof=self.proof_of_work(new_block)
        self.chain.append(new_block)
    
        return proof,self.chain
        
    def validate_chain(self):
        for i in range(1,len(self.chain)):
            current=self.chain[i]
            previous=self.chain[i-1]
            if(current.hash!=current.generate_hash()):
                print("Current block:{} hash:{} is not equal to current generated hash:{} in current block".format (i,current .hash,current .generate_hash ()))
                return False
            if(current.previous_hash!=previous.generate_hash()):
                print("previous block:{} hash value:{} doesnt equal to previous hash value:{} stored in current block:{}".format (i-1,previous .generate_hash (),current  .previous_hash ,i))
                return False
        return True   
        
         
    def proof_of_work(self,block,difficulty=2):
        #block.nonce=0
        proof=block.generate_hash()
        while proof[:difficulty]!='0'*difficulty:
            
            block.nonce +=1
            proof=block.generate_hash()
            #block.nonce+=1
        block.nonce =0
        return proof    
            
            
block_one_transactions = {"sender":"A", "receiver": "B", "amount":"50"}
block_two_transactions = {"sender": "C", "receiver":"D", "amount":"25"}
block_three_transactions = {"sender":"E", "receiver":"F", "amount":"35"}
fake_transactions = {"sender": "G", "receiver":"H", "amount":"25"}
local_blockchain=Blockchain()

local_blockchain.add_block(block_one_transactions)
local_blockchain.add_block(block_two_transactions)
local_blockchain.add_block(block_three_transactions)
#print (local_blockchain .chain [2].previous_hash )
#print(local_blockchain .chain[1].hash)
local_blockchain .chain [1].transactions =fake_transactions

local_blockchain.validate_chain()
#local_blockchain.chain [0].print_block ()
#print ("Block {}{}".format (1,local_blockchain  .chain [1]))
#local_blockchain .chain [1].print_block ()
local_blockchain .print_blocks ()
