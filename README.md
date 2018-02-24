# linux-nodevfee-for-v11.0

This software changes devFee wallet to your wallet in Claymore Miner.

How to use?
It works like a transaprent proxy.
You need 2 unusable ports.

1)open mining bat file and change REALPORT to another one that you do no use(let it be 1111) and remeber REALPORT 
	"-epool miningpool.com:REALPORT " -> "-epool miningpool.com:1111"

2)apply redirect command in the terminal "sudo iptables -t nat -A OUTPUT -p tcp --dport 1111 -j REDIRECT --to 1112"

3)go to nofee folder

4)add executable rule in the terminal "chmod +x nofee"

5)run it "./nofee 1112 REALPORT wallet.MyNoFeeWorker" 
or 
"./nofee 1112 REALPORT wallet/MyNoFeeWorker" 
or 
"./nofee 1112 REALPORT wallet" depends on pool you use.


example ethermine "./nofee 1112 4444 123456789012345678901234567890123456789012.MyNoFeeWorker" 

example nanopool "./nofee 1112 9999 123456789012345678901234567890123456789012/MyNoFeeWorker"




General:
 ( Claymore Miner )   --->------+
                                |
                          < local port >
                                |
                         [ nofee engine ]
                                |
                                +-------------> ( minig pool)
Example of ethermine.org

 ( Claymore Miner -epool eu1.ethermine.org:1111 ) --->--+
						        |
				< redirect to local port 1112 IPTABLES rule >
							|
				 [ nofee listening 1112 and redirect to 4444 ]
							|
							+-------> (connection eu1.ethermine.org:4444)
