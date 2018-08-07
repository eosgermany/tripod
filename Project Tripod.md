# Project Tripod

## Overview
The EOS platform is facing criticism, both internal and external of the community, mostly around its not so decentralized nature, perceived or not, as well as the lack of test networks.

The undersigned also want to raise that the number of standby block producers are not enough, especially considering how many are running on cloud infrastructure and in countries with "questionable" online ethics. EOS is much more vulnerable than leaders of the community want to acknowledge, and literally 3 coordinated actions is enough to bring down the network, court orders against Amazon and Google, plus a China Great Firewall block.

We have also seen that standby block producer not being ready when elected block producer.

EOS Community does not have an solid upgrade plan in place. How are new features introduced to the EOS platform in a responsible manner? How are dApps developers getting access to, and ability to test with, new testnets, other than chaotic independent testnets that are not necessarily reliable nor trustworthy.

This proposal intends to address ALL of the above.

Project Tripod stands on 3 legs; Strengths in Numbers, Operational Readiness and Healthier Community.

## Goals
1. Increase the number of operational standby producers, enshrining readiness into standby block producers.
2. Provide reliable test networks for dApps developers.
3. Staged, organized deployment of new features.
4. Increase EOS resilience against government action.

## Specifications
The mainnet is served by block producers 1-21. The standby block producers operates 4 testnets in evolutionary sequence; Tier 1 is served by BP 22-42, Tier 2 by 43-63, Tier 3 by 64-84 and Tier 4 by 85-105. An additional 10 block producers (106-115) are standby outside the testnets.

Any change, that are not critical to security or stability of the network itself, must be deployed in order on the testnets, starting at Tier 4, 2 weeks apart. This provides 2 weeks of testing at each tier, 8 weeks in total, before the change is applied to mainnet.

Bugs found at any tier, will send the change all the way back to Tier 4 after a fix. Not only does this ensure provenance and due diligence, but also promotes small, reversible changes, rather than big bang upgrades, as a bug in one unrelated part (say, in contractA) could prevent the deployment of something else (say, a new contractB).

Within a Tier, the same rules of block production exists. Each Tier will have its own genesis block, and there will be the following additional changes to each Tier;

- Tier 1
Tier 1 has exactly the same set up as mainnet.
Re-synchronizes with mainnet once every 4 hours.

- Tier 2
Same as Tier 1, except
Re-synchronizes with mainnet once every 48 hours.
Unstaking of tokens are set to 1 hour. 
Voting decay is set to 50% in 1 day.

- Tier 3
Same as Tier 2, except,
Creating an account allocates 10,000 EOS to the account.
EOS Tokens are automatically burned by 100 EOS/day per account.

- Tier 4

Same as Tier 3, except
Code execution time limit is set to 10x of Tier 3.
Bandwidth restriction, to avoid abuse.

## Rewards

The number of paid block producer candidates is in our opinion too small.  The initial intent of 21+100 was a much more reasonable goal. At the same time, we don't wish to change the reward currently allocated. We propose the following;

Under the current system, 0.75% inflation is allocated to be distributed to the block producer candidates by share of votes. 0.25% inflation is to be shared among the elected block producers equally.

We suggest that Tier 1 and Tier 2 is receiving 0.15% each, Tier 3 and Tier 4 is receiving 0.1% each. The total BP inflation is hence increased from 1% to 1.5%. We estimate that this is acceptable to achieve the goals set forth above. For the 10 BPCs outside Tier 4, we suggest a flat 100EOS/day.

For a BP 100 this will result in 130EOS/day.

## Tier Transition

In the current EOS setup, all BPCs are running nodeos on the same blockchain. For this proposal to work, additional work is required to handle 5 parallel networks, and ability for block producers to switch network easily, preferably automatically. 

We could put all the endpoint data for all the testnets on the mainnet, which would allow for us to develop tooling to automate all of it. The bootstrap problem is also not present, as these testnets can require the mainnet to be operational (at least read-only API endpoints).

There are obvious issues with this, such as the node coming into the tier will need to drop the block chain it is working on and start over. However, for tier 1 and tier 2, there should be relatively recent.

## Readiness

Being ready to produce blocks is the primary function of Standby Block Producers. But at the moment, there is no incentives, nor checks that this is actually the case.

By adopting this proposal, every Standby Block Producer from 22 to 115 are actively producing blocks on testnets. Failure to do so has a direct negative consequence, no rewards. And for new participants, there is plenty of "runway" to practice, not only block production, but to switch tiers and upgrade nodeos on an active network. Additional exercises may also be practiced on the test networks, such as testing large-scale failures, DDoS, simulating government strike downs, and other potential risks identified.

## Risks

### Abuse of platform

Applications trying to abuse EOS will hereby be provided with additional avenues to do so. But is this any different than the many testnets running independently out there? Wouldn't a spammer more easily put the abusive code on AWS or GCE? Will we see applications that tries to get additional RAM/compute/network by deploying across multiple networks in a collaborative fashion? Hard to predict if there are any incentives to do so, and whether the BPCs will suffer as a result.

### Technology won't work

There are a set of development work needed to make this reality. 
- Resynchronization with mainnet.
- Tier transition
- Daily EOS burning on Tier 3 and 4.
- Auto-allocation of funds on Tier 3 and Tier 4
- Tier-support in build system.
- Other...

It is unreasonable to expect this to be developed by Block.one, so community will need come together and make this happen. But among 100 BPCs, there should be enough talent, and there should be enough capital around to make it a reality.

### Less capital for other things

It is true that an additional 0.5% of inflation is taken for this purpose. But we claim that it is offsetted by real value;

- dApps needs reliable testing environments, especially in the early days, even perhaps to simply test the feasibility of the idea. Being able to do that on test network, not having to worry about EOS tokens, renting tokens, expensive RAM purchases (or rent) and a lot more. 
- There is currently no robust process to bring new features to the mainnet. Individual testing here and there, and then hoping it will work as advertised on the mainnet is foolish at best, but reckless and irresponsible are better words. With these testnets, new features and fixes will be going through real application testing, ensuring no regression, and apps needing the new features can test them out at scale before hitting the mainnet.
