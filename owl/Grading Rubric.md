# Write a Grading Rubric Specific to This Prompt

In the rubric, describe aspects that are required to form the perfect completion, the **ideal** completion. The rubric should be **very specific to the user prompt, focusing on non-obvious and context-dependent traits, but excluding general aspects** such as being grammatically correct or brevity/correctness--which are already part of the given axes. If you do 10 tasks, you should probably not have too many repeated bullet points. One helpful way of thinking about the rubric is that while there are many different ways of writing the ideal completion for a given user prompt, they must all share the same critical points. Thus the goal of the rubric is to identify these critical points.  
  
Additionally, the rubric should follow this format:

1. Provide a short summary in about 1 - 2 sentences of what the User is looking for
2. 1. consider referencing the User "thumbs down" reason which is available when you open the `Instructions` from a task)  
3. followed by about 2 - 5 bullets covering key points that need to be met by the completion in order to create the perfect response
Below an example of the rubric's typical format:

`First write a short summary (1-2 sentences) summarizing the (task-specific) User’s intention or desires. (Read the User’s original ChatGPT feedback to see why the original User was upset – this can help you understand their intent.)      - Then provide bullets summarizing the key requirements to satisfy the User’s intention   - These bullets can also include things to avoid, if possible in the context   - Be as task-specific as possible. Avoid cliches or general guidance.`

  

## IMPORTANT THINGS TO CONSIDER WHEN WRITING THE RUBRIC:

- The criteria should be **very concrete and specific to this user prompt**. Avoid general statements if possible. Essentially, the criteria should be written for this user prompt only, instead of for a broader class of prompts similar to this one.
- - Bad example: `the ideal completion should use the the correct formula.`
    - Good example: `the ideal completion should use Pythagorean theorem.`
    - Bad example: `the ideal completion should implement the plotting code using the right function in matplotlib`
    - Good example: `the ideal completion should implement the plotting code using the "scatter" function of matplotlib`
- The criteria can include non-essential but nice-to-have points, but please explicitly state that these points are optional
- - e.g. `Including some examples of applications of deep learning is nice-to-have but optional.`
- Write a rubric like you’re a teacher for a question on an assignment
- - i.e. like instructions for your teaching assistant
- Do not use first person (”I” statements)
- Each bullet point should be a grammatically correct statement. (i.e. no half sentences or other grammatical shortcuts people normally take with bullet-points).
- - Bad Example - `A clear explanation of the approach`
    - Good Example - `It is critically important that a clear explanation of the approach is provided`
- The bullets can be what the response should include, or it can also include what the response should avoid if it is applicable.
- Don't point to any of the completions, neither to their ratings. Mentioning explicit values is allowed in the rationales, but not in the rubrics.
- It is fine to reference criteria from the system message in the rubrics. The model should obviously never reference the system message in its regular assistant-turns.