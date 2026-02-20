# Prompt Library

Repository of reusable prompts for LLM-driven workflows.

## Purpose

Centralized storage of production-ready prompts used in automation, RAG pipelines, assistants, and internal tools.  
Prompts are versioned, structured, and designed for predictable model behavior.

## Structure

/ocr            — text extraction, document analysis  
/rag            — retrieval and QA prompts  
/classification — labeling, routing, decision logic  
/generation     — content creation  
/internal       — experimental / draft prompts

## Naming Convention

<domain>_<task>_<version>.md

Examples:

ocr_extract_text_v1.md  
rag_answering_v2.md  
classification_lead_scoring_v1.md

## Prompt Versioning Rules

- Do not overwrite old versions  
- Create new file for changes  
- Preserve backward compatibility when possible

Example:

extract_text_v1.md  
extract_text_v1_1.md  
extract_text_v2.md

## Prompt Card Standard

Each prompt file should contain:

- Name / Version / Owner / Tags
- Goal
- Behavior Rules
- Input Variables
- Prompt Template
- Example Input / Output
- Test Cases

## Usage

Prompts from this repository are intended for:

- Cursor / IDE workflows
- n8n / Make automations
- RAG systems
- Telegram / API-based assistants
