# AI Chatbot vs AI Agent

A simple explanation with examples.

---

## AI Chatbot = it talks

You ask, it answers. That's all it does.
It only uses what it already knows (plus what you send it).

**Examples**
- You ask "What is Next.js?" and it explains.
- A support bot on a website answering "What are your opening hours?"

---

## AI Agent = it talks AND does things

It can use **tools** (search, database, APIs, sending email), decide the next step, and keep going until the task is finished.

**Examples**
- "Book me a meeting tomorrow." The agent checks the calendar, finds a free slot, creates the event, and tells you it's done.
- "Find all unpaid orders and email the customers." It queries the database, writes the emails, and sends them.

---

## The difference in one line

| Type    | Flow                                                      |
|---------|-----------------------------------------------------------|
| Chatbot | question → answer                                         |
| Agent   | goal → think → use tool → check result → repeat → done    |

---

## Simple analogy

- **Chatbot** is a receptionist who answers your questions.
- **Agent** is an assistant you give a task to, who actually goes and does it.

---

## In code (very simplified)

**Chatbot: one call, one answer**

```ts
const reply = await ai.chat("What is Next.js?");
```

**Agent: a loop with tools**

```ts
const tools = { getOrders, sendEmail };
let done = false;

while (!done) {
  const step = await ai.decide(goal, tools); // AI picks the next action
  if (step.tool) await tools[step.tool](step.input);
  done = step.finished;
}
```

> `ai.chat` and `ai.decide` are placeholder names to show the idea, not a real library.
