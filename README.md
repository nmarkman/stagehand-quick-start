# Stagehand Quick Start

A project for experimenting with and testing **Stagehand** and **Browserbase** for AI-powered browser automation.

## Purpose

This repository serves as a testing ground for exploring Stagehand's capabilities in web automation, combining the power of Playwright with AI-driven browser interactions through Browserbase's cloud infrastructure.

## What is Stagehand?

Stagehand amplifies Playwright by adding three powerful AI-driven methods to the `Page` class:

- **`act`** - Perform actions on web pages using natural language instructions
- **`extract`** - Extract structured data from web pages with AI assistance  
- **`observe`** - Plan and analyze page elements before taking actions

## How It Works

### Basic Usage

```typescript
import { Stagehand } from "@browserbasehq/stagehand";
import StagehandConfig from "./stagehand.config";

const stagehand = new Stagehand(StagehandConfig);
await stagehand.init();

const page = stagehand.page;

// Take actions with natural language
await page.act("Click the sign in button");

// Extract data with schemas
const data = await page.extract({
  instruction: "Get the product price",
  schema: z.object({
    price: z.string(),
  })
});

// Plan actions before executing
const [action] = await page.observe("Click the submit button");
await page.act(action);
```

### Key Features

- **Cloud Browser Automation**: Runs on Browserbase's cloud infrastructure
- **AI-Powered Actions**: Use natural language to interact with web pages
- **Structured Data Extraction**: Extract data with Zod schemas for type safety
- **Multiple LLM Support**: Supports both OpenAI and Anthropic models
- **Agent Mode**: Autonomous execution of complex multi-step tasks

## Project Structure

```
Stagehand Test/
├── index.ts              # Main entry point
├── llm_clients/          # LLM client configurations
├── stagehand.config.ts   # Stagehand configuration
├── utils.ts              # Utility functions
└── package.json          # Dependencies and scripts
```

## Getting Started

1. Navigate to the `Stagehand Test` directory
2. Install dependencies: `npm install`
3. Configure your environment variables (see `.env.example`)
4. Run your tests: `npm start` or `ts-node index.ts`

## Configuration

The project includes configurations for:
- Stagehand browser automation settings
- LLM client configurations (OpenAI, Anthropic)
- Browserbase cloud browser setup
- TypeScript compilation settings

## More Information

For detailed usage patterns, advanced configurations, and best practices, see the [`.cursorrules`](./Stagehand%20Test/.cursorrules) file which contains comprehensive guidelines for working with Stagehand.

---

**Note**: This is an experimental project for learning and testing purposes. Use it to explore the capabilities of AI-powered browser automation with Stagehand and Browserbase. 