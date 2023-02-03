## API Flow

In this section we will go over how to use the API to disburse a payment to a single consumer recipient. By the end of this section you should have a solid foundation of how the API works and how to generate the neccesary infomration for each step.

In general, the flow of the API is as follow:
1. Create a Recipient. 
2. Get an Encryption Key.[^1]
3. Create a single use token (*nonce token*) for the specified payment method.
4. using that token, save the payment method to the Users account, in turn receiving an Enrollment Vault (*EV*) Token
5. disburse a payment to the recipient's account using the EV Token.

[^1]: *If you are using a Trans Armor (TA) token in place of the standard Enrollment Vault (EV) token, You will jump from Step 1 directly to step 5 as you will not need to create an EV Token.*

![Next](../../../../assets/images/button.png)]( /docs/?path=docs/interactive-guide/api-flow/create-recipient.md)