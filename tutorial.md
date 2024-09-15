Save the Account in the Database
==============================


In this activity, you will learn to store the account address in Firebase, fetch the account addresses from Firebase, and display them on the web page.


<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10761273/PCP_gif.gif" width = "480" height = "320">


Follow the given steps to complete this activity.




1. Add an address to the database




* Open the file `wallet.py`.


* Call the `addToDB()` method to add the account address and the private key to the database.
~~~python
self.addToDB(self.address, self.privateKey)
~~~   
* Define the `addToDB` method that takes the account address and private key.
~~~python
def addToDB(self, address, privateKey):
~~~
* Create a reference for the node "adminAccount/" in the database.
~~~python
ref = db.reference("adminAccount/")
~~~
* Set the data at the reference location to a dictionary value of address and privateKey.
~~~python
ref.set({
"address" : address,
"privateKey" :privateKey
})
~~~   


2. Retrieve the accounts


* Open the file `app.py`.


*  Create a reference to the "adminAccount/" path in the database.
~~~python
ref = db.reference('adminAccount/')
~~~
* Store the data retrieved from the database using the reference in a variable.
~~~python
   accounts = ref.get()
~~~    
      
* Create an account, only if the account does not exist.
Move the account creation code to if part.
~~~python
if(not account):
account = Account()
~~~


*  Set the balance from the database if the data type of the account is a dictionary. As the account set from the list of accounts is in the form of a dictionary and while creating an account address is an object.
~~~python
if(type(account) == dict):
balance = myWallet.getBalance(account['address'])
~~~


*  Move the code to get the balance of an account when a new account address is created (which is already in the boilerplate) to the `else` part. 
~~~python
balance = myWallet.getBalance(account.address)
~~~


* Save and run the code to check the output.