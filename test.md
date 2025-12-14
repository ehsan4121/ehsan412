**[The Agent Factory - Episode 1: Agents, their frameworks and when to
use them]{.mark}**

Think of building an AI agent like building an intelligent robot for a
specific job.

**1. What is an AI Agent?**

An **AI Agent** is an innovative program that can reason, make a plan,
and use tools to accomplish a goal on its own. It\'s not just a simple
chatbot that gives pre-written answers.

- **The Brain:** A Large Language Model (LLM) that does the thinking and
  planning.

- **The Memory:** Keeps track of the conversation and what it has done
  so far.

- **The Hands:** \"Tools\" (like other software functions) can be used
  to take action.

**Example: A Customer Support Agent**

- **Goal:** Solve a customer\'s shipping problem.

- **The Plan:** 1) Identify the customer. 2) Check the order status in
  the database. 3) Communicate the solution.

- **In Action:**

  - The agent finds the customer\'s order (uses a **tool** to search the
    database).

  - The database says \"shipping delayed\" but not why. The agent
    **reasons** that this isn\'t enough information.

  - It then uses another **tool** to check the shipping carrier\'s
    website.

  - The carrier\'s site says \"Weather delay.\" The agent uses this new
    information to **replan** and tell the customer about the delay and
    offer a solution.

**What is NOT an Agent?**\
A simple FAQ chatbot that finds a pre-written answer when you type
\"return policy\" is **not** an agent. It doesn\'t reason or use tools;
it just reacts.

------------------------------------------------------------------------

**2. Why Use an Agent Framework?**

You could build an agent from scratch, but it\'s complex. A
**framework** is like a pre-built workshop with all the tools and
instructions you need.

- **It Manages State:** It helps the agent remember its goal and what it
  has already done, so it doesn\'t get lost or forget what it\'s doing.

- **It Provides Observability:** It gives you a \"window into the
  agent\'s brain\" so you can see its thought process and debug it when
  it makes a mistake.

**Example:** Building a complex piece of furniture. You *could* try with
just a screwdriver, but it\'s much easier and faster if you have the
instructions and all the right tools (a framework) in one box.

------------------------------------------------------------------------

**3. Key Frameworks Discussed**

The podcast compares different \"workshops\" (frameworks) you can use:

  --------------------------------------------------------------------------------
  **Framework**   **Simple      **Best For**          **Example**
                  Analogy**                           
  --------------- ------------- --------------------- ----------------------------
  **LangChain**   A **Big Box   Building predictable, A system that finds
                  of Lego®**    step-by-step          information in your
                                workflows.            documents and summarises it
                                                      (a RAG system).

  **LangGraph**   A **Flowchart Building agents that  The customer support agent
                  Maker**       need to make          from our example had to
                                decisions, loop, and  adapt their plan.
                                re-plan.              

  **CrewAI**      A **Company   Systems with multiple A \"marketing crew\" with a
                  Org Chart**   specialised agents    Writer Agent, a Designer
                                that work together.   Agent, and an Analyst Agent
                                                      collaborating on a campaign.

  **Google ADK**  An **Assembly Taking an agent and   Adding a user interface,
                  Line**        making it secure,     connecting to secure company
                                scalable, and ready   data, and deploying it to
                                for real-world use.   handle thousands of
                                                      customers.
  --------------------------------------------------------------------------------

------------------------------------------------------------------------

**4. Multi-Agent Systems**

This is when you have multiple AI agents working together, each with a
special role.

**Example:** Instead of one agent trying to do everything, you could
have:

- **Researcher Agent:** Finds information online.

- **Writer Agent:** Writes a report based on that information.

- **Reviewer Agent:** Checks the report for quality.

This is often more efficient than a single, overwhelmed agent.

------------------------------------------------------------------------

**5. Core Tips for Building Good Agents**

1.  **Start Simple:** Don\'t try to build an agent that can do
    everything. Solve one clear problem first (e.g., \"an agent that
    checks the weather\").

2.  **Focus on Tools:** An agent is only as good as the \"hands\" you
    give it. Make sure its tools (like database connections or
    calculators) work reliably.

3.  **Iterate and Observe:** You won\'t build a perfect agent on the
    first try. Use frameworks that let you see what the agent is
    thinking so you can improve it.

In short, an **AI Agent** is a goal-oriented, reasoning program that
uses tools. **Frameworks** are toolkits that make it easier to build,
debug, and deploy for real-world use.

[The Agent Factory - Episode 2: Multi-agent systems, concepts &
patterns]{.mark}

**1. The Big Idea: Single Agent vs. Multi-Agent System**

Think of an AI agent as an intelligent assistant that can reason, plan,
and use tools (like searching the web or writing code).

- **Single Agent:** A **single, overworked employee** who must do
  everything.

  - **Example:** You ask one agent to plan a party. It must research
    recipes, send invitations, and create a playlist. As you give it
    more jobs, it gets overwhelmed and starts making mistakes. It\'s a
    jack-of-all-trades, but master of none.

- **Multi-Agent System:** A **specialised team** where each member has a
  specific job.

  - **Example:** To plan that party, you hire a team:

    - A **Caterer Agent** to handle the food.

    - A **Planner Agent** to send invites.

    - A **DJ Agent** to create the playlist.

  - **Benefit:** This team is more efficient, makes fewer mistakes, and
    can handle complex tasks much better.

**2. [Context Engineering]{.mark}: The Agent\'s \"[Short-Term
Memory]{.mark}\"**

AI doesn\'t have infinite memory. Its \"[context window]{.mark}\" is
like a **small, precious whiteboard** it can use to think. \"[Context
engineering]{.mark}\" is the art of managing what information you put on
that whiteboard.

The podcast mentions three main strategies:

- **Isolation:** Only giving an agent the information it *needs* for its
  specific job.

  - *Example:* When you ask the **DJ Agent** to make a playlist, you
    only give it information about music genres and the guest list. You
    don\'t distract it with details about the potato salad recipe.

- **Persistence (Memory):** Letting the agent remember past
  conversations.

  - *Example:* The next time you ask the **Planner Agent** to organise
    an event, it remembers that you always forget to order napkins and
    reminds you.

- **Compression (Summarisation):** Shortening long pieces of information
  to save space.

  - *Example:* Instead of pasting a 10-page article, the **Researcher
    Agent** summarises the key points into a few sentences before
    passing it to the **Writer Agent**.

**3. Multi-Agent Patterns: How the Team is Organised**

This is like designing your team\'s \"org chart.\" The podcast describes
several patterns:

**A. With a Supervisor (The \"Manager\" Model)**

A boss agent coordinates the team.

- **Router Supervisor:** The manager talks to workers **one at a time**,
  in a dynamic order.

  - *Example:* A **Research Supervisor** gets a task. It first asks the
    **Researcher Agent** to find information. Then it passes those
    findings to the **Writer Agent** to create a summary. If the summary
    isn\'t good, it goes back *only* to the Writer to fix it.

- **Parallel Supervisor:** The manager delegates tasks to multiple
  workers **at the same time**.

  - *Example:* A **Market Research Supervisor** needs a report. It
    *simultaneously* asks the **Data Agent** for sales numbers, the
    **News Agent** for recent headlines, and the **Social Media Agent**
    for public opinion to speed things up.

**B. Deterministic Flows (The \"Assembly Line\" Model)**

The process is more predictable and predefined.

- **Sequential Flow:** Agents work in a strict, one-after-the-other
  sequence.

  - *Example:* Agent A (researcher) finds data → passes it to Agent B
    (writer) who writes a report → passes it to Agent C (designer) who
    makes it look pretty.

- **Circular Flow:** Agents work in a loop for refinement.

  - *Example:* A **Coder Agent** writes code → passes it to a **Tester
    Agent** → if the test fails, it goes back to the **Coder** to fix
    it. This loop continues until the code passes the test.

**C. The Swarm (The \"Group Chat\" Model)**

There is no single boss. All agents can talk to each other directly.

- **How it works:** It\'s like a group chat of brilliant experts.

- **Upside:** Very flexible. If one agent gets stuck, another can jump
  in to help.

- **Downside:** Can get chaotic, like a meeting with no leader where
  people start arguing about side topics (like what to order for lunch
  instead of finishing the report).

------------------------------------------------------------------------

**4. Observability: How to Debug Your Team**

When your AI team is running, especially in the cloud, you need a way to
see what\'s happening.

- **The Concept:** You need to **log and trace every decision**.

- **The Tool:** Use tools like **[Cloud Trace Explorer]{.mark}**.

- **The Analogy:** A \"**trace**\" is like the complete story of one
  request (e.g., \"[Book a trip]{.mark}\"). \"**Spans**\" are the
  individual chapters of that story (e.g., \"Find Flights,\" \"Book
  Hotel,\" \"Rent Car\"). This lets you see exactly which agent did what
  and why, making it easy to find and fix problems.

**Simple Summary**

The main takeaway is that for simple tasks, a single AI agent is fine.
But for complex jobs, it\'s better to build a **team of specialised AI
agents** and manage them using patterns like a \"manager\" or an
\"assembly line.\" You also must be smart about what each agent
remembers and use debugging tools to watch how the team works together.

######### [The Agent Factory - Episode 3: Building custom tools for agents]{.mark}

Imagine you\'re building a super-smart robot assistant (an
**[Agent]{.mark}**). This robot has an extraordinary brain ([the AI
model]{.mark}), but it\'s stuck in a room with no way to interact with
the outside world. **[Tools]{.mark}** are the arms, legs, and special
gadgets we give this robot so it can do jobs for us.

**1. What is an Agent?**

An **Agent** is an AI program that doesn\'t just answer questions---it
*does jobs*. You give it a big goal, and it figures out the steps needed
to accomplish it.

- **Simple Explanation:** It\'s like a personal assistant. You don\'t
  tell it *how* to do everything; you tell it *what* you want done.

- **Example:** Instead of asking, \"What\'s the weather?\" and then
  asking, \"What\'s the traffic?\", you tell the agent: **\"Get me to my
  meeting on time.\"** The agent will then check the weather, check
  traffic, book you an Uber, and send a message to your boss if you\'re
  running late by itself.

**2. What are Custom Tools?**

**Tools** are the specific skills or abilities we give to an agent so
they can interact with data, software, and the real world. **[Custom
Tools]{.mark}** are skills you build specifically for your agent\'s
unique job.

- **Simple Explanation:** You\'re teaching your robot assistant a new
  skill that only your team needs.

- **Example:** A general agent might know how to search the web. But if
  you work in finance, you might build a custom tool that lets your
  agent **\"Check my company\'s private stock portfolio.\"** This is a
  skill no other agent has.

**3. Why are Tools Needed? (The \"Stale Data\" Problem)**

Agents are trained on old data. If you ask one about today\'s news or
your personal files, they won\'t know. Tools give it a \"live
connection\" to the world.

- **Simple Explanation:** It\'s like using a 2023 map to navigate
  in 2025. You\'ll get lost! Tools are like giving your agent a live
  GPS.

- **Example:** If you ask an agent without tools, \"What is the current
  price of Apple stock?\", it might guess based on old data. An agent
  *with* a tool can use a live financial API to give you the exact,
  current price.

------------------------------------------------------------------------

**The Different \"[Power Levels]{.mark}\" of Tools**

The video explains that not all tools are the same. You pick the right
one for the job.

**Tool Type 1: The Simple Function Tool**

This is for a quick, single action, like looking up one piece of
information.

- **Example:** A get_stock_price tool. You give it a stock name (e.g.,
  \"Tesla\"), and it returns the current price. It\'s fast and simple.

**Tool Type 2: The Specialist Agent Tool (\"[Agent as a
Tool]{.mark}\")**

Sometimes a task is too complex for a straightforward function. So, you
create a *mini-agent* that is an expert at one thing, and you give *that
mini-agent* to your leading agent as a tool.

- **Example:** The user says, **\"Analyse my portfolio and plot its
  growth.\"** This is too open-ended for a simple function.

  - You create a specialist **\"Financial Analyst Agent\"** whose only
    job is to write and run Python code to analyse data and create
    charts.

  - You then give this specialist agent to your leading agent as a tool.
    So, when the primary agent sees \"[plot its growth]{.mark},\" it
    hands that task off to its specialist \"[Financial Analyst]{.mark}\"
    tool.

**Tool Type 3: The Heavy-Duty External Service Tool (MCP)**

This is for tasks that are very heavy and complex, like running a
scientific simulation. You build this as a separate program on another
server and give the agent a \"universal plug\" (called MCP) to connect
to it.

- **Example:** A **\"Portfolio Optimiser\"** that runs a \"Monte Carlo
  simulation\" (a very complex calculation) to recommend the best stocks
  to buy. It\'s too heavy to run inside the agent, so it runs as a
  separate service that the agent can call when needed.

**Tool Type 4: The Secure Authenticated Tool**

This is for actions that need to be safe and secure, like making
purchases or accessing private data. The tool handles login and security
checks.

- **Example:** A buy_stock tool. Before it buys anything, it checks if
  the user is logged in. If not, it asks for a password. Once confirmed,
  it safely executes the trade.

------------------------------------------------------------------------

**Helpful Concepts for Developers**

The video also mentioned some things that make building these agents
easier:

- **OpenAPI Toolset:** If you have a large website or API with dozens of
  features, you don\'t have to build a tool for each one manually. You
  can give the agent the API\'s instruction manual (the **OpenAPI
  spec**), and it will automatically understand all the available
  actions.

- **Long-Running Tools:** For tasks that take a long time (like
  rendering a video), you can give the agent a tool that starts the job
  and then \"pauses\" the conversation until the job is done, so the
  agent isn\'t stuck waiting.

**Summary with a Final Example**

Let\'s combine everything into the example from the video:

**User Prompt:** *\"Analyse my portfolio\'s performance, plot it,
recommend better stocks, check the price of the top one, and if I say
yes, buy 10 shares.\"*

The **Main Agent** breaks this down and uses its custom tools:

1.  It uses its **Specialist Agent Tool** (the financial analyst) to run
    code, analyse, *and plot* the portfolio.

2.  It uses its **Heavy-Duty Service Tool** (the portfolio optimiser) to
    *recommend better stocks*.

3.  It uses its **Simple Function Tool** (get stock price) to *check the
    price* of the top recommended stock.

4.  It uses its **Secure Authenticated Tool** (execute trade) to *buy
    the shares* after getting user approval.

By giving the agent this **custom toolkit**, it transforms from a
chatbot that can only talk into a powerful assistant that can do *work*.

[The Agent Factory - Episode 4: Remember me, memory in agents]{.mark}

**1. The Problem: The \"[Goldfish]{.mark}\" Agent**

Imagine you tell a chatbot, \"My name is Alex, and I love pineapple on
pizza.\" A minute later, you ask, \"What\'s my name?\" A basic agent
without memory would say, \"I don\'t know.\" It forgets everything from
one interaction to the next.

- **Why?** Each time you chat, it starts with a blank slate. There is no
  way to remember past conversations.

**2. The Solution: Building Memory for Agents**

The solution involves two main types of memory:

**A) Short-Term Memory (The \"Session\")**

This is like remembering the details of a single, ongoing conversation.

- **What it is:** The agent keeps a log of everything said in the
  current chat session. When you ask a question, it looks back at the
  recent conversation to find the answer.

- **Example:** In a long chat about planning a trip, you can ask, \"What
  was the hotel I liked?\" and the agent can check the session history
  to tell you.

- **The Limitation:** As the chat gets very long, it can get slow,
  expensive, and messy. More importantly, if you start a **new chat
  tomorrow**, the session is empty, and the agent forgets who you are.

**B) Long-Term Memory (The \"Memory Bank\")**

This is the real breakthrough. It\'s like the agent\'s personal diary or
brain, where it saves essential facts about you across *all* your
conversations.

- **What it is:** A special system that automatically reads
  conversations, picks out the most important facts (like your name,
  your preferences, your goals), and stores them in a \"Memory Bank\"
  for the long run.

- **Example:**

  - **Monday:** You tell the agent, \"I\'m allergic to shellfish.\"

  - **Friday:** You ask, \"Find me a good dinner recipe.\" The Memory
    Bank automatically reminds the agent of your allergy. The agent then
    suggests a pasta dish instead of a shrimp scampi.

**How the \"Memory Bank\" Works (The Cool Part)**

The Memory Bank doesn\'t just save your entire chat history. It\'s
smarter than that. It does two key things:

1.  **Memory Extraction:** It uses a powerful AI (like Gemini) to read
    the conversation and pull out only the most valuable bits.

    - **It looks for:** Your preferences (\"loves cats\"), facts about
      you (\"is a developer\"), key events (\"is planning a trip to
      Japan\").

2.  **Memory Consolidation:** It constantly cleans up the Memory Bank to
    avoid duplicates and contradictions.

    - **Example:** If you say \"My favourite colour is blue\" on Tuesday
      and then \"I love the colour green\" on Thursday, the Memory Bank
      will **update** the old memory. It won\'t have two conflicting
      memories. It keeps only the most recent, relevant information.

------------------------------------------------------------------------

**Simple Analogy: A Helpful Personal Assistant**

- **Agent without Memory:** A new, temporary intern every day. You must
  re-explain everything from scratch.

- **Agent with Short-Term Memory:** An assistant for the day. They
  remember what you talked about this morning, but if you call them
  tomorrow, they\'ve forgotten you.

- **Agent with a Memory Bank:** A lifelong personal assistant. They have
  a notebook where they jot down your essential likes, dislikes, and
  history. Every time you talk to them, they check that notebook to give
  you personalised help, no matter how much time has passed.

------------------------------------------------------------------------

**Key Difference: Memory Bank vs. RAG**

This is a crucial point from the text:

- **RAG ([Retrieval-Augmented Generation]{.mark}):** Is for **external
  knowledge**. It\'s like giving the agent access to a company\'s
  library or manual.

  - **Example:** An agent that can answer questions about your
    company\'s HR policy by looking it up in the employee handbook.

- **Memory Bank:** Is for **internal, personal knowledge**. It\'s about
  what the agent *learns about you* through your conversations.

  - **Example:** The agent remembers that *you*, specifically, are
    planning a vacation and what your budget is.

**Putting It All Together: A Final Example**

Let\'s see how an agent with a Memory Bank would work in practice:

- **Conversation 1:**

  - **You:** \"Hi, I\'m Sam. I\'m a gardener and I\'m trying to grow
    tomatoes.\"

  - **Agent:** (Uses its Memory Bank, sees it\'s a new user, no memories
    yet. It helps you and, in the background, saves the memories:
    \"User\'s name is Sam\", \"Profession: Gardener\", \"Current
    project: Growing tomatoes\").

- **Conversation 2 (a week later):**

  - **You:** \"My tomato leaves are turning yellow. What\'s wrong?\"

  - **Agent:** (Before it answers, it uses the Memory Bank\'s
    \"Preload\" tool. The Bank provides the relevant memories: \"User:
    Sam\", \"Current project: Growing tomatoes\").

  - **Agent\'s Response:** \"Hi Sam! Sorry to hear about your tomato
    plants. Since you\'re growing tomatoes, yellow leaves could be due
    to\...\" **(The agent personalised the response because it reminded
    you of your project).**

[The Agent Factory - Episode 5: Tackling the most challenging questions
in agent development with]{.mark}

**What is an AI Agent?**

Think of a simple AI chatbot (like ChatGPT) as a very knowledgeable but
passive librarian. You ask a question, and it gives an answer based on
its training.

An **AI Agent** is like a proactive personal assistant. You give it a
big goal, and it doesn\'t just answer, it *acts*. It can use tools,
browse the web, write code, and make decisions to accomplish the task
for you.

**Example:**

- **Simple AI:** You ask, \"What\'s the weather in Tokyo?\" It tells you
  based on its old data.

- **AI Agent:** You command, \"Plan a 3-day trip to Tokyo for me.\" The
  agent could then:

  1.  Use a **tool** (Google Search) to find the best attractions.

  2.  Use another **tool** (a booking API) to check flight and hotel
      prices.

  3.  Write a summary and email it to you.

------------------------------------------------------------------------

**Key Concepts Explained**

**1. Models (The \"[Brain]{.mark}\" of the Agent)**

This is the core AI, like Gemini, GPT, or Claude. The podcast highlights
**[Gemini]{.mark}** for its specific strengths:

- **[Large Context Window]{.mark} (1 million tokens):** It can read and
  understand a *vast* amount of information at once.

  - \*Example: You could give it a 500-page manual and a user\'s
    question, and it can find the relevant answer without getting
    confused. \*

- **[Multimodality]{.mark}:** It can understand different types of input
  not just text, but also images, audio, and video.

  - *Example: You could show it a picture of a broken engine part, and
    it could diagnose the problem and suggest fixes.*

- **\"Time to Think\" ([Reasoning]{.mark}):** Newer models can spend
  more computational \"time\" to reason through complex problems,
  leading to better answers.

**2. Open vs. Proprietary Models**

- **Proprietary (like Gemini):** You access it through an API (like a
  subscription service). It\'s easy to start, powerful, and you don\'t
  manage the hardware.

  - *Analogy: Like renting a powerful supercomputer by the minute.*

- **Open Models (like Gemma):** You can download and run them on your
  own computer. This is good for privacy, specific customization, or
  environments with no internet.

  - *Analogy: Owning and maintaining your own car. More control, but
    you\'re responsible for gas and repairs.*

**The podcast\'s advice: Start with a proprietary API (like Gemini) to
quickly test your idea, then consider open models if you have specific
needs like privacy or customisation.**

**3. Function Calling / Tool Use**

This is how the agent interacts with the world. It\'s a way to force the
AI to output a structured command (like a JSON object) instead of just
text.

- \*Example: You ask the agent, \"What\'s the population of Tokyo?\"
  Instead of just answering, the agent outputs a structured command: {
  \"tool\": \"google_search\", \"query\": \"Tokyo population 2024\" }.
  Your program then executes this search and feeds the results back to
  the agent.

**4. Agentic Frameworks (The \"Workflow Manager\")**

Building an agent from scratch is complex. Frameworks like
**[LangGraph]{.mark}** or **[CrewAI]{.mark}** provide pre-built
structures to manage the agent\'s workflow, memory, and tool use.

- *[Analogy]{.mark}: If the AI model is the chef, the framework is the
  kitchen, recipes, and kitchen tools that help the chef prepare a
  complex meal efficiently.*

**5. Context Engineering**

This is the modern version of \"[prompt engineering]{.mark}.\" It\'s not
just about the initial question, but about strategically giving the
agent the *correct information* and the *right tools* at the *right
time* throughout a conversation.

- *Example: For a customer support agent, you wouldn\'t just give the
  user\'s question. You\'d also provide the user\'s purchase history,
  previous support tickets, and the knowledge base articles all as
  \"context\" to help it give a personalised and accurate answer.*

**6. Evaluation**

This is one of the biggest challenges. How do you know if your agent is
working well? Unlike traditional software that is deterministic (1+1
always equals 2), AI agents are non-deterministic (the same question
might get slightly different answers).

- *Example: You need to constantly test your agent with a set of example
  questions and have a way to score the answers, often using another AI
  as a \"judge,\" to ensure it\'s performing reliably.*

**7. The [Gemini CLI]{.mark} (Command Line Interface)**

This is a practical tool that acts like an AI coding partner that lives
in your computer\'s terminal. It can help you write code, debug, update
documentation, and more, all by understanding your commands in natural
language.

- *Example: Instead of manually searching through code, you could tell
  the CLI: \"Find all places in this project where we call the payment
  API and update the error handling.\" It would then propose and even
  make those changes.*

**A Simple Analogy to Tie It All Together**

Imagine building a **Self-Driving Car Agent**:

- **The Model (Gemini)** is the car\'s **brain**, processing what it
  sees.

- **The Large Context Window** means it can see far down the road and
  remember the last few minutes of driving.

- **Multimodality** means it can understand data from cameras, LiDAR,
  and microphones.

- **Function Calling / Tool Use** is how the brain tells the **wheels**
  to turn and the **brakes** to press.

- **An Agentic Framework (LangGraph)** is the **nervous system** that
  manages the loop: See -\> Think -\> Act -\> See again.

- **Context Engineering** provides the brain with a map, traffic rules,
  and the destination.

- **Evaluation** is the rigorous testing in simulators and on closed
  tracks to make sure it drives safely before hitting the real road.

[The Agent Factory - Episode 6: The Impossible Computing with Keith
Ballinger]{.mark}

**What is an \"AI Agent\"?**

Think of a regular AI chatbot (like asking a question to an intelligent
assistant). It gives you an answer, and that\'s the end of the
conversation.

An **AI Agent** is like a super-powered version of that. It\'s an AI
that doesn\'t just answer a question; it *acts*. You can give it a big
goal, and it will break that goal down into steps, use different tools,
and complete the task for you.

- **Simple AI:** You ask, \"How do I make a website?\" It gives you a
  list of instructions.

- **AI Agent:** You tell it, \"Build me a simple website for my
  bakery.\" The agent might then write the code, create the design, and
  even set up the online hosting, all by itself.

**The Key Concepts Explained**

**1. [Impossible Computing]{.mark}**

This is the main idea that AI agents are making things possible that
were once too hard, time-consuming, or required specialised skills for
most people.

- **Simple Explanation:** Turning \"I could never do that\" into \"I
  just did that!\"

- **Example from the text:** Keith wanted to create a new programming
  language. This is a massive, complex project. With the help of AI
  agents, he was able to build it in his spare time, something that
  would have been \"impossible\" for one person to do quickly before.

**2. [Vibe Coding]{.mark}**

This is a fun, informal way to describe building software with an AI
agent. Instead of writing every single line of code yourself, you
describe what you want in plain English, and the AI agent writes the
code for you. You then \"vibe\" with giving feedback, making changes,
and iterating until it\'s right.

- **Simple Explanation:** \"Telling\" a computer what to build instead
  of \"typing\" the instructions letter by letter.

- **Example from the text:** Keith demonstrates this by asking an AI to
  build a \"command-line markdown viewer.\" He describes the features he
  wants (like syntax highlighting and paging), and the AI writes all the
  code, creates a user guide, and sets up the project files.

**3. Developer as an \"Orchestrator\" or \"Conductor\"**

This is a key point about how the job of a software developer is
changing.

- **Simple Explanation:** Instead of being the musician who plays every
  instrument, you become the **conductor** who leads the orchestra.

- **Example:** Imagine you\'re building a new app. You don\'t have to
  write the code for the login screen, the database, or the payment
  processing yourself. Instead, you \"conduct\" several AI agents:

  - You tell one agent, \"Design a secure login system.\"

  - You tell another, \"Set up a database to store user profiles.\"

  - Your job is to have an overall vision and make sure all these pieces
    work together harmoniously.

**4. Job Change, Not Job Displacement**

The podcast argues that AI won\'t necessarily take developers\' jobs,
but it will change them.

- **Simple Explanation:** Just like calculators didn\'t make accountants
  obsolete (it just changed their work), AI agents will change what
  developers do.

- **Example:** In the past, a developer might have spent hours writing
  basic, repetitive code. Now, an AI can do that. The developer\'s time
  is freed up to focus on more complex problems, like the overall design
  of the system, the user experience, and solving unique business
  challenges. The skill shifts from *writing code* to *designing and
  directing*.

**5. Context Engineering**

This is the most essential skill for working with AI agents effectively.
It\'s about giving the AI the correct information at the right time.

- **Simple Explanation:** You can\'t just give an AI agent a
  one-sentence command for a complex task. You must carefully manage the
  information you give it, just like you would with a new human team
  member.

- **Example:** If you want an AI agent to help fix a bug in a large,
  existing software project, you wouldn\'t dump the entire million-line
  codebase on it at once. That would overwhelm it. Instead, you\'d be a
  sound \"[context engineer]{.mark}\" by:

  1.  First, give it a high-level overview of how the project works.

  2.  Then, point it to the specific files that are related to the bug.

  3.  Finally, explain the exact problem you\'re seeing.

**Summary**

The core message is that **AI Agents are potent tools that can act like
a team of assistants**, taking high-level goals and making them happen.
This makes complex tasks feel \"impossible\" and changes our role from
\"doors\" to \"directors.\" The key to success is learning how to
communicate with them effectively through sound \"context engineering.\"

[The Agent Factory - Episode 7: Gemini CLI with Taylor Mullen]{.mark}

**1. What is Gemini CLI?**

**Simple Explanation:** It\'s an intelligent assistant that lives in
your computer\'s command line (the text-based interface where developers
and tech-savvy users type commands).

- **Analogy:** Imagine you have a super-knowledgeable coworker sitting
  inside your computer\'s terminal. Instead of searching the web or
  reading long documents yourself, you can ask this coworker to do it
  for you.

- **Example from the text:** The host, Molly, doesn\'t manually clone a
  code repository from GitHub. She types a command like, clone the
  Google ADK Python repo from GitHub, and the Gemini CLI does all the
  steps to find and download it for her.

------------------------------------------------------------------------

**2. The Agentic Loop**

**Simple Explanation:** This is the \"[thought process]{.mark}\" the AI
uses. It doesn\'t just answer; its *reasons* about a problem, uses tools
to get information, and checks back with you before taking significant
actions.

- **Analogy:** It\'s like a detective solving a case.

  1.  **Reason:** \"I need to find the suspect\'s address.\"

  2.  **Use a Tool:** They look up the address in a database.

  3.  **Act & Check:** They find the address and then say to their
      partner, \"I found it at 123 Main Street. Should we go there
      now?\"

- **Example from the text:** When cloning the repo, the CLI first
  *searched the web* to find the correct link, then *asked for
  permission* before running the git clone command.

------------------------------------------------------------------------

**3. Massive Context Window (1 million Tokens)**

**Simple Explanation:** A \"[context window]{.mark}\" is the AI\'s
short-term memory. A huge 1-million-token window means it can read and
understand a massive amount of information at once.

- **Analogy:** A person with a small memory can only read one paragraph
  of a book at a time. A person with a massive memory can read the
  entire book in one sitting, giving them a much better understanding of
  the whole story.

- **Example from the text:** Instead of just reading a README.md file,
  the Gemini CLI can analyse an *entire codebase*---all the folders,
  code files, and documentation---at once to give a complete project
  overview.

------------------------------------------------------------------------

**4. MCP Servers (Model Context Protocol)**

**Simple Explanation:** These are like **plugins or apps** you can
install to teach the Gemini CLI new skills. They let it connect to other
tools and services.

- **Analogy:** Your smartphone can\'t do much out of the box. But when
  you install apps, you can call a car, order food, or edit photos. MCP
  servers are the \"apps\" for Gemini CLI.

- **Example from the text:** They used a **Google Docs MCP server**.
  This taught the CLI how to interact with Google Drive. So, after the
  AI analysed a codebase, they could command it to \"save that summary
  to my Google Drive,\" and it knew exactly how to do it.

------------------------------------------------------------------------

**5. Custom Slash Commands**

**Simple Explanation:** This lets you save long, complex instruction as
a simple, reusable command.

- **Analogy:** It\'s like creating a \"macro\" or a \"quick dial\"
  number. Instead of giving your friend a long list of directions to
  your house every time, you save it as \"Home\" in their GPS.

- **Example from the text:** One host created a very detailed prompt for
  analysing research papers. Instead of copying and pasting that huge
  prompt every time, he saved it as command called /research_digest.
  Now, whenever he drops a new PDF into a folder, he types that one
  command to get a beautifully formatted summary.

------------------------------------------------------------------------

**6. Self-Healing & Proactive Problem Solving**

**Simple Explanation:** The AI doesn\'t just give up if it hits a
roadblock. It tries to find another way and tells you the steps it wants
to take.

- **Analogy:** You ask a friend to book you a flight, but the website is
  down. A simple tool might say, \"I failed.\" A self-healing agent
  would say, \"That airline\'s site is down. I can try a different
  airline or a travel aggregator site. Is it okay if I do that?\"

- **Example from the text:** When asked to deploy a website (which it
  couldn\'t do directly), the CLI figured out it could create a GitHub
  repository, use a feature called GitHub Pages to host the site, and
  then provide the link---a creative solution the user hadn\'t even
  considered.

**In a Nutshell**

The main idea of **Gemini CLI** is to have an AI assistant that works
the way a thoughtful human would: it uses tools, remembers a lot of
contexts, asks for permission, and finds clever workarounds, all from
the convenience of your keyboard.

[The Agent Factory - Episode 8: Agent payments, can you do my
shopping?]{.mark}

**The Main Problem: Trusting an AI with Your Money**

Imagine you tell a super-smart assistant, \"Go online and buy me two
concert tickets for under \$200.\" Right now, you\'d be nervous because:

- What if it buys 200 tickets by mistake?

- What if it uses your credit card to buy something else?

- Who do you blame if it makes a mistake?

This \"[crisis of trust]{.mark}\" is what the **[Agent Payment
Protocol]{.mark}** is designed to solve.

------------------------------------------------------------------------

**Key Concept 1: Specialised Roles (The Team of Helpers)**

Instead of one AI doing everything, the protocol uses a team where each
member has a specific job. This is called a **[role-based
ecosystem]{.mark}**.

**Example: Buying Concert Tickets**

- **The Shopping Agent ([The Personal Shopper]{.mark}):** This is the AI
  you talk to. Its job is to find the best tickets that match your
  request. It\'s excellent at shopping, but it **never sees your credit
  card number**.

- **The Credential Provider (The Secure Wallet):** This is like a
  digital vault (e.g., PayPal or a bank app). It safely stores your
  payment methods and address. When it\'s time to pay, the Shopping
  Agent asks the Wallet to pay, but only the Wallet handles the actual
  card details.

- **The Merchant (The Seller):** This is the website or API of the
  ticket seller.

- **[The Merchant Payment Processor]{.mark} (The Cashier):** This is a
  specialised system that talks to banks to finalise the payment. It\'s
  the only one, besides your Wallet, that sees the full payment details.

**Why this is great:** By separating the jobs, your \"[Personal
Shopper]{.mark}\" can be an expert at finding deals without being a
security risk.

**Key Concept 2: Verifiable Credentials ([The Digital Permission
Slips]{.mark})**

This is the most important innovation. These are cryptographically
signed digital documents that act as unforgeable permission slips.

There are three main types:

1.  **Cart Mandate (The \"[Final Checkout]{.mark}\" Slip):**

    - **When:** You are present and reviewing the purchase.

    - **How it works:** The AI shows you the final cart (e.g., \"[2
      tickets for Taylor Swift]{.mark}, Section 101, total \$190\"). You
      click \"[Approve]{.mark},\" and this creates a signed digital
      mandate. It\'s like a legally binding \"[Yes, I want exactly
      this]{.mark}.\"

    - **Example:** It\'s the digital version of looking at your cart on
      Amazon and clicking \"[Place Order]{.mark}.\" You can\'t later
      claim you didn\'t want those exact items.

2.  **Intent Mandate (The \"Go Do This for Me\" Slip):**

    - **When:** You are **not** present and want the AI to act on its
      own.

    - **How it works:** You give pre-approval for a specific goal. \"Buy
      two concert tickets for under \$200 as soon as they go on sale.\"
      You sign this intent upfront.

    - **Example:** It\'s like telling your friend, \"Here\'s my credit
      card. If you see the new video game for less than \$50, buy it for
      me.\" Your friend has permission to act, but only within the rules
      you set.

3.  **Payment Mandate (The \"[Agent Was Here]{.mark}\" Slip):**

    - **What it is:** This tells the bank and payment networks that an
      AI agent was involved in the transaction, and whether a human was
      present or not. This adds a layer of visibility for everyone.

------------------------------------------------------------------------

**How It All Works Together: The \"Contractual Conversation\"**

Let\'s walk through the concert ticket example using the \"Intent
Mandate\" (since you\'re not online when the tickets go on sale).

1.  **You Give the Task:** You tell your Shopping Agent, \"Buy two
    tickets under \$200 when they\'re available.\"

2.  **Agent Shops:** The agent finds the tickets on the merchant\'s
    website and prepares a cart.

3.  **Agent Calls the Wallet:** The agent tells your Credential Provider
    (Wallet), \"I need to pay for this. What payment methods does the
    user have?\"

4.  **You Pre-Approve (Earlier):** You had already signed an **[Intent
    Mandate]{.mark}** giving the agent permission for this kind of
    purchase.

5.  **Agent Checks Out:** The agent sends your signed Intent Mandate to
    the merchant. The merchant sees this unforgeable permission slip and
    knows it\'s a legitimate order.

6.  **Payment Happens Securely:** The merchant sends the payment request
    to the Payment Processor, which works with your Wallet to finalise
    the transaction. Your credit card is charged, and you get the
    tickets!

**Summary: Why This Matters**

- **Security:** Your payment info is safe with specialised providers
  (Wallets and Processors), not with every AI you use.

- **Trust:** The digital permission slips ([Verifiable
  Credentials]{.mark}) create a clear record of what you approved,
  preventing misunderstandings.

- **Accountability:** If something goes wrong, it\'s clear who is
  responsible. If you approved a cart, it\'s on you. If the merchant
  sent the wrong item, it\'s on them.

In short, the Agent Payment Protocol is like building a secure,
well-defined team and a system of signed contracts so that you can
finally trust an AI to do your shopping without worrying it will buy a
lifetime supply of rubber duckies!
