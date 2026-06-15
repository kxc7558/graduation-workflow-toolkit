# AI-Powered Graduation Project Workflow

This documents the complete workflow I used to build a full-stack graduation project (Spring Boot + Vue 3 + Blockchain + thesis) with AI assistance.

## The Project

**Logistics Fund Transparency Management System** — a dual-ledger architecture combining a business ledger with blockchain-based audit trail.

- Backend: Spring Boot + MyBatis-Plus + JWT + Web3j
- Frontend: Vue 3 + TypeScript + Element Plus
- Blockchain: Solidity + Hardhat (local Ethereum)
- Database: MySQL (16 tables, 14 controllers)
- AI Integration: Ollama + OpenAI-compatible API for in-app assistant
- Thesis: ~15,000 words, 7 chapters, formatted to school standards

## AI Tools Used

| Tool | Role | Cost |
|------|------|------|
| **Claude Code** | Primary dev engine — architecture, code generation, debugging | API usage |
| **MiMo Code** | Lightweight tasks — syntax queries, simple snippets | Free |
| **Python scripts** | Thesis formatting, docx manipulation, AIGC risk scanning | Free |

## The Workflow

### Phase 1: Architecture & Setup (2-3 days)
1. Defined project requirements and tech stack with Claude Code
2. Generated database schema (16 tables, ER modeling)
3. Set up Spring Boot project structure with Maven
4. Configured Hardhat local blockchain environment

### Phase 2: Backend Development (5-7 days)
1. Generated controller/service/repository layers with `backend-dev` skill
2. Implemented RBAC permission system (3 roles)
3. Built approval workflow engine for fund transactions
4. Integrated Web3j for blockchain interaction
5. Wrote unit and integration tests

### Phase 3: Frontend Development (5-7 days)
1. Generated Vue 3 views and components with `frontend-pro` skill
2. Built admin dashboard with Element Plus
3. Implemented blockchain browser and audit pages
4. Added AI assistant panel with model switching
5. Applied design tokens and dark mode

### Phase 4: Blockchain Integration (2-3 days)
1. Wrote Solidity smart contracts with `blockchain-dev` skill
2. Deployed to local Hardhat network
3. Implemented tx_hash recording and hash verification
4. Built snapshot and recovery system for chain resets

### Phase 5: Thesis Writing (7-10 days)
1. Generated chapter drafts from code with `thesis-tools` skill
2. Created database documentation, API docs, and flowcharts from code
3. Formatted thesis with Python scripts (header/footer, TOC, table captions)
4. Ran AIGC risk scanning and rewrote high-risk sections
5. Applied school formatting standards

### Phase 6: Defense Preparation (2-3 days)
1. Generated defense PPT outline and speaker notes
2. Prepared demo script and test scenarios
3. Compiled project screenshots and system manual

## Key Learnings

1. **Skills amplify speed**: Each skill captured project-specific conventions, reducing repetitive instruction by 80%
2. **AI for formatting is underrated**: Python + python-docx saved days of manual Word formatting
3. **Dual AI strategy works**: Claude Code for complex tasks, MiMo for quick queries
4. **Code-to-doc is a superpower**: Generating thesis content directly from source code ensures accuracy
5. **Iterate, don't perfect**: Generate a rough draft first, then refine — both code and thesis

## How to Use This Toolkit

1. Copy the `skills/` directory to your project's `.claude/skills/`
2. Each skill activates automatically when Claude Code detects the relevant context
3. Combine skills — e.g., `backend-dev` + `blockchain-dev` for blockchain API endpoints
4. For thesis work, use `thesis-tools` to generate documentation from existing code
