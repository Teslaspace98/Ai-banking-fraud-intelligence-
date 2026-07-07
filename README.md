# AI-Powered Banking Support & Fraud Intelligence System (NLP + RAG)

GUVI x HCL Mini Project 5 — Banking & Finance domain.

## Objective
Build an AI system that automates banking customer support, detects potential fraud, and assists human agents with decision-making using NLP + RAG.

## Status
v0.1 — Intent detection + risk classification layer (Step 1). RAG pipeline, FAISS vector DB, and Streamlit dashboard to follow over the 14-day build.

## Tech Stack (planned)
Python, NLP, FAISS, RAG, Streamlit, Machine Learning

## Current Code (app.py)

```python
import streamlit as st

FRAUD_KEYWORDS = ["didn't make", "unauthorized", "fraud", "stolen"]

def detect_intent(query):
    """Rule-based intent classifier - baseline before ML model."""
    query = query.lower()
    if any(w in query for w in FRAUD_KEYWORDS):
        return "Fraud / Unauthorized Transaction", "High"
    elif any(w in query for w in ["loan", "emi", "application status"]):
        return "Loan Query", "Low"
    elif any(w in query for w in ["kyc", "verification", "document"]):
        return "KYC Verification", "Medium"
    else:
        return "General Support", "Low"

st.title("AI Banking Support & Fraud Intelligence")
user_query = st.text_input("Customer Query", "I see a transaction of ₹10,000 I didn't make")
if st.button("Analyze"):
    intent, risk = detect_intent(user_query)
    st.write(f"**Intent:** {intent}")
    st.write(f"**Risk Level:** {risk}")
```

## Roadmap
- [x] Intent + risk detection (rule-based baseline)
- [ ] ML-based intent classifier
- [ ] RAG pipeline with FAISS
- [ ] LLM response generation
- [ ] Streamlit dashboard
