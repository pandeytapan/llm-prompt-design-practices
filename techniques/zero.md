# General Prompting / zero shot

This is simplest of the all prompts: -
- Just a task description
- Maybe a question or some text to start with that.
- No examples, no context, no additional information.

## Zero-shot examples

In the examples below, (that are good use cases) we are relying only on the **instructions of the prompt**, and aren't providing any additional instructions

**Text classification**`

```
| **Text**          | Classify the sentiment of the following sentence as                 |
|                   | Positive, Negative, or Neutral: "I love how fast the delivery was!" |
| **Temperature     | 0.1                                                                 |
| **Top P**         | 0.0                                                                 |
| **Input Tokens**  | 24                                                                  |
| **Output**        | Positive                                                            |
| **Output Tokens** | 1                                                                   |
```

**Text summarization**

```
| **Text**          | Summerize the following paragraph in one sentance:                      |
|                   | Bali and Lombok are neighbouring islands; both are part of the          |
|                   | Indonesian archipelago. Bali is a popular tourist destination,          |
|                   | known for its vibrant culture and beautiful beaches, while              |
|                   | Lombok is less developed but offers stunning natural scenery.           |
| **Temperature     | 0.1                                                                     |
| **Top P**         | 0.0                                                                     |
| **Input Tokens**  | 63                                                                      |
| **Output**        | Bali is a popular tourist destination known for its culture and beaches |
|                   | while offers stunning natural scenery.                                  |
| **Output Tokens** | 20                                                                      |
```

**Translation**

```
| **Text**          | Translate the following sentence to French: "Hello, how are you?"   |
| **Temperature     | 0.1                                                                 |
| **Top P**         | 0.0                                                                 |
| **Input Tokens**  | 14                                                                  |
| **Output**        | Comment ça va aujourd'hui ?                                         |
| **Output Tokens** | 6                                                                   |
```

**Extraction**

```
| **Text**          | Extract the date from the following text:                               |
|                   | 10 May 1857, sepoys in Meerut fired the first shots of a revolt that    |
|                   | jolted the British Raj and planted the seed of modern nationalism;      |
|                   | fast-forward to 15 August 1947, when Nehru’s “tryst with destiny”       |
|                   | speech echoed through a newly independent (and very sleep-              |
|                   | deprived) Parliament at midnight; and finally 26 January 1950, the      |
|                   | day the Constitution came into effect, marking the birth of the world’s |
|                   | largest democracy.                                                      |
| **Temperature     | 0.1                                                                     |
| **Top P**         | 0.0                                                                     |
| **Input Tokens**  | 109                                                                     |
| **Output**        | 10 May 1857, 15 August 1947, 26 January 1950                            |
| **Output Tokens** | 20                                                                      |
```

**Question answering**

```
| **Text**          | What is the capital of France? |
| **Temperature**   | 0.1                            |
| **Top P**         | 0.0                            |
| **Input Tokens**  | 6                              |
| **Output**        | Paris                          |
| **Output Tokens** | 1                              |
```

**Rewriting text**

```
| **Text**          | Rewrite the following sentence in a more formal tone: |
|                   | "I can't wait to see you!"                            |
| **Temperature**   | 0.1                                                   |
| **Top P**         | 0.0                                                   |
| **Input Tokens**  | 17                                                    |
| **Output**        | I look forward to seeing you.                         |
| **Output Tokens** | 7                                                     |
```

## When zero shot prompting is useful

- When there is no labelled data available.
- When the task is simple and can be described in a few words.
- When the model is capable of understanding the task from the description alone.
- When you want to quickly test the model's capabilities without providing examples.

## Writing the zero-shot prompt more effectively

**Remove redundant information**:

```
| **Text**          | Sentiment (Positive/Negative/Neutral): "I love how fast the delivery was. |
| **Temperature     | 0.1                                                                       |
| **Top P**         | 0.0                                                                       |
| **Input Tokens**  | 18                                                                        |
| **Output**        | Positive                                                                  |
| **Output Tokens** | 1                                                                         |
```

**Use clear and concise instructions**:

```
| **Text**          | One-sentance summary:
|                   | Bali and Lombok are neighbouring islands; both are part of the          |
|                   | Indonesian archipelago. Bali is a popular tourist destination,          |
|                   | known for its vibrant culture and beautiful beaches, while              |
|                   | Lombok is less developed but offers stunning natural scenery.           |
| **Temperature     | 0.1                                                                     |
| **Top P**         | 0.0                                                                     |
| **Input Tokens**  | 58                                                                      |
| **Output**        | Bali is a popular tourist destination known for its culture and beaches |
|                   | while offers stunning natural scenery.                                  |
| **Output Tokens** | 20                                                                      |
```

**Avoid unnecssary output format**:

```
| **Text**         | Fruits:                                                         |
|                  | Pineapples march in with their spiky swagger, a perfect mix of  |
|                  | sweet and tart, while bananas, with their smooth, yellow coats, |
|                  | bring a creamy, tropical vibe. Apples, crisp and refreshing,    |
|                  | add a touch of crunch to the fruity parade.                     |
| **Temperature    | 0.1                                                             |
| **Top P**        | 0.0                                                             |
| **Input Tokens** | 58                                                              |
| **Output**       | Pineapples, bananas, apples                                     |
| **Output Tokens**| 3                                                              |
```

**Avoid unnecessary instructions**:

```
| **Text**          | English to Hindi: "Hello, how are you?" |
| **Temperature**   | 0.1                                     |
| **Top P**         | 0.0                                     |
| **Input Tokens**  | 14                                      |
| **Output**        | नमस्ते, आप कैसे हैं?                          |
| **Output Tokens** | 5                                       |
```
