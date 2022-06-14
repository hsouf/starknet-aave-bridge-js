# starknet-aave-bridge.js


The starknet-aave-bridge.js package gives developers access to methods for interacting with the AAVE bridge & staticATokens on Starknet using [ArgentX](https://github.com/argentlabs/argent-x) & [Starknet.js](https://github.com/0xs34n/starknet.js).

Install starknet-aave-bridge-js with `npm`

```bash
$ npm install starknet-aave-bridge-js
```


Withdrawing staticATokens on l2:


```javascript
import {getStarknet} from "@argent/get-starknet";
import {withdraw} from "@starknet-aave-bridge-js";

export const handleWithdraw=async (
  l2_token: bigint,
  l1_recipient: string,
  amount: string
): Promise<any> => {

    const starknet=getStarknet();
    await starknet.enable();

    const tx=withdraw(starknet, l2_token, l1_recipient, amount);
    return tx;
  
}
```


Get staticAToken data:

```javascript

import {getStaticATokenData} from "@starknet-aave-bridge-js";

const tokenInfo=getStaticATokenData(aDAI.address);// returns totalSupply, last_rewards_index_blocknumber & current_rewards_index
 



```

Get staticATokens holder info:

```javascript

import {getUserInfo} from "@starknet-aave-bridge-js";

const userInfo=getUserInfo(aDAI.address, l2_user_address );// returns balance, user's pending rewards & latest claimed rewards index (snapshot)



```
