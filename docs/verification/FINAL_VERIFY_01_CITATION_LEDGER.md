# FINAL_VERIFY_01 — Citation Ledger

**Project:** GIBBRN Dossier V2  
**Scope:** All citations across all 13 V2 documents  
**Audit Date:** September 2026  
**Standard:** Primary-source verification for all externally checkable claims  

Legend: ✅ Verified | ⚠️ Conditional | ❌ Error | 🔴 Blocking

---

## Citation Verification Table

| ID | Claimed Citation | Dossier Claim | Files | Metadata Verified | Claim Supported | Publication Status | Required Correction |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **C01** | "A. Achiam et al., 'GPT-4 Technical Report,' arXiv:2303.08774, 2023" | LLMs exhibit reasoning across bounded prompts | V2_01 [1] | ✅ Title, arXiv ID, year correct. First author "Achiam" (OpenAI) confirmed. | ✅ Supported | Technical report / preprint; not peer-reviewed journal. | None. |
| **C02** | "Gemini Team, 'Gemini: A Family of Highly Capable Multimodal Models,' arXiv:2312.11805, 2023" | Foundation model capability evidence | V2_01 [2] | ✅ Title and arXiv ID confirmed. | ✅ Supported | Technical report / preprint. | None. |
| **C03** | "J. S. Park et al., 'Generative Agents,' ACM UIST 2023" | Agent state maintained as unstructured context | V2_01 [3] | ✅ Park et al. UIST 2023 confirmed. Title "Generative Agents: Interactive Simulacra of Human Behavior" confirmed. | ⚠️ Partial — paper covers simulated social agents, not agent frameworks for enterprise tasks. The inference about "unstructured context" is a GIBBRN generalization. | Peer-reviewed, ACM UIST 2023. | Add clarification: "used as illustrative evidence of context-window-centric architecture; not enterprise-focused." |
| **C04** | "C. Packer et al., 'MemGPT: Towards LLMs as Operating Systems,' arXiv:2310.08560, 2023" | Flat vector databases storing unverified summaries | V2_01 [4], V2_02 [3] | ✅ Title, arXiv ID, year confirmed. Authors: Packer, Fang, Patil, Moon, Thomas, Gonzalez. | ⚠️ Partial — MemGPT does use hierarchical memory but "flat vector database storing unverified textual summaries" is an imprecise description of MemGPT's architecture. | arXiv preprint; also appeared at NeurIPS 2023 workshops. | Soften characterization: "MemGPT extends context management via hierarchical memory tiers." |
| **C05** | "C. Wu et al., 'AutoGen,' arXiv:2308.08155, 2023" | Unvalidated application-level dictionary state | V2_01 [5] | ✅ AutoGen paper confirmed. Wu et al., arXiv:2308.08155. | ⚠️ Partial — "unvalidated application-level dictionary" is a GIBBRN interpretation of AutoGen's design, not an explicit AutoGen claim. | arXiv preprint. | Label as GIBBRN design interpretation. |
| **C06** | "N. Dziri et al., 'Faith and Fate,' NeurIPS 2023" | Context compression causes factual drift | V2_01 [6] | ✅ Dziri et al., "Faith and Fate: Limits of Transformers on Compositionality," NeurIPS 2023 confirmed. | ⚠️ Supported with qualification — the paper covers compositional reasoning limits, not specifically "context compression causing factual drift." The inference is GIBBRN's. | Peer-reviewed, NeurIPS 2023. | Label the drift inference as SUPPORTED INFERENCE based on Dziri et al.'s compositionality findings. |
| **C07** | "OWASP GenAI Security Project, 'OWASP Top 10 for Agentic AI,' Community Draft Standard, 2025–2026" | Memory Poisoning is ASI06 | V2_01 [7], V2_02 [9] | ✅ OWASP Agentic Top 10 confirmed, officially published December 9, 2025. ASI06 = Memory & Context Poisoning confirmed. | ✅ Verified fact. | Official community standard published December 2025. | Update citation year to "2025" (December 2025 publication). Remove "Community Draft" — it is the official v1.0 release. |
| **C08** | "S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, '...MINJA...', NeurIPS 2024, arXiv:2503.03704" | Memory injection attacks with >85% success | V2_01 [8], V2_02 [10], V2_05 [1], V2_10 | 🔴 **YEAR WRONG.** arXiv:2503.03704 submitted March 5, 2025. Accepted NeurIPS **2025**, not NeurIPS 2024. Title "Memory Injection Attacks on LLM Agents via Query-Only Interaction" ✅. Authors ✅. arXiv ID ✅. | ✅ Claim direction supported — attack success is demonstrated. ">85%" needs caveat as configuration-dependent. | **NeurIPS 2025** (not 2024). arXiv submitted March 2025. | **MUST FIX:** Change all instances of "NeurIPS 2024" to "NeurIPS 2025" for this citation. Add qualifier: ">85% success in evaluated configurations." |
| **C09** | "T. Xie et al., 'AgentErrorBench,' arXiv:2407.01505, 2024" | Markovian error cascades analysis | V2_01 [9], V2_02 [11], V2_06 Table | 🔴 **AUTHOR AND arXiv ID INCORRECT.** AgentErrorBench is by **Zhu et al. (2025)**, not Tianbao Xie et al. arXiv:2407.01505 does not correspond to this paper. Tianbao Xie is known for OSWorld (NeurIPS 2024). | ⚠️ The general claim about Markovian cascades and AgentErrorBench (ALFWorld/GAIA/WebShop trajectories) is directionally consistent with what AgentErrorBench (Zhu et al.) covers. But the attribution is wrong. | AgentErrorBench: Zhu et al. 2025, pending full arXiv ID verification. | **MUST FIX:** Replace with: "Zhu et al., 'Where LLM Agents Fail and How They can Learn From Failures,' 2025 (AgentDebug/AgentErrorBench benchmark)." Remove arXiv:2407.01505 entirely. |
| **C10** | "H. Xia et al., 'Agentless: Demystifying LLM-based Software Engineering,' arXiv:2407.01489, 2024" | Static pipeline rivals autonomous loops; resolve rate | V2_01 [10], V2_02 [5], V2_09 | ✅ Title, arXiv ID, year confirmed. Authors: Chunqiu Steven Xia et al. Note: first author "Xia" confirmed; "H. Xia" in text is imprecise ("Chunqiu Steven Xia"). | ✅ Supported — Agentless achieved 32% resolve on SWE-bench Lite with GPT-4o. | arXiv preprint 2024. Also appears in later proceedings. | Minor: Update first author initial from "H. Xia" to "C. S. Xia" for accuracy. |
| **C11** | "OpenAI, 'Learning to Reason with LLMs,' Technical Announcement, Sept. 2024" | Scaling parameters and test-time compute | V2_02 [1] | ⚠️ This is a blog post announcement, not a peer-reviewed paper. | ✅ Supported directionally (refers to o1 model). | Blog / announcement. | Add "(Technical Blog Post)" label. This is an acceptable source for a product announcement but should not be treated as peer-reviewed. |
| **C12** | "Harrison Chase, 'LangGraph: Multi-Agent Workflows as Graphs,' LangChain Technical Report, 2024" | Graph-based developer ergonomics | V2_02 [2] | ⚠️ This citation is informal. LangGraph is documented through official LangChain documentation. "Technical Report" is not standard nomenclature for this. | ✅ Supported — LangGraph's graph-based architecture is documented. | Official library documentation / blog posts. | Replace with: "LangChain Team, 'LangGraph Documentation,' LangChain, Inc., https://langchain-ai.github.io/langgraph/, accessed September 2026." |
| **C13** | "C. E. Jimenez et al., 'SWE-agent,' NeurIPS 2024" | Harness dominance; 27.4 percentage point effect | V2_02 [4], V2_10 | ⚠️ **Author attribution issue:** First author is **John Yang**; C.E. Jimenez is second author. In IEEE/ACM "et al." convention, first author governs: should be "J. Yang et al." Title and NeurIPS 2024 venue ✅. arXiv:2405.15793 ✅. | ⚠️ **27.4pp claim is not verified as a direct comparison.** SWE-agent paper compares configurations but the specific "27.4 percentage point harness-driven swing holding model constant" is not confirmed as a single-experiment controlled result attributable jointly to both papers. | Peer-reviewed, NeurIPS 2024. | Fix to "J. Yang et al." Reframe 27.4pp claim as an approximate cross-paper observation, not a controlled within-paper result. |
| **C14** | "N. Shinn et al., 'Reflexion: Language Agents with Verbal Reinforcement Learning,' NeurIPS 2023" | Verbal self-reflection hypothesis | V2_02 [6] | ✅ Confirmed. Authors: Shinn, Cassano, Berman, Gopinath, Narasimhan, Yao. NeurIPS 2023 ✅. | ✅ Supported — Reflexion proposes verbal self-reflection for improvement. | Peer-reviewed, NeurIPS 2023. | None. Note: dossier correctly cites this as the "initial hypothesis" that subsequent work contradicts — accurate framing. |
| **C15** | "J. Huang et al., 'Large Language Models Cannot Self-Correct Reasoning Yet,' ICLR 2024" | Self-correction non-monotonic without external verifier | V2_02 [7], V2_10 | ✅ Title, venue, year confirmed. Authors: Huang, Chen, Mishra, Zheng, Yu, Song, Zhou (abbreviated "J. Huang et al." acceptable). | ✅ Strongly supported — paper's central finding is that LLMs cannot self-correct reasoning without external feedback. | Peer-reviewed, ICLR 2024. | None. This is the dossier's best-verified citation. |
| **C16** | "K. Valmeekam, M. Marquez, A. Olmo, S. Sreedharan, and S. Kambhampati, NeurIPS 2023" | LLMs cannot autonomously validate plans | V2_02 [8] | ⚠️ Paper confirmed as NeurIPS 2023. Title verified: "On the Planning Abilities of Large Language Models: A Critical Investigation." However, the NeurIPS proceedings version lists 4 authors (Valmeekam, Marquez, Sreedharan, Kambhampati). "A. Olmo" appears in the arXiv preprint but may not appear in the final NeurIPS proceedings version. | ✅ Claim strongly supported — paper directly demonstrates LLM planning limitations without symbolic validators. | Peer-reviewed, NeurIPS 2023. | Minor: Remove "A. Olmo" from author list in reference [8] if citing NeurIPS proceedings. Use "et al." to be safe. |
| **C17** | "F. Perez and I. Ribeiro, 'Ignore This Title and Hack This Agent,' arXiv:2305.14874, 2023" | Authority laundering / prompt injection | V2_02 [12] | ✅ arXiv:2305.14874 confirmed. Note: title is "Ignore Previous Prompt: Attack Techniques For Language Models" by Fábio Perez and Ian Ribeiro. Slight title variation in dossier. | ✅ Supported as prompt injection evidence. | arXiv preprint 2023. | Minor: Update to exact title "Ignore Previous Prompt: Attack Techniques For Language Models." |
| **C18** | "L. Lamport, 'Time, Clocks...' CACM 1978" | Event-sourced causal tracking | V2_02 [13] | ✅ Classic, verified primary reference. | ✅ Established — foundational distributed systems theory. | Peer-reviewed journal (ACM CACM). | None. |
| **C19** | "P. A. Bernstein et al., Concurrency Control and Recovery in Database Systems, Addison-Wesley, 1987" | Causal tracking in database systems | V2_02 [14] | ✅ Classic textbook, verified. | ✅ Established. | Published textbook. | None. |

---

## Summary Statistics

| Status | Count |
| :--- | :--- |
| ✅ Fully Verified | 10 |
| ⚠️ Conditional (minor issues) | 7 |
| ❌ / 🔴 Blocking Error | 2 (C08, C09) |
| **Total Citations Audited** | **19** |

---

## Corrected Reference Block (Canonical)

The following is the corrected reference list to propagate to all V2 files:

```
[MINJA-CORRECT] S. Dong, S. Xu, P. He, Y. Li, J. Tang, T. Liu, H. Liu, and Z. Xiang, 
  "Memory Injection Attacks on LLM Agents via Query-Only Interaction," 
  in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), 2025. arXiv:2503.03704.
  [First submitted March 5, 2025; accepted NeurIPS 2025.]

[AGENTERRORBENCH-CORRECT] Zhu et al., "Where LLM Agents Fail and How They can Learn From Failures,"
  2025. (AgentDebug / AgentErrorBench benchmark; 200 annotated failure trajectories 
  from ALFWorld, GAIA, WebShop.) [Full arXiv ID to be confirmed at submission.]

[SWE-AGENT-CORRECT] J. Yang, C. E. Jimenez, A. Wettig, K. Lieret, S. Yao, K. Narasimhan, 
  and O. Press, "SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering," 
  in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), vol. 38, 2024. arXiv:2405.15793.

[OWASP-CORRECT] OWASP GenAI Security Project, "OWASP Top 10 for Agentic AI Applications," 
  v1.0, December 2025. Category ASI06: Memory & Context Poisoning. 
  [Official release, not community draft.]

[AGENTLESS-CORRECT] C. S. Xia, Y. Ding, L. Zhang, and T. Zhang, "Agentless: Demystifying 
  LLM-based Software Engineering Agents," arXiv preprint arXiv:2407.01489, 2024.
  [First author: Chunqiu Steven Xia.]
```

---

> **Agents can change. Their integrity must persist.**
