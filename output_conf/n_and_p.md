The words are aren't chosed as a single value but rather a list of words with probablity value. By introducing the temperature we basically controling the sampling i.e. giving model a chance of how much to sample from the top ranking words vs the lower ranking words.

What temperature does?

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
