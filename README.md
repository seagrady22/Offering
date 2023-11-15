# Offering
A resource evaluation solution that could be used for some greater resource trading implementation.


I have been designing this for months in my head, but this is my current workspace for defining my ideas that I'll be implementing:

Offering - is a tool for consumers to understand the value of the used objects around them.  Offering is not a marketplace. Offering is not a cryptocurrency. Offering has no value other than to process user data.
It is my separate mission to complete offering with a focus on securing user data and allowing users the freedom to do local business in their own manner.
I understand that there are inherent risks and will take responsibility to shut down offering in the case that I find it is being used for illicit or malicious intent.

Offering Inventory (TBD) is a system that connects to offering that can fetch estimated values of objects that users own. An inventory is just a collection of NFTs. A wallet is an example of a private inventory, but seeing as I want to show off to employers, I will be creating my own inventory/wallet as well that allows users to publish items that are for sale to anyone that wants to view their inventory.

An inventory implies an owner of said inventory. For the time being I want to consider the inventories only. When we send money or goods to another wallet, the concept of a user is really adding information that is unecessary.  While this information could be great to be used to do things like track user data, I find it unecessary for what I am building.

Escrow (TBD) - is a system by which users can leverage smart contracts in their inventory to make an offering to another inventory. For example, if I have a smart contract that pays me 30 tezos 10 days in the future, I can actually use that future as a source of currency rather than having to wait 10 days for the acount to be paid out. '
Smart contracts allow us to be able to manage money like this in an elegant way.

Scrapers - To begin my work, I want to focus on pulling data from offerUp. I love that the name is so close to offering and it has helped me grasp the concept of what offering truly is or could be.
That being said, offerup can and will be replaced with (m)any service provider that can query a location for product pictures and prices. It would be impossible to evaluate the price of an object based on a single source of data.

Architecture:

To begin, I want to collect a lot of information on objects available for purchase on offerup. I am only concerned with objects already owned by others i.e. P2P.  I am not accounting for vendors that are selling new objects, though this functionality could be added with ease.
The information I am collecting will be used to create neural networks that can use both images and historical listing data to price objects.

Once I am able to create a NN that can accurately predict an object's price based on real market data (within lets say 90% or so), I could theoretically allow that NN to price things to help buyers reach consensus when evaluating an offer.

To do this, I will have each of the components defined above architecture securely communicating with one and other. Communication will be done using rest to account for possible network speed or traffic that could back up request. There can be no expectations for any kind of low latency library that queries products. However wherever possible, data processing will be done with either C++ or preferably Rust.

[ Inventory ] has objects, we'l group them all as NFTs to start because its an easy concept to grasp that a wallet has NFTs that can be traded and users know nfts can be either digital or a representation of a real object. The owner of an inventory dictates the price of an object. I will say this as many times as I have to so here it is again: The owner of an inventory dictates the price of an object. Pictures of your dog are priceless. Your mom's jewlery cannot be bought. Your time spent as a woodworker is as you price it, whether you are perceived as the best or the worst. 

[ Offering ] - is a containerized application whereby users can allow an evalautation of objects that are in their inventory whether real or digitial. We will make a big distinction between real and digital objects. Transactions are going to be a multi part interaction with the containerized offering. The main algorithm for offering is as follows:
1: What item is desired? (the input to offering is an NFT(s)) -The whole point is that an item is wanted so first the user will select an item (or multiple)
2: Return a best guess of value! Offering gives a best guess to evaluate or appraise an object in some currency based on real world data
  -but remember, this doesn't matter and is highly speculative. Value is held by the owner of the object. Offering makes no attempt to exchange the objects, this is outside of the realm of a simple tool helping users make offerings to understand the value of their objects
3: Offering will now propose a smart contract in the form of a stubbed json object to the user that provides both users a trade they want. So we give the user data in the form of json that they will continue to fill out. 

[Example]
(1) Some inventory wants a piano from some other inventory (1)

(2) Offering gives back an evaluation of 500$USD of the piano based on its current internal black box pricing model. 

(3) The user is then given a stub of a smart contract that they are able to send to another user offering 500$USD for the digital certification representing the piano.

(4a) The user accepts the offering - The digital certificate is swapped in buyer/seller inventories and the money is sent to the seller in the form of smart contract. In this case, offering will record the transaction data privately and only by supplying it to its NN to help better evaluate and assist users. Again, no user data needs to be stored. Its just used to track and market to consumsers, and this is not a tool for those things, but rather a solution in the opposite direction.

(4b) The user declines the offering indicating a missing required field
(4c) The user declines the offering indicating a counter offering
(4d) The user declines the offering for any other reason for which we discontinue the transaction completely.

The smart contract can now be a live representation of the real trade happening from each inventory for the piano. Managing digital certificates of real objects will always be in the hands of the user. If we allow nft's to represent real objects, there is always room for scammers. But offering also gives tons of real value to folks doing honest business that just want to record their transactions while getting good real time information to evaluate their offerings. 

Couple of comments before we get out of hand with features:
NO CHAT: items need to be clearly depicted in images with their state and condition
The state and conditions need to be baked into the smart contracts i.e. held in json in the data section of the NFT. What if there is no clear explanation of whats going on? then no deal, thats on the owner. More chat gives way to more scams imo. Less chat forces users to clearly spell out current conditions and states of the objects being transferred. if we support PNG and mp4 there should be no need for any chat services becausre we should be able to render the quality of objects based on real recorded data. If a user asks questions, that information needs to stay with the object/NFT. These object notes can grow over time to help our NN's further evaluate the price of an object. 

So rather than a chat service, a feature I am demanding here is the "Required Field" feature whereby an offer can be declined pending "Required Field" which once filled out will continue on the current offering process. (see 4b).

So now we have inventory systems that are interacting with a containerized price evaluator that will generate a stubbed offering i.e. probably just a json object that defines a smart contract. Users can not define their own smart contracts because they could have bugs. We will take on that work for the user by giving them an initial stub based on the information provided. We should also make some attempt to call out important missing information and i imagine there are several ways of doing this. 

The use of offering is to help those doing honest business that want to keep digital certificates of their transactions. Thus the final feature of offering is a tool to help evaluate a users taxes at the end of the year. Things can get a little hairy when doing resource trading, but its really helpful when doing a lot of cash business to be able to keep a record of these sorts of trades and be able to declare them at the end of the tax year. And again, this is up to the user on whether they want to actually accept a digital smart contract. 








