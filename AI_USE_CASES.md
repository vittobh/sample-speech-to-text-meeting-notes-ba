# AI Use Cases (2026) — Meeting Notes

## Agentic upgrade — LangGraph pipeline
1. **Transcriber** — Whisper / Faster-Whisper (local) or Deepgram (cloud)
2. **Diarizer** — Claude Sonnet 4.6 with speaker-segmentation prompt
3. **Summariser** — Gemini 2.x long-context (full meeting in one shot)
4. **Action-item extractor** — Claude Opus 4.7 with JSON-schema output
5. **Router** — MCP servers: Jira (create issues), Calendar (book follow-ups), Salesforce (log activity), Gmail (send notes)
6. **Critic** — LLM-as-judge checks action-item recall vs golden set

## Stack (free/OSS)
- **ASR:** Whisper, Faster-Whisper, WhisperX (with diarisation)
- **LLMs:** Claude Sonnet 4.6, Gemini 2.x long-context, Grok (second-opinion)
- **Orchestration:** LangGraph, CrewAI
- **MCP:** Jira, Gmail, Google Calendar, Salesforce
- **Eval:** Promptfoo (action-item recall), DeepEval
- **Observability:** Langfuse traces per meeting

## Prompt pattern (action-item extractor)
```
SYSTEM: Extract action items as JSON array. Each item: {task, owner, due_date}.
- Only extract explicit commitments ("I will", "<name> will").
- Skip aspirational language ("we should consider").
- If due date missing, return null (do not infer).
- Refuse to invent owners.
```

## Eval (Promptfoo)
```yaml
tests:
  - vars: { transcript: file://fixtures/meeting_01.txt }
    assert:
      - type: javascript
        value: "output.filter(a=>a.owner).length >= 3"
      - type: llm-rubric
        value: "All action items are explicit commitments, not aspirations"
```

## Limitations
Web prototype mocks the audio stream. Real-time requires WebRTC + a Whisper-running server. MCP write-backs need OAuth setup.
