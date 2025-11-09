# 🔢 React Hook Form Number Input Fix — with shadcn/ui + Tailwind CSS v4

A minimal example demonstrating how to handle number inputs correctly in **React Hook Form** using **shadcn/ui** and **Tailwind v4** — ensuring numeric values aren’t submitted as strings.  

---

## 🚀 Overview

Even if your input type is `"number"`, browsers still submit its value as a **string**.  
That can cause type issues, validation errors, or incorrect calculations down the line.

This repo shows how to fix that cleanly using:

- 🪄 **React Hook Form**
- 🎨 **shadcn/ui**
- 💨 **Tailwind CSS v4**
- ⚡ Type-safe handling with `valueAsNumber`

---

## 🧩 The Problem

```tsx
<input type="number" {...register("age")} />
Looks fine, right?
But this will actually submit:

js
Copy code
{ age: "25" } // ❌ string, not number
✅ The Fix (Controller / FormField Pattern)
tsx
Copy code
<Field data-invalid={fieldState.invalid}>
  <FieldLabel htmlFor="form-rhf-demo-mobile">
    Mobile Number
  </FieldLabel>
  <Input
    {...field}
    onChange={(e) => field.onChange(e.target.valueAsNumber)} // ✅ converts to number
    id="form-rhf-demo-mobile"
    aria-invalid={fieldState.invalid}
    placeholder="Enter your mobile number"
    autoComplete="off"
    type="number"
  />
  {fieldState.invalid && <FieldError errors={[fieldState.error]} />}
</Field>
Here, e.target.valueAsNumber ensures the value stays numeric.

⚙️ Alternative (Using register Directly)
If you’re not using a Controller or custom field component, you can let React Hook Form handle the conversion automatically:

tsx
Copy code
<input
  type="number"
  {...register("age", { valueAsNumber: true })}
/>
🧠 Why This Matters
Prevents numeric values from being sent as strings

Keeps form data consistent and type-safe

Works seamlessly with Zod schemas, APIs, and TypeScript models

Avoids silent bugs in form validation logic

🛠️ Setup
bash
Copy code
# Clone this repo
git clone https://github.com/yourusername/react-hook-form-number-example

# Move into the directory
cd react-hook-form-number-example

# Install dependencies
npm install

# Run the project
npm run dev
🧱 Built With
React Hook Form

shadcn/ui

Tailwind CSS v4

TypeScript

🧑‍💻 Author
Siddhesh Shirdhankar
Frontend Engineer (1.5 YOE)
Follow me on [Medium](https://medium.com/@siddhesh.shirdhankar18) | Connect on [LinkedIn](https://www.linkedin.com/in/siddhesh-shirdhankar-8024871a7/)


💬 “Sometimes, it’s not about complex logic — it’s about knowing how the browser and libraries interact.”
— Inspired by a question from one of my juniors ❤️
