import { config } from "dotenv";
import { Eko, WorkflowParser } from "@eko-ai/eko";
import { loadTools } from "@eko-ai/eko/nodejs";

// Initialize environment variables
config();

// Load Node.js environment available tools
Eko.tools = loadTools();

async function main() {
  // Initialize Eko
  const eko = new Eko({
    llm: "claude", // Explicitly choose Claude as our LLM
    apiKey: process.env.ANTHROPIC_API_KEY,
  });

  try {
    // Create and execute a simple workflow
    const workflow = await eko.generate(`
      Clean up all files in the current directory larger than 1MB
    `);

    const workflowJson = WorkflowParser.serialize(workflow);
    console.log("Generated workflow:");
    console.log(workflowJson);

    console.log("Executing workflow...");
    await eko.execute(workflow);
    console.log("Done!");
  } catch (error) {
    console.error("Error:", error);
  }
}

await main().catch(console.error);
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
rananisar348/rananisar348 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
