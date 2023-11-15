# Offering
A resource trading solution.


I have been designing this for months in my head, but this is my current workspace for defining my ideas that I'll be implementing:

Offering - is a tool for consumers to understand the value of the used objects around them.  Offering is not a marketplace. Offering is not a cryptocurrency. Offering has no value other than to process user data.
It is my separate mission to complete offering with a focus on securing user data and allowing users the freedom to do local business in their own manner.
I understand that there are inherent risks and will take responsibility to shut down offering in the case that I find it is being used for illicit or malicious intent.

Inventory (TBD) is a system that connects to offering that can fetch estimated values of objects that users own. An inventory is just a collection of NFTs. A wallet is an example of an inventory, but seeing as I want to show off to employers, I will be creating my own inventory/wallet as well.
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

[ Inventory ] has objects we'l group them all as NFTs to start because its an easy concept to grasp that a wallet has NFTs that can be traded and users know nfts can be either digital or a representation of a real object.




