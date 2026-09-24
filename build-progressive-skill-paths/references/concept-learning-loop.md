# Concept Learning Loop

Use the same predictable structure for every important concept. Familiar structure reduces learning friction while the work becomes progressively harder.

## Contents

- [Required Why-and-How concept card](#required-why-and-how-concept-card)
- [React example: state and props](#react-example-state-and-props)
- [Practice loop](#practice-loop)
- [Guidance fade](#guidance-fade)
- [Session shape](#session-shape)

## Required Why-and-How concept card

Begin every concept with this card. Do not replace Purpose, Why, or How with a definition alone.

| Field | Required answer |
|---|---|
| **What is it?** | Give a one- or two-sentence plain-language definition. |
| **Purpose** | State the specific job or responsibility the concept exists to perform. |
| **Why do we use it?** | Name the problem it solves, the benefit it provides, and the important trade-off. |
| **How does it work?** | Explain the mechanism, inputs, outputs, lifecycle, and data or control flow. |
| **Underlying fundamental** | Identify the prerequisite, invariant, or durable principle that explains the behavior. |
| **Framework relationship** | When applicable, name what the framework abstracts, the benefit it provides, and where the abstraction can leak. |
| **When do we use it?** | Give recognizable conditions and a realistic use case. |
| **When should we not use it?** | Name a boundary, misuse, or simpler alternative. |
| **Related concepts** | Explain how it differs from or collaborates with adjacent concepts. |

Use concrete language. Replace “X is used for Y” with enough mechanism for the learner to predict behavior.

## React example: state and props

### State

- **What is it?** State is data owned by a React component that can change over time and persist across renders.
- **Purpose:** Hold local, changeable component data that affects what the component renders or how it behaves.
- **Why do we use it?** A normal local variable in a function component does not persist reliably across renders, and changing it does not ask React to render again. State gives React a managed value and an update signal.
- **How does it work?** A hook such as `useState` returns the current value and a setter. Calling the setter schedules an update; React renders the component again with the new state value.
- **Underlying fundamental:** State represents data at a point in time; an event produces a state transition, and the resulting value determines the next output. JavaScript closures, value identity, and immutability affect how React observes those transitions.
- **Framework relationship:** React manages update scheduling and DOM synchronization. The abstraction can leak through direct mutation, stale closures, unnecessary derived state, and misunderstood render timing.
- **When do we use it?** Use it for component-owned values that change through interaction or time, such as an input value, open/closed status, or selected tab.
- **When should we not use it?** Do not store a value that can be calculated directly from current props or other state. Avoid duplicating server or shared application data without a clear ownership reason.

```jsx
function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

### Props

- **What is it?** Props are read-only inputs a parent passes to a child component.
- **Purpose:** Configure a child and pass data, callbacks, or renderable content through the component tree.
- **Why do we use it?** Props make components reusable and keep ownership clear through one-way data flow: the parent owns the value and the child consumes it.
- **How does it work?** The parent supplies JSX attributes. React passes them as an object to the child. The child reads them but does not mutate them; it requests changes through a callback when needed.
- **Underlying fundamental:** Props are function inputs and component contracts. Read-only inputs and explicit ownership make data flow predictable.
- **Framework relationship:** JSX and React's component model package these inputs as props. The abstraction can leak through prop drilling, unstable object identity, or unclear ownership.
- **When do we use it?** Use props when a value or behavior is owned outside the component or when multiple instances need different configuration.
- **When should we not use it?** Do not copy a prop into state unless the component intentionally needs an independent snapshot or editable draft.

```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}</h1>;
}

function App() {
  return <Greeting name="Asha" />;
}
```

### Relationship

The parent can keep a value in **state** and pass that value to a child as **props**. State answers “who owns this changing value?” Props answer “how does another component receive it?”

## Practice loop

### 1. Connect

- State the real problem the concept solves.
- Link it to one prerequisite, underlying invariant, and the target use case.
- If a framework is involved, name the abstraction benefit and one way it can leak.
- Show the result the learner will produce.

### 2. Explain and predict

- Present the Why-and-How concept card.
- Ask the learner to predict behavior before showing the result.
- Pair abstract and concrete representations when useful.

### 3. Demonstrate

- Show one worked example with inputs, decisions, outputs, and checks.
- Make hidden expert decisions visible.
- Include expected output for self-correction.

### 4. Reproduce

- Let the learner repeat a small guided task.
- Keep setup stable and introduce one main new idea.
- Add checkpoints instead of one long instruction list.

### 5. Modify

- Change one meaningful variable, constraint, or requirement.
- Ask for a prediction before running the change.
- Compare the result with the prediction.

### 6. Solve and transfer

- Remove step-by-step guidance.
- Provide acceptance criteria, sample inputs, and a timebox.
- Place the concept inside a realistic scenario with a trade-off or failure condition.
- Require testing and explanation, not only a working output.

### 7. Retrieve and reflect

- Ask the learner to explain What, Purpose, Why, and How without notes after a delay.
- Revisit important ideas over increasing intervals.
- Record what failed, why, what fixed it, and what remains uncertain.

## Guidance fade

Progress from full example to independence:

1. complete worked example;
2. partially completed example;
3. hints only;
4. acceptance criteria only;
5. ambiguous real-world brief;
6. peer teaching, review, or design defense.

If failure comes from missing knowledge, restore one layer of guidance. If it comes from weak recall, use retrieval and another varied example.

## Session shape

1. Recall the previous concept's What, Purpose, Why, and How.
2. Introduce one new concept card.
3. Inspect a worked example.
4. Perform one task.
5. Debug or vary it.
6. Capture evidence.
7. Name the next action.

Favor multiple short cycles over a long theory block followed by delayed practice.
