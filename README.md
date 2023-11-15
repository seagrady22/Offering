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
1: What item is desired? -The whole point is that an item is wanted so first the user will select an item (or multiple)
2: Return a best guess of value! Offering gives a best guess to evaluate or appraise an object in some currency based on real world data
  -but remember, this doesn't matter and is highly speculative. Value is held by the owner of the object. Offering makes no attempt to exchange the objects, this is outside of the realm of a simple tool helping users make offerings to understand the value of their objects
3: ( Future TBD maybe not even ) Propose a smart contract to the user that provides both users a trade they want.

Couple of comments before we get out of hand with features:
NO CHAT: items need to be clearly depicted in images with their state and condition
The state and conditions need to be baked into the smart contracts i.e. held in json next to the item. No clear explanation of whats going on? no deal. More chat gives way to more scams. Less chat forces users to clearly spell out functionality. if we support PNG and mp4 there should be no need for any chat services to ask questions. If a user asks questions, that information needs to stay with the object/NFT. These things can grow over time to help our NN's further evaluate the price of an object.

So now we have inventory systems that are interacting with a price evaluator that will generate a stubbed offering i.e. probably just a json object that defines a smart contract. Users can not define their own smart contracts because they could have bugs. We will take on that work for the user by giving them an initial stub based on the information provided. We should also make some attempt to call out important missing information and i imagine there are several ways of doing this. 







