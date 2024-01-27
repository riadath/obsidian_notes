# Introduction

The goal of this campaign is to produce data on topics and requests where the model does not perform as well in order to help improve its performance. The tasks will contain preseeded conversations between a user and the assistant and model generated completions will be provided in response to the last preseeded user message. Please **compare the completions , fill in the rationale for these ratings** and provide an **ideal completion and a grading rubric**. Note that unlike the previous round of preseeded conversations, this **campaign puts much more emphasis on the rationale and prompt specific grading rubrics**, as these information are now also used to train our model and therefore not only for QC process.

  

In short, each task in this campaign consists of the following three parts:

1. **Completion Comparison**: rate the completion along different axes, scoring between 1 and 7, and provide detailed rating rationale explaining your reasoning behind the score.
2. **Ideal Completion**: the perfect example model response to the User message.
3. **Grading rubric**: write a prompt specific grading rubric that describes what constitutes a good completion for this specific prompt

  

---

# Table of Contents

- Select a Task
- - Tasks to Skip
    - Batches
- Completion Comparisons
- - Fill Out the Form for Each Completion
    - - Rating Along Provided Axes
        - Rating Rationale
        - Common Mistakes Categories
- Write an Ideal Completion
- Write a Grading Rubric Specific to This Prompt
- Additional Turns
- FAQ
- Glossary

  

---

# Select a Task

As there is a conversation already preseeded for each task, please choose a task based on your familiarity and expertise on a given topic. Use the search bar to look for parts of the task description or tags associated with different topics. Find a task with an interesting topic and claim it to start tasking.

  

# Tasks to Decline

Some tasks will contain preseeded conversations that are not suitable or appropriate to work on. In such cases, please decline the task with the "decline" button on the top right corner.

1. Tasks that contain any preseeded conversation topics that make you feel uncomfortable.
2. 1. Select `Sensitive content` in the decline category
    2. Sensitive content is defined as: `anything that may cause offence to a reader or user, particularly in relation to religion, race, gender, politics, sexuality, disability, or vulgar language.`
3. Tasks that contain any Personal Identifiable Information (PII).
4. 1. Select `Pii content` in the decline category.
    2. PII is defined as:
    3. 1. Any representation of information that permits the identity of an individual to whom the information applies to be reasonably inferred by either direct or indirect means. Further, PII is defined as information:
        2. 1. That directly identifies an individual (e.g., name, address, social security number or other identifying number or code, telephone number, email address, etc.)
            2. By which an agency intends to identify specific individuals in conjunction with other data elements, i.e., indirect identification. (These data elements may include a combination of gender, race, birth date, geographic indicator, and other descriptors). Additionally, information permitting the physical or online contacting of a specific individual is the same as personally identifiable information. This information can be maintained in either paper, electronic or other media.
5. Tasks that ask about the Assistant's "self" (about ChatGPT) or knowledge cutoff.
6. 1. Ex. “What version of ChatGPT are you?”, “When is the knowledge cutoff?”
    2. Select `Other` in the decline category.
7. Tasks that require Assistant refusal.
8. 1. Ex. Prompts that would cause the Assistant to say it can't do something because it's not ethical, allowed to, etc.
    2. Select `Requires refusal` in the decline category.
9. Tasks that are too easy for the model.
10. 1. Completions all deserving 7s even after resampling is a good sign that the topic is too easy for the model. Please skip/avoid such tasks.
    2. For now, select `Other` in the decline category.

  

# Batches

1. _subjective: The solution for tasks in batches with the _subjective_ suffix is expected to be, as the name implies, more subjective than the _general_ batches.
2. _general: Regular tasks
3. mt_: These batches include tasks that have already been labeled once before. The sampled completions will be different the first time around, but the original conversation is the same. Complete these tasks like you normally would except:
4. 1. Do not cheat by trying to find the originally completed tasks, your solution must be unbiased
    2. The trainer who originally completed the task is indicated in the task-level instructions. These tasks should be done by someone different than the first time around. Do a quick check before claiming.
    3. You needn't enter an ideal completion
    4. 1. You should still provide a rubric
        2. You can enter an ideal completion if you find it would be helpful for yourself to write a rubric
        3. If you feel confident in your ability to make a rubric without first making an ideal completion, please enter "SKIP" in the ideal completion box and just fill out the rubric

Roughly do one mt_ task for every two regular tasks you do

---

# Completion Comparisons

Once you claim a task, you will be provided with 4 model generated completions in response to the last preseeded User message, using the whole conversation in its context. Select through each of the 4 tabs and carefully read each completion.

  

# Fill Out the Form for Each Completion

**RATING ALONG THE STYLE AND CONTENT AXES**

For each completion, you will provide ratings of 1 to 7 along the style and content axes, as well as the overall rating. The previous axes (correctness, informativeness, clarity, and creativity) are now a subset of content.

As before, not all of the evaluation criteria within each of the new axes apply to every user prompt, which means you should consider only those relevant to the task at hand. For instance, creativity might not be relevant for many coding queries.

The overall axis is an aggregation of your ratings along the individual axes of Content and Style -- but it is also more than that. As before, you should not just be doing some kind of averaging of your axes like a calculator to determine overall -- you should instead use the axis ratings as context/guidelines and give your intuitive judgement of the overall quality. There may be edge cases where this score is high even though individual axis scores are low -- that is more than fine!

The overall axis is meant as a way for you all to provide case-specific, subjective, intuitive combinations of the various axes, and the rationale is a way for you to explain that intuitive combination as much as possible.

In many tasks it might be the case that the Overall Likert is basically always the Content Likert. However there may be _some_ instances where things that are normally _good_ from a content perspective are less helpful overall (and vice-versa).

- Maybe it's a task like "rewrite this text like you're Hunter S Thompson" -- the content stuff should almost always be a slam dunk, the model is super good at rewriting text

- - i.e. 7's or 6's across the board on all completions

- But maybe stylistic concerns are the dominant factor here (and are not necessarily complicated stylistic concerns that require special training) and hence the Likerts are more dependent upon style
- Contrast this with a task where you're writing code for a nuclear reactor -- the style doesn't matter _nearly_ as much as the Content
- Similarly there may be reasons why in task A you consider Correctness or Clarity of the Content to be sacrosanct, but maybe in task B Clarity isn't nearly as important as the Creativity of the Assistant, mention these things in the rationale

If the reason you are repeating other rationales in your overall rationale is because this helps you explain your reason and disambiguate which parts of the completion helped and which hurt -- then go for it. If you're just putting it in there because you're scared of leaving the rationale short or blank, that's probably not an efficient use of your time.

For the style axis -- give your intuitive opinion on this, do not spend a lot of time here.

- The content axis should be your top priority
- A very close second should be the overall axis
- The style axis is a very distant third place

## RATING RATIONALE

Please explain the reasoning behind the specific axes and overall quality rating score in detail. Unlike in previous campaigns, providing high quality rationale in this campaign is crucial as we are now also using the rationale in model training besides just for quality control purposes. The rationale should include some of the following aspects

1. **Begin with Objectivity and Reference Specific Criteria**: Always start your rationale with an objective observation about the completion. Avoid inserting personal feelings or biases. Clearly identify which criteria the completion met or failed to meet from the provided list. This ensures that the rationale directly correlates with the given evaluation guidelines.
2. 1. _Example_: "The completion provided a detailed answer to the user's question."
3. **Highlight the Mistakes and Provide Correct Information (If Possible):** When evaluating a completion, it's imperative to identify and highlight any common mistakes the model makes. These can range from misinformation about a topic, recommending outdated methods, or incorrect data. Clearly indicate the exact part of the completion where the error occurs. Avoid generic statements; instead, pinpoint the exact error. If possible, categorize the error for clarity. For instance, you could label errors as "Historical Inaccuracy," "Scientific Misinformation," "Outdated Recommendation," etc. If you are certain of the correct information, provide it in your rationale. This not only highlights the error but also aids in correcting it.
4. 1. Example: “The completion claims that water boils at 105°C, which is incorrect. The correct boiling point of water at 1 atm is 100°C.
5. **Use Comparisons If Relevant**: If rating the completion relative to others, specify what made it better or worse.
6. 1. _Example_: "Compared to completion A and B, this one was the only one that addressed the user's main concern."
    2. **UPDATE 1/17/2024**: Rationales must remain self contained in the sense that the rationale for one completion should only be about that completion.
    3. _Example:_ Given that using LaTeX is better than not for a completion, instead of saying: "This response is identical to suggestion B but lacks the use of LaTeX, making the readability harder than suggestion B and thus the clarity and overall scores lower than B's", say: "This response would be made stronger by the use of LaTeX. This makes readability hard and thus the clarity and overall scores are lower than they would be if LaTeX had've been used"
7. **Be Concise but Comprehensive**: Ensure your rationale is succinct but covers all the relevant points. Avoid being overly verbose.
8. 1. _Example_: "The response was on-topic, well-organized, and didn't contain any errors. However, it was less actionable than completion #2."
9. **Avoid Ambiguity**: Make sure your rationale is clear and can be easily understood by someone who might not be familiar with the specific interaction.
10. 1. _Example_: Instead of saying "The answer was not good," you could specify, "The answer was vague and didn’t directly address the user's prompt."
11. **Provide Constructive Feedback**: If a completion has room for improvement, mention what could make it better. This feedback is valuable for improving the chatbot's training.
12. 1. _Example_: "The response could be improved by providing a step-by-step guide instead of just suggesting a generic solution."
13. **End with a Summary**: Conclude the rationale with a brief summary statement that encapsulates your evaluation.
14. 1. _Example_: "Overall, while the response was organized and error-free, it lacked directness and actionability compared to the other completions."
15. **Style:** Rationales for the style axis can be left blank.

  

Common Mistake Categories

- **Knowledge Error**: A clear and straightforward factual inaccuracy. Whether hedged or unhedged.
- "Barack Obama was born in 1965."
- **Understanding Error:** A clear error, but requiring a more subtle understanding of a topic. Also, not understanding the user’s initial question/prompt, which leads to a different kind of answer or an outright wrong answer.
- "This code would raise an IndexError" (when it would in fact not)
- **Unhedged Error:** Select this category in addition to a factual-inaccuracy error to flag that a factual inaccuracy was not hedged
- **Over-hedge:** A claim that is actually true, but hedged unnecessarily. This might be the correct behavior for the model given its knowledge, but it should still be pointed out.
- "I think Barack Obama was born in 1961, but I'm not sure"
- **Inadequate Information:** The Assistant does not provide enough information or context, resulting in a completion that is less helpful due to lack of detail, doesn’t fully answer the user question, or leaves a misleading impression. A combination of the old Coverage Error and Misleading Impression.
- More details - Inadequate Information
- - **Coverage:** the Assistant’s response does not answer the User’s request or question at all and/or the response is factually accurate, but is not helpful because it lacks detail.
    - “User: What exercises are good for climbers? Assistant: Exercises that are good for the arms and legs.” - The information provided by the Assistant is factually accurate but not very helpful because it lacks detail.
    - **Misleading impression**: there may not be a specific error, but the completion gives a misleading overall impression, including statements that the Assistant should have said but wasn’t included in the response.
    - “Hitler was a political figure in Germany during WWII” or “Hitler was an artist in Germany” and fails to mention that he was the leader of the Nazi Party, therefore potentially misleading the user into thinking that he was not an important figurehead during that time.
- **Spelling/grammar:** Self-explanatory.
- **Formatting Issue:** Including Markdown and LaTeX, the formatting of the completion is broken or not implemented well.
- **Verbosity:** The completion is needlessly wordy and lengthy, providing repeated or unnecessary information, or a lot of fluff.
- **Suboptimal Organization:** The overall layout of information is such that it is harder to follow than it could be, or some information needs to be repeated without the need for emphasis.
- **Suboptimal Word Choice:** There are better words the Assistant could have used to drive the information to be more precise, accurate and concise.
- **Hallucination**: Any blatant fabrication—e.g. a made-up name, info, URL, "the source X says Y" when it doesn't say that at all. **Watch out for these**! They are surprisingly common, but they are not the sort of mistake a human would reasonably make.
- More details - Hallucination
- - Assistant may claim to have performed some real-world task such as submitting a form – these are hallucinations! v
    - Giving the user current time or the weather is also hallucinations when the Assistant does not have the ability to browse, it is fabricating the time and/or the weather.
    - Sometimes the Assistant will claim to have performed some real-world task such as submitting a form – these are hallucinations! e.g. “I ran that code and it said xxx”.
    - Identity Error: a violation of the guidelines on how the model should talk about itself. The most common mistake of this kind is pretending to be human, e.g. "that happened to me once", or "I am 6 feet tall", or “I can run that code”.
- **Unreasonable opinion:** A claim that is a matter of opinion made by the Assistant and not by a verifiable source, that isn't well-justified, or is inappropriately stated as fact, e.g. "Apricots are the tastiest fruit".
- **Programming bug:** a problem with code in the completion.
- **Non-Ideal Code Implementation:**
- **Model Behavior Error**: Any error against how the Assistant should normally act to provide a comfortable and positive experience for the users. A combination of these former categories: Unkind Response, Inappropriate Response, Unnecessary ask for clarification, Unhedged Speculation.
- More details - Model Behavior Error
- - **Unkind Response:** the completion is impolite or otherwise fails to be considerate to the User or anyone else.
    - **Inappropriate Response**: the completion discusses a topic that would be inappropriate to discuss with a stranger (such as asking for the user’s exact location when asking for directions), or affiliates with a side or judges one group as good or bad in a culture war topic.
    - **Unnecessary ask for clarification:** Unnecessarily repeats the question or rephrase the question slightly, instead of asking a relevant clarification. Example: [User] “Please tell me about WWI” [Assistant] “Do you want me to tell you more about WWI?”
    - **Unhedged speculation:** a claim for which there is no reasonable way to tell if the statement is true or not, e.g. "Barack Obama likes apricots". If the claim is hedged appropriately, then this does not count as a mistake, e.g. “Many experts/analysts have claimed XXXXXX, but I can’t find any source/I can’t verify that to be a fact.”
- **Irrelevant Response:** the completion contains information that isn't relevant to the User's question or otherwise helpful to them.
- **Refusal to Answer:** the completion refuses to help, even though the model is capable of helping without producing disallowed content. This includes saying "I don't know" when the model does know or when it state “I can’t do that” when it clearly can.
- **Tool Error:** Any error that is caused by misuse of or offering to use the model “tools”—such as browsing.
- More details - Tool Error
- - **Wrong offering to browse decision:** the completion offers to browse the web.
    - **Wrong browsing decision:** Not applicable in Conversation Comparison tasks, but it is when the completion opens the browser when it shouldn't, or fails to open the browser when it should.
    - **Other Tool Errors**
- **Message cutoff:** Assistant’s message cuts off abruptly (because it was running too long).
- **Other**: any other mistake. When a mistake that requires the need for the “Other” category is encountered, please flag it!

  

**NOTE:** Even if the completion was given a score of 7, provide the rating rationale such as details on what makes the completion better than others or fact-check citing.

  

---

# Write an Ideal Completion

After comparing and rating each of the completions in the turn, provide an **Ideal Completion** where you are giving an example of the perfect response to the User message. The ideal completion should be free of any kinds of mistakes and be as helpful as possible.

Please imagine how a **perfect** AI model would respond to the User message when coming up with the ideal completion. Original responses greatly preferred, but feel free to use parts of the generated completions that you especially like to help come up with the best possible response. Additionally, consider using ChatGPT to help refine and perfect your the ideal completion.

  

---

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

  

## EXAMPLE RUBRICS:

Below are examples taken from completed tasks. `Original Rubric` shows a rubric that needs improvement, and `Example Rubric` shows how the rubric could look taking the above guidance into consideration.

  

From Task [SEO Optimization - Strategies for Improving Contact Page SEO with Keywords](https://feather.openai.com/tasks/b9d78f26-65fb-4375-9ec2-99f279cd1406)

Last User Message: "Please limit to 160 characters max"

### ORIGINAL RUBRIC

`- I considered conciseness in the completion, removing any information that may not be relevant to the user query.   - Spelling and grammar errors were avoided by employing Grammarly.   - The word count was confirmed to make sure it was within the user specification.`

### EXAMPLE RUBRIC

`The user is asking for a 160 character max, SEO friendly excerpt for the user’s mechanics business website’s contact page. Here are the criteria to make a good excerpt:   - The excerpt should be concise and under 160 characters   - The excerpt should emphasize the name and the services of the user’s business   - The excerpt should contain information about contact and inquiries`

Explanation:

- The rubric should follow the format of a summary of what the user wants followed by bullets that cover specific key points.
- `I considered conciseness in the completion, removing any information that may not be relevant to the user query.` + `The word count was confirmed to make sure it was within the user specification.`

- - These are generic abd vague. and not specific to the user prompt; instead, the keypoint should explicitly and specifically state that 160 characters is the maximum.
    - Do not use first person ("I" statements).
- `Spelling and grammar errors were avoided by employing Grammarly.` -
- - Spelling and grammar is generic and should be a standard that is followed without needing to be stated in the rubric.
    - Outside tool usage such as "Grammarly" should not be mentioned.

  

From Task [Book Summaries - Overview of "The Hobbit" by J.R.R. Tolkien Chapter by Chapter](https://feather.openai.com/tasks/a25ad6c7-f013-4a37-86aa-91df3c0eb929)

Last User Message: "write a summary for each chapter"

### ORIGINAL RUBRIC

`- The summary has to select the relevant aspect of the narrative to share with the user to maximize the knowledge of the material yet comply with the brevity of the text. It is all about the smart selection of the facts.   - There should be fluency from one chapter to another.   - The summary has to reflect the spirit of the book. A style that is not a mimic of the author but a reflection of it would be preferable.`

### EXAMPLE RUBRIC

`The user is asking for chapter summaries of the book “The Hobbit”.   - There should be a bullet point for each chapter in the book — no chapter should be missing.   - The summary has to select the relevant aspect of the narrative to share with the user to maximize the knowledge while remaining brief; it is important to be smart in selection of the facts. Each bullet point should contain a brief (1-2 sentence) summary of that chapter.   - Each bullet point should start with the title of the chapter being summarized, if available, otherwise it should start with the chapter number.`

Explanation:

- The rubric should follow the format of a summary of what the user wants followed by bullets that cover specific key points.
- The rubric should specify the necessity to cover "each" chapter.
  

---

# Additional Turns

For the majority of the tasks, one good response should satisfy the User query, and the task can end there. Only take more than 1 turn if:

- The topic is interesting/involved and requires the assistant to take more than 1 turn in order to be helpful such as when it is necessary to ask clarifying questions
- **OR** if following up with additional turns is a good chance to test the model's capabilities.

  

---

# FAQ

**Q: All 4 completions are the same/All the completions deserve to be rated 7. What should I do?**

**A:** The first thing you can try is to resample some or all the completion once or twice to see if a completion with interesting differences can be generated. Otherwise, it is a sign that the topic/request in the User message is too easy or simple for the model and that the task should be **skipped/declined**. Data from topics that the model is already good at is not helpful for this campaign.

**Q:** **Does the Assistant go by any pronouns?**

**A:** No, it’s not programmed with any pronouns. If the Assistant says that it goes by a pronoun (ex: she/her) in a completion, please label it as an **identity error.**

**Q: What should I do if a completion that is cutoff is selected for the conversation?**

**A**: Tell the model to continue the completion, and the ideal message for the next Assistant turn should be a continuation.

**Q: Should the model provide full code-blocks or code diffs when writing code?**

**A**: Make sure to follow any user instructions in the prompt or model instructions.

  

---

# Glossary

## ASSISTANT

The AI, the expert, the model. We want to guide it to answer questions and requests flawlessly. Counterpart of User.

## COMPARISON

The “rating” part of the tasks—step 1.b: Do a Comparison at Each Assistant Step. Flag any mistakes and rate each completion on this step.

## COMPLETION

The auto-generated responses—count of 4 at each turn—given by Assistant to answer the User input. These responses are what we are comparing in these tasks.

## CUTOFF

May refer to one of two things:

1. Instances where a completion ends suddenly leaving the response unfinished. One of the flag-able Assistant mistakes.
2. Latest point in time for the model’s training data. The model will not have knowledge of events that happened beyond that certain date.

## HALLUCINATION

False information Assistant sometimes produces in completions. We want to catch and correct these by giving completions that contain them low scores.

## TURN

One “User input”-and-”Assistant answer” pair. Aim for 1-3 Turns per task depending on the complexity of the conversation.

## USER

The supposed user in the task’s scenario. Mainly asks the questions. Counterpart of Assistant.