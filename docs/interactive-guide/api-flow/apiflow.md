## API Flow

In this section we will go over how to use the API to disburse a payment to a single consumer recipient. By the end of this section you should have a solid foundation of how the API works and how to generate the neccesary infomration for each step.

In general, the flow of the API is as follow:
1. Create a Recipient. 
2. Get an Encryption Key. [^1]
3. Create a single use token for the specified payment method.
4. using that token, save the payment method to the Users account.
5. disburse a payment to the recipient.

[^1]: *If you are using a Trans Armor (TA) token in place of the standard Enrollment Vault (EV) token, You will skip from Step one directly to steps 2 and 3 as you will have already created a token to save to the account.*