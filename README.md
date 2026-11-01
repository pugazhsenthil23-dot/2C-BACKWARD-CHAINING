# 2C-BACKWARD-CHAINING# Experiment 2(c) – Implementation of Backward Chaining

## Aim

To implement backward chaining.

## Scenario

A medical expert system is designed to diagnose diseases based on patient symptoms. The system uses backward chaining to infer whether a patient has a specific disease by checking rules and known facts.

## Procedure

1. Define the knowledge base with rules:

   * Flu occurs if both cough and fever exist.
   * Fever occurs if sore throat exists.
2. Define the known facts: `sore_throat` and `cough`.
3. Define the backward chaining function.
4. Check whether the goal is already in the known facts.
5. If rules exist for the goal, verify all conditions recursively.
6. Query whether the patient has flu.
7. Print the diagnosis.

## Program

```python
# Knowledge Base (Rules in IF-THEN format)
knowledge_base = {
    "flu": [["cough", "fever"]],
    "fever": [["sore_throat"]],
}

# Known facts
facts = {"sore_throat", "cough"}

# Backward chaining function
def backward_chaining(goal):
    if goal in facts:
        return True

    if goal in knowledge_base:
        for conditions in knowledge_base[goal]:
            if all(backward_chaining(cond) for cond in conditions):
                return True

    return False

# Query: Does the patient have flu?
query = "flu"

if backward_chaining(query):
    print(f"The patient is diagnosed with {query}.")
else:
    print(f"The patient does NOT have {query}.")
```

## Output

```text
The patient is diagnosed with flu.
```

## Result

Thus, the backward chaining algorithm was implemented successfully using Python. The system checked the symptoms and rules and diagnosed the patient with flu.
