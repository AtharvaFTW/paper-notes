# Direct Preference Optimization:Your Language Model is Secretly a Reward Model

### Key Findings:

**What is the core problem DPO identified with RLHF's reward model approach?**
-> The identification of how RLHF's seperate reward model can be 'Gamed' to maximize the scores brought the DPO to life. The policy can learn to produce output's the score high on the RM without actually getting better itself.

**What does DPO optimize directly, and what does it skip?**
-> It mathematically reparameterizes the reward function in terms of the policy itself, meaning the RM is implicityly embedded directly within the policy.Eliminating the need of seperate RM becuase the math shows the ability to express the optimial reward directly through the trained policy to the reference policy.

The DPO keeps a frozen copy of the original SFT model as an anchor. The trained policy cannot drift too far from it.

**What does the DPO loss function look like conceptually?**
-> The loss is essentially a binary cross-entropy that increases the likelihood of prefered response relative to the rejected one, keeping close to the reference model by penalizing the policy for moving too far from the reference model's distribution on any output, not just the preference pairs via KL penalty making the DPO stable.The gap between the good and the bad reponses is what keeps the math happy.