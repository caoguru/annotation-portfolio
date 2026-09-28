markdown

# Annotation Guidelines: Sentiment Classification (Week 1 Practice)

## 1. Label Definitions (Rules)

### positive
- Definition: Clear satisfaction, praise, or intention to recommend regarding a product/service
- Criteria: Contains positive expressions such as "good," "satisfied," or "recommend"

### negative
- Definition: Dissatisfaction, disappointment, or inconvenience regarding a product/service
- Criteria: Contains negative expressions such as "not great," "unfriendly," or "below expectations"

### neutral
- Definition: A factual statement or neutral evaluation that is neither positive nor negative
- Criteria: Reservation of judgment, such as "it's just okay" or "I guess it's fine"

## 2. Examples

### Example 1

- Original: "I am satisfied with the product"
- Annotation: positive
- Reason: Clear expression of satisfaction

### Example 2
- Original: "The customer service response was unfriendly"
- Annotation: negative
- Reason: Clear expression of dissatisfaction

## 3. Edge Cases

### Edge Case 1: Mixed Positive + Negative
- Situation: "Shipping was fast, but the product is not great"
- Judgment: negative
- Reason: The final evaluation is negative. Even if positive elements are present, if the overall sentiment is negative, it is labeled negative.

### Edge Case 2: Ambiguous Expression
- Situation: "It seems okay for the price"
- Judgment: neutral
- Reason: "It seems okay" is a reserved expression without confidence. It is not clear satisfaction.

### Edge Case 3: Conditional Recommendation
- Situation: "I intend to purchase again"
- Judgment: positive
- Reason: Repurchase intention is a clear positive signal.