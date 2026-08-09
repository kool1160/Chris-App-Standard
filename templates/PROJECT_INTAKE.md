# Project Intake — App Standard

Keep this short. The goal is enough truth to start safely, not a giant specification.

## 1. Product

**Name:**  
**One-sentence purpose:**  
**Primary user:**  
**Pain/problem today:**  
**What must be easier/faster/better:**

## 2. V1

**The smallest complete thing V1 must let the user do:**

**Three required capabilities:**
1. 
2. 
3. 

**Three explicit non-goals:**
1. 
2. 
3. 

**How we will prove V1 worked:**

## 3. Surfaces

**Primary device/screen:**  
**Secondary device/screen:**  
**Offline required?** yes / no / unknown  
**Accessibility constraints:**  
**Existing brand/UI to preserve:**

## 4. Data and integrations

**Default hosting:** Vercel  
**Default backend/data platform:** Supabase  
**Durable data needed? What belongs in Supabase?**  
**Accounts/auth needed? Why?**  
**Storage/realtime/server functions needed? Why?**  
**External APIs/services needed beyond Vercel/Supabase? Why?**  
**AI needed for V1? What exact job?**  
**External side effects (send/publish/pay/delete/etc.):**

A deviation from Vercel + Supabase requires a concrete reason and explicit owner approval. Do not add Supabase features merely because they exist.

## 5. Technical constraints

**Existing repo/code to reuse:**  
**Required language/framework/runtime, if any:**  
**Vercel environment/runtime constraints:**  
**Supabase auth/RLS/data/privacy constraints:**  
**Budget/paid-service constraints:**  
**Other privacy/security constraints:**

## 6. Commands

Fill these after the stack is selected:

- install:
- lint:
- typecheck:
- test:
- integration/e2e:
- build/package:
- run/dev:

## 7. First gate

What is the smallest vertical slice that proves the foundation without building future features?

**Gate objective:**  
**In scope:**  
**Out of scope:**  
**Acceptance evidence:**
