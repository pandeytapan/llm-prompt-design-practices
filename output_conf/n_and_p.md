The words are aren't chosed as a single value but rather a list of words with probablity value. By introducing the temperature we basically controling the sampling i.e. giving model a chance of how much to sample from the top ranking words vs the lower ranking words.

**What temperature does?**

| **Temperature**     | **Behavior**         | **Description**                              |
| :------------------ | :-----------------   | :------------------------------------------- |
| Low (0.1 - 0.5)     | Pick from top tokens | Make the high score sharper - low ranked     |
|                     |                      | ones get tiny chances                        |
| Meduim (1.0)        | Balanced choice      | Maintain relative weights                    |
| High (1.5 - 2.0)    | Random sampling      | Flattens the score. Gives chances to the low |
|                     |                      | ranking tokens also.                         |


A sample table

| **Index** | **Token**  | **0.5** | **1.0** |  **2.0** | **2.5** | **3.0** |
| -------:  | --------   | ------- | ------- | -------  | ------- | ------- |
| 0         | apple      | 0.6364  | 0.4287  | 0.31     | 0.2868  | 0.2715  |
| 1         | banana     | 0.2341  | 0.26    | 0.2414   | 0.2348  | 0.2298  |
| 2         | chery      | 0.0861  | 0.1577  |    0.188 | 0.1922  | 0.1946  |
| 3         | date       | 0.0317  | 0.0956  |   0.1464 | 0.1574  | 0.1647  |
| 4         | elderberry | 0.0117  | 0.058   |   0.1141 | 0.1289  | 0.1394  |

table showing how the token probabilities change at temperature = 2.5 and 3.0:

    - The probabilities are getting even more spread out.
    - Lower-scoring tokens like "elderberry" are becoming more likely.
    - The top token "apple" becomes less dominant as temperature increases.

Example of temperature effect token generation:

| **Temperature** | **Prompt**                              | **Generated Tokens**                                   |
|-----------------|-----------------------------------------|--------------------------------------------------------|
| 0.0             | Tell me about citrus fruit in 20 words. | Citrus fruits, including oranges, lemons, and limes    |
|                 |                                         | are high in vitamin C, known for their tangy flavor    |
|                 |                                         | and culinary versatility.                              |
| 0.0             | Tell me about citrus fruit in 20 words. | Citrus fruits, including oranges, lemons, and limes    |
|                 |                                         | are high in vitamin C, known for their tangy flavor    |
|                 |                                         | and culinary uses.                                     |
| 1.0             | Tell me about citrus fruit in 20 words. | Citrus fruits, includes oranges, lemons, and limes     |
|                 |                                         | are high in vitamin C, known for their diverse cooking |
|                 |                                         | uses.                                                  |
| 1.0             | Tell me about citrus fruit in 20 words. | Citrus fruits, includes oranges, lemons, and limes     |
|                 |                                         | are high in vitamin C, and are widely used in          |
|                 |                                         | cooking.                                               |

| **Temperature** | **Prompt**                              | **Description**                                |
|-----------------|-----------------------------------------|------------------------------------------------|
| 0.0             | Tell me about citrus fruit in 20 words. | Characterized by a thick, aromatic rind       |
|                 |                                         | and acidic, segmented flesh                   |
|                 |                                         | citrus fruits like oranges                    |
|                 |                                         | are famously rich in Vitamin C.               |

The top-p sampling

Top-p sampling, generates text by selecting from a subset of the most probable next words. Instead of choosing from all possible words, it focuses on a dynamic set of words whose cumulative probability exceeds a certain threshold (p).

Let's take the fruits example again. We are applying top-p sampling with a threshold of 0.9, i.e., we only consider the most probable words until their cumulative probability reaches 0.9.

| **Index** | **Token**  | **T = 0.5 top-p = 0.9** | **T = 1.0 & top-p = 0.9 ** | **T = 2.0 & top-p = 0.9** |
| -------:  | --------   | -------                 | -------                    | -------                   |
| 0         | apple      | 66.5%                   | 45.5%                      | 31.0%                     |
| 1         | banana     | 24.5%                   | 27.6%                      | 24.1%                     |
| 2         | chery      | 9.0%                    | 16.7%                      | 18.8%                     |
| 3         | date       | -                       | 10.1%                      | 14.6%                     |
| 4         | elderberry | -                       | -                          | 11.4%                     |

In the all the tokens with cumulative probablity of 0.9 or more are selected. For example, at T = 1.0, the top three tokens "apple", "banana", and "chery" have a cumulative probability of 89.8% (45.5% + 27.6% + 16.7%), which exceeds the threshold of 0.9, so they are selected.

The top-k sampling

Top-k sampling is where the model selects the next word from the top k most probable words. Reduces randomness and focus on more likely candidates.

Let's take the fruits example again. We are applying top-k sampling with k = 3, i.e., we only consider the top 3 most probable words.

| **Index** | **Token** | **T = 0.5 top-k = 3** | **T = 1.0 & top-k = 3** | **T = 2.0 & top-k = 3** |
| -------:  | --------  | -------               | -------                 | -------                 |
| 0         | apple     | 66.5%                 | 50.6%                   | 41.9%                   |
| 1         | banana    | 24.5%                 | 30.7%                   | 32.6%                   |
| 2         | chery     | 9.0%                  | 18.7%                   | 25.5%                   |

In the table, we see that at T = 0.5, the top three tokens "apple", "banana", and "chery" have probabilities of 66.5%, 24.5%, and 9.0% respectively. The model will only consider these three tokens for the next word generation.

Also with changing temperature, the probabilities of the top tokens change. For example, at T = 2.0, the probabilities of "apple", "banana", and "chery" are 41.9%, 32.6%, and 25.5% respectively, showing a more balanced distribution among the top candidates.


`top - p` is best for:

- Structured tasks.
- When you want to control the diversity of the output.
- Controlled and focused generation.

`top - k` is best for:

- Creative tasks.
- Allow more randomness and exploration.
- Generate more diverse and creative outputs.
