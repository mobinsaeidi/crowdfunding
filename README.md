Crowdfunding Smart Contract
Hey, welcome! This is my little crowdfunding project built on Ethereum using Solidity. It’s a simple, fun way to raise funds on the blockchain—think of it like a digital tip jar with some cool rules. Anyone can chip in, and depending on how it goes, the creator either gets the cash or contributors get their money back. Let’s dive in!

What’s It All About?
Solidity Version: ^0.8.25
License: MIT (free to use and tweak!)
Date: March 04, 2025
Cool Features
Start a Campaign: Set a funding goal (in wei) and how long it’ll run.
Pitch In: Send some Ether to help out—if you’re feeling generous!
Cash Out: If the goal’s hit, the creator can grab the funds.
Money Back: Didn’t make it? No stress—contributors can get a refund.
Events: Little notifications for when stuff happens (like new contributions or withdrawals).
What You’ll Need
To play around with this, here’s what you’ll want:

Node.js and npm (the basics!)
Truffle or Hardhat to compile and deploy
Metamask to connect and interact
A test network like Ropsten, Rinkeby, or Ganache (mainnet’s for the brave!)
Getting Started
Clone this repo to your machine:
bash

Collapse

Wrap

Copy
git clone https://github.com/[your-username]/[repo-name].git
cd [repo-name]
Install the goodies (if you’re using Truffle or Hardhat):
bash

Collapse

Wrap

Copy
npm install
Compile the contract:
With Truffle:
bash

Collapse

Wrap

Copy
truffle compile
With Hardhat:
bash

Collapse

Wrap

Copy
npx hardhat compile
Deploy it to your favorite network:
Truffle:
bash

Collapse

Wrap

Copy
truffle migrate --network [network-name]
Hardhat:
bash

Collapse

Wrap

Copy
npx hardhat run scripts/deploy.js --network [network-name]
How to Use It
1. Kick Off a Campaign
The creator sets a goal and how long it’ll run. Something like:

solidity

Collapse

Wrap

Copy
Crowdfunding campaign = new Crowdfunding(1000000000000000000, 604800); // 1 Ether, 7 days
2. Chip In
Anyone can contribute by calling contribute() with some Ether:

javascript

Collapse

Wrap

Copy
await campaign.contribute({ value: web3.utils.toWei("0.1", "ether") });
3. Grab the Funds
If the goal’s met, the creator can cash out with withdrawFunds():

javascript

Collapse

Wrap

Copy
await campaign.withdrawFunds();
4. Get a Refund
If time’s up and the goal’s not reached, call refund() to get your Ether back:

javascript

Collapse

Wrap

Copy
await campaign.refund();
What’s Inside?
Variables:
creator: Who started this party
goal: How much we’re aiming for (in wei)
totalRaised: What we’ve collected so far
deadline: When the clock runs out
contributions: Tracks everyone’s donations
Functions:
contribute(): Toss in some Ether
withdrawFunds(): Creator grabs the loot (if goal’s met)
refund(): Get your money back if it doesn’t work out
Events:
CampaignCreated: “Hey, we’ve got a new campaign!”
ContributionReceived: “Thanks for the support!”
FundsWithdrawn: “Creator’s cashing out!”
RefundIssued: “Here’s your refund!”
Safety Notes
I’ve tried to keep it safe from sneaky stuff like Reentrancy attacks.
There are checks to stop things like contributing after the deadline.
Still, test it out with tools like MythX or Slither before going big on mainnet!
Limits
One campaign per contract—no multi-tasking here.
No “cancel” button for the creator (yet!).
Wanna Help Out?
Got ideas? Found a bug? I’d love your input! Feel free to open a Pull Request or an Issue—let’s make it better together.

License
This is all under the MIT License—go wild with it!
