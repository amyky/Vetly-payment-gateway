TalentVetting
This smart contract provides talent vetting subscription management. It allows companies to subscribe to vetting services provided by talents for a specified duration, either monthly or yearly.

License
This project is licensed under the terms of the MIT license. Please see the LICENSE file for more details.

Prerequisites
This project is written in Solidity programming language. It requires Solidity compiler to compile the contract code. The recommended version is 0.8.18.

This project also depends on the OpenZeppelin library. The necessary files are already imported in the contract.

Usage
Contract Initialization
To initialize the contract, two addresses should be passed to the constructor:

_owner: The address of the contract owner.
_appWallet: The address of the wallet to which the transaction fees will be transferred.
solidity
constructor(address payable _owner, address payable _appWallet)
Subscription Fees
The subscription fees can be set by calling the setOneTimeFee(), setMonthlyFee(), and setYearlyFee() functions. These functions can only be called by the contract owner.

solidity

function setOneTimeFee(uint256 _price) public;
function setMonthlyFee(uint256 _price) public;
function setYearlyFee(uint256 _price) public;
Subscription Management
One-Time Subscription
Companies can subscribe to a one-time vetting service by calling the subscribeOneTimeSubscription() function. The function requires the payment amount to be equal to the one-time subscription fee.

solidity

function subscribeOneTimeSubscription() public payable;
Monthly Subscription
Companies can subscribe to a monthly vetting service by calling the subscribeMonthly() function. The function requires the payment amount to be equal to the monthly subscription fee.

solidity
function subscribeMonthly() public payable;
Yearly Subscription
Companies can subscribe to a yearly vetting service by calling the subscribeYearly() function. The function requires the payment amount to be equal to the yearly subscription fee.

solidity
function subscribeYearly() public payable;
Remaining Vetting Count
Companies can check the remaining number of vetting services they have subscribed to by calling the getRemainingVettingCount() function.

solidity
function getRemainingVettingCount() public view returns (uint256);
Events
The contract emits the following events:

PaymentProcessed(address payer, uint256 amount): This event is emitted when a payment is successfully processed.
PaymentRefunded(address payer, uint256 amount): This event is emitted when a payment is refunded.
SubscribedAmount(address payer, uint256 amount, uint256 _amount): This event is emitted when a subscription is successfully processed.
SubscriptionCreated(uint256 subscriptionId, address subscriber, address talent, uint256 duration, uint256 amount): This event is emitted when a new subscription is created
