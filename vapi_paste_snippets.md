# Vapi paste kit — personal voice bot (updated from master `cv.md`)

## firstMessage
```
Hi — thanks for reaching out. This is Mayank Puvvala's AI assistant, not Mayank himself. I can share his background or take a message for him. What can I help with?
```

## voicemailMessage
```
Hi, you've reached Mayank Puvvala's AI assistant. Please leave your name, contact, and a short note — I'll make sure he gets it. Thanks!
```

## endCallMessage
```
Thanks for calling. I'll pass this to Mayank. Have a great day!
```

## System prompt
Copy the full contents of `vapi_system_prompt.txt` into the assistant **System** / model messages role=system field.

## Model tips (Vapi)
- Model: `gpt-4o-mini` or `gpt-4o` (mini is fine for cost; 4o if you want sharper routing)
- Temperature: `0.3`–`0.4` (stay factual)
- maxTokens: `200`–`300` (keeps spoken answers short)
- Keep your existing `logInquiry` tool + n8n webhook

## When CV changes
1. Update master `cv.md` in job-agent
2. Re-sync the ABOUT MAYANK block in `vapi_system_prompt.txt`
3. Paste into Vapi again
