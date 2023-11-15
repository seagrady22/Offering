# Offering

A resource evaluation solution. In other words, an offering solution. It means exactly what it says. When some entity wants a resource from another entity, it must evaluate that resource with respect to its own resources. In some cases, two parties might be able to reach a consensus and trade resources only in terms of other resources, not using any money. I played a lot of mmorpgs growing up and so this project represents the wide range of knowledge I have gained from both the digital and real world trading and doing business. Without further adue:

Offering - is a tool for consumers to understand the value of objects around them.  Offering is not a marketplace. Offering is not a cryptocurrency. Offering has no value other than to process user data and help users generate and execute safe smart contracts.

It is my mission to complete offering with a focus on not storing user data and allowing users the freedom to do local business in their own manner.  Storing data allows for data to be mined. Offering in certain cases will need to transmit data, which it will using appropriate TLS, JWT and other security features. Again, in no case will offering store user data. In many cases, offering may use transmitted data to train its internal models, but I make the distinction that this is not really storing user data and welcome discussion around this topic. The models used in offering will be securely stored however even in some case someone wanted to rent the model, sharing the model does not share the underlying user data. Underlying data will be destroyed when data is not being used and in NO CIRCUMSTANCE will user data ever be sold to third parties.

Offering Inventory (OI - TBD) is a system that connects to offering that stores currency and smart contracts for the owner of the inventory. A wallet is an example of an inventory. I will be creating my own inventory/wallet as well that allows users to publish items for sale to anyone that wants to view their inventory. Additionally offering will be able to browse all of these inventories in a given local area similar to services like offerup craigslist fbmarketplace that I will be scraping.

An inventory implies an owner of said inventory. For the time being I want to consider the inventories only. When we send money or goods to another wallet, the concept of a user is really adding information that is unecessary and my goal is to store little to no information. 

Escrow (TBD) - is a system by which users can leverage smart contracts in their inventory to make an offering to another inventory. For example, if I have a smart contract that pays me 30 tezos 10 days in the future, I can actually use that future as a source of currency rather than having to wait 10 days for the acount to be paid out (as long as the smart contract is valid).
Smart contracts allow us to be able to manage money in an elegant way.

Scrapers - To begin my work, I want to focus on pulling data from offerUp. I love that the name is so close to offering and it has helped me grasp the concept of what offering truly is or could be.
That being said, offerup can and will be replaced with (m)any service provider that can query a location for product pictures and prices. It would be impossible to evaluate the price of an object based on a single source of data. Additionally the goal is to allow for each offering inventory to have a flag that allows it to be visible in a local area.

Use Cases/Architecture:

To begin, I want to collect a lot of information on objects available for purchase on offerup. I am only concerned with used objects for sale right now, but models later on are going to be able to show how items should be priced vs what they are being priced for.

The public information I am collecting will be used to create neural networks that can use both images and historical listing data to price objects. The NN should be able to accurately predict the price of an object for sale withing 80-90% confidence, though it really doesn't matter.

Once I am able to create a NN that can accurately predict an object's price based on real market data, I could theoretically allow that NN to price things to help buyers reach consensus when evaluating an offer. But at the end of the day, it really is up to the owners of the objects to decide what is best for them from within their own state/region/country. 

[ Inventory ] has objects, we'l group them all as NFTs to start because its an easy concept to grasp that a wallet has NFTs that can be traded and users know nfts can be either purely digital or some representation of a real object. The owner of an inventory dictates the price of an object. I will say this as many times as I have to so here it is again: The owner of an inventory dictates the price of its object. Pictures of your dog are priceless. Your mom's jewlery cannot be bought. Your time spent as a woodworker is as you price it, whether you are perceived as the best or the worst woodworker.

[ Offering ] - is a containerized database application whereby users can allow an evalautation of objects that are in their inventory whether real or digitial. Offering will be written using next gen tools like graphQL, an ORM, RUST aynsch io, more...  We will make a big distinction between real and digital objects. Offerings are going to be multi step interactions with a distrbuted db system. 

The main algorithm for offering is something like:

1: Provide the item desired to generate an offering (tbd could be multiple)

2: Offering returns a best guess of value.. i.e. Offering gives a best guess to evaluate or appraise an object in some currency based on real world data

  -Remember, this doesn't matter and is highly speculative. Value is held by the owner of the object. Offering makes no attempt to exchange the objects, this is outside of the realm of a simple tool helping users make offerings to understand the value of their objects
  
3: Offering then proposes a smart contract in the form of a stubbed json object to the user that provides both users a trade they want. So we give the user data in the form of json that they will continue to fill out.

4: Offering executes the smart contract on behalf of the wallets, exchanging the goods and growing a number of research models. The users in good faith can repeat the steps if something fails and trade the goods back. Users need to be very cautious when attaching any kind of digital currency to their smart contracts. We personally only recommend doing local business and doing cash trades for digital assets. This describes the transactions as best as possible for transparency/tax purposes and then leaves the users and their local governments to their business.

A user can decline because the trade is not clear enough, which keeps the deal open but continues to build out the smart contract in more detail. (missing field decline MFD)

A user can decline because the trade is not sufficient enough in value and purpose counter offers. (counter offering CO)

A user can decline for any reason they want. (NEHNEH)


[Example]
(1) Some inventory wants a piano from some other inventory (1)

(2) Offering gives an evaluation of 500$USD of the piano based on its current internal black box pricing model. 

(3) Offering returns a stub of a smart contract which can be filled out and sent to invetory offering 500$USD for the digital certification representing the piano. So here the user fills it out and offers it to the inventory with the piano.

(4a) The inventory owning the piano accepts the offering - The digital certificate is swapped in buyer/seller inventories and the money is sent to the seller in the form of smart contract. In this case, offering will record the transaction data privately and only by supplying it to its NN to help better evaluate and assist users. Again, no user data needs to be stored. Its just used to track and market to consumsers, and this is not a tool for those things, but rather a solution in the opposite direction.

(4b) The user declines the offering indicating a missing required field
(4c) The user declines the offering indicating a counter offering
(4d) The user declines the offering for any other reason for which we discontinue the transaction completely.

Couple of comments before we get out of hand with features:
NO CHAT: items need to be clearly depicted in images with their state and condition
The state and conditions need to be baked into the smart contracts i.e. held in json in the data section of the NFT. What if there is no clear explanation of whats going on? then no deal, thats on the owner. More chat gives way to more scams imo. Less chat forces users to clearly spell out current conditions and states of the objects being transferred. if we support PNG and mp4 there should be no need for any chat services becausre we should be able to render the quality of objects based on real recorded data. If a user asks questions, that information needs to stay with the object/NFT. These object notes can grow over time to help our NN's further evaluate the price of an object. 

So rather than a chat service, a feature I am demanding here is the "Required Field" feature whereby an offer can be declined pending "Required Field" which once filled out will continue on the current offering process. (see 4b).

So now we have inventory systems that are interacting with a containerized price evaluator that will generate a stubbed offering i.e.  just a json object that defines a smart contract. Users can not define their own smart contracts because they could have bugs. We will take on that work for the user by giving them an initial stub based on the information provided. We should also make some attempt to call out important missing information and i imagine there are several ways of doing this. 

Offering does not encourage users to pay via smart contracts. Offering instead encourages users to user smart contracts to help with their bookkeeping. Blockchain is really good at keeping information transparent and public and so we want to allow for humans to start getting more familiar with using smart contracts. As more tools come out and users feel safer executing their own smart contracts, maybe this will change. But in the meantime, offering is just a free tool to start helping evaluate the prices of their objects online. So there is tons of incentive for users to be honest and work together to show transparent transactions where it does not force them into paying more taxes. We again support local laws to govern business and take no stake in anyone that seeks to use this platform for illicit behavior.

Thus the final feature of offering is a generalized tool to display a list of transactions as csv at the end of the year for all smart contracts executed through offering. Things can get a little hairy when doing resource trading, but its really helpful when doing a lot of cash business to be able to keep a record of these sorts of trades and be able to declare them at the end of the tax year. As a seller of clothing, I find NFTs to be an extremely useful tool when combined with things like QR code tags. 








