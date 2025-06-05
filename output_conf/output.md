Controling the number of output tokens in an LLM response is crucial for managing costs and ensuring the response is concise. Here are some strategies to control output tokens:

1. **Set a Maximum Token Limit**: Most LLM APIs allow you to specify a maximum number of tokens for the response. This is the simplest way to control output length.

2. **Use Prompt Engineering**: Design your prompts to elicit shorter responses. For example, instead of asking for a detailed explanation, you can ask for a summary or a specific piece of information.

3. **Specify Response Format**: If the LLM supports it, you can specify the format of the response (e.g., bullet points, short answers) to encourage brevity.

4. **Iterative Refinement**: If the initial response is too long, you can refine your prompt based on the output to ask for a more concise version.

Here are some examples of the above strategies:

**Maximum Token limit**

Version 1
```markdown
| **Strategy**       | **Description**                                                                                           |
|--------------------|-----------------------------------------------------------------------------------------------------------|
| **Model**          | gpt-4.1-nano                                                                                              |
| **Example Prompt** | Explain quantum computing in few words                                                                    |
| **Input tokens**   | 6                                                                                                         |
| **Characters**     | 38                                                                                                        |
| **Output Tokens**  | 100                                                                                                       |
| **Temperature**    | 0.0                                                                                                       |
| **Output**         | Quantum computing uses tiny particles to perform complex calculations much faster than regular computers. |
| **Characters**     | 108                                                                                                       |
| **Output Tokens    | 17                                                                                                        |
```

Version 2
```markdown
| **Strategy**       | **Description**                                                                                    |
|--------------------|----------------------------------------------------------------------------------------------------|
| **Model**          | gpt-4.1-nano                                                                                       |
| **Example Prompt** | Explain quantum computing in few words                                                             |
| **Input tokens**   | 6                                                                                                  |
| **Characters**     | 38                                                                                                 |
| **Output Tokens**  | 50                                                                                                 |
| **temperature**    | 0.0                                                                                                |
| **Output**         | Quantum computing uses quantum bits to solve problems faster using superposition and entanglement. |
| **Characters**     | 97                                                                                                 |
| **Output Tokens    | 17                                                                                                 |
```

Version 3
```markdown
| **Strategy**       | **Description**                                                                                    |
|--------------------|----------------------------------------------------------------------------------------------------|
| **Model**          | gpt-4.1-nano                                                                                       |
| **Example Prompt** | Explain quantum computing in few words                                                             |
| **Input tokens**   | 6                                                                                                  |
| **Characters**     | 38                                                                                                 |
| **Output Tokens**  | 25                                                                                                 |
| **temperature**    | 0.0                                                                                                |
| **Output**         | Quantum computing leverages quantum mechanics to perform complex calculations rapidly.             |
| **Characters**     | 85                                                                                                 |
| **Output Tokens    | 12                                                                                                 |
```

Prompt Engineering

Version 1: Just plain prompt
```markdown
| **Strategy **       | **Description**                                                                                     |
| ------------------- | --------------------------------------------------------------------------------------------------- |
| **Model**           | gpt-4o                                                                                              |
| **Example Prompt**  | Explain quantum computing in few words                                                              |
| **Input tokens**    | 6                                                                                                   |
| **Characters**      | 38                                                                                                  |
| **Output**          | Quantum computing uses quantum bits (qubits) that can be in multiple states at once (superposition) |
|                     | and interact through entanglement, allowing them to process complex problems much faster than       |
|                     | classical computers in specific domains.                                                            |
| **Characters**      | 234                                                                                                 |
| **Output Tokens     | 43                                                                                                  |
```

Version 2: Prompt engineered for brevity
```markdown
| **Strategy **       | **Description**                                                                                     |
| ------------------- | --------------------------------------------------------------------------------------------------- |
| **Model**           | gpt-4o                                                                                              |
| **Example Prompt**  | Explain quantum computing in one short sentance                                                     |
| **Input tokens**    | 8                                                                                                   |
| **Characters**      | 47                                                                                                  |
| **Output**          | Quantum computing leverages qubits to perform parallel computations using superposition and         |
|                     | entanglement                                                                                        |
| **Characters**      | 105                                                                                                 |
| **Output Tokens     | 18                                                                                                  |
```

Version 3: Prompt engineered for controlled output characters limit
```markdown
| **Strategy **       | **Description**                                                                                     |
| ------------------- | --------------------------------------------------------------------------------------------------- |
| **Model**           | gpt-4o                                                                                              |
| **Example Prompt**  | Explain quantum computing in maximum 90 characters                                                  |
| **Input tokens**    | 8                                                                                                   |
| **Characters**      | 50                                                                                                  |
| **Output**          | Quantum computing uses qubits, superposition & entanglement for fast computation.                   |
| **Characters**      | 81                                                                                                  |
| **Output Tokens     | 16                                                                                                  |
```

Response Format
