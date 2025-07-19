# prompt-library

These are the prompts I currently use when developing features in partnership with an AI coding tool, usually Cursor or Claude Code.

## Prompt strategy in 3 steps

There are 3 phases to my approach:

### 1. Develop a Product Requirements Document

Example:

>We're building a product described here: @product-context.mdc. We'd like to build a new feature that does... {fill this in with a few sentences describing your feature}. Our first step is to create a Product Requirements Document. Please follow these instructions to develop a document for our new feature: @create-prd.mdc.

Once this generates a PRD, I will review this carefully and manually edit the document. Going slow at this review step is one of the highest leverage moments in the development process, and time spent here will save you time later, so don't rush it! Once I've made all my edits, I make sure the agent knows I have made changes from its last state so it can update its context.

### 2. Develop a task list

Example:

>Ok, I've made some edits to the PRD. Please note them going forward. Now take this PRD and follow the instructions in @generate-tasks.mdc to develop a task list.

Again, this is a high leverage moment, so I review the planned tasks carefully, and often make several edits to the planned tasks.

Note that if we're still in the same context window, there's no need to attach the product requirements document again in subsequent prompts as it's already in context. However if our AI coding assistant goes off the rails, I will usually start a new context window and restate our goals (described below).


### 3. Execute individual tasks

Example:

>Great! We now have a well-defined list of tasks. Please follow the instructions in @process-task-list.mdc and begin on task 1.1.


## What to do when we exhaust our context window or when the agent goes off the rails

I find that as our context grows in size (for example on our 20th turn with agent), the quality of the results start to diminish. It starts to get confused, or repeat past mistakes. This is usually a good sign that it's time for a fresh context window. I will often start a fresh context window pre-emptively when we're at a natural breakpoint in our feature work (e.g. moving from frontend tasks to backend tasks).

However, when we create a new context window The agent no longer has any memory of what product we're building, our product requirements, our task list, or how to process a task, so we must restate each of these.

Example:

>We're building this product: @product-context.mdc. We're following this product requirements document @prd-{my_feature}.md and have completed these tasks so far @tasks-prd-{my_feature}.md. Please follow these instructions @process-task-list.mdc and proceed with task {x.y}.


## Credits

I'd like to thank https://github.com/snarktank/ai-dev-tasks for inspiring this process I use today.
