## Privacy in Machine Learning - An Overview

**Summary**

This section provides an overview of privacy in machine learning, emphasizing the risks and defenses involved when sharing or analyzing data:

1. **Privacy Motivation**

   - Individuals consent to data collection under the assumption it will not be used to harm them (e.g., by revealing sensitive health information).
   - Sharing data can foster collaboration (as in open benchmark datasets like MNIST or CIFAR) but also poses risks to personal privacy.

2. **Threat Model Approach**

   - **Membership Inference**: An attacker determines whether a specific individual was part of a dataset (e.g., identifying someone’s involvement in a sensitive clinical study).
   - **Attribute Inference**: An attacker predicts missing attributes (e.g., revealing someone’s smoking status). Although inference is a core goal of machine learning, it can become a privacy violation if the attacker’s predictions are substantially improved by an individual’s inclusion in the dataset.
   - **Reconstruction Attacks**: An attacker attempts to recover entire records (for instance, reconstructing exact data of individuals from aggregate statistics).

3. **Differential Privacy (DP)**

   - **Definition**: DP ensures that the algorithm’s output changes minimally when any one individual’s data is added or removed, limiting the potential privacy harm.
   - **Interpretation**: If a person opts out of the dataset, DP guarantees the algorithm’s output will not change “too much,” thus severely limiting information leakage about that person.
   - **Properties**:
     - _Composability_: Multiple DP operations combine to still maintain DP guarantees.
     - _Resistance to Post-Processing_: Any transformations on DP outputs remain DP.
     - _Bayesian Interpretation_: DP bounds how much posterior beliefs (e.g., about an individual’s presence in a dataset) can change relative to prior knowledge.

4. **Limitations of DP**
   - **Choosing Parameters (ε, δ)**: Selecting the privacy parameters that balance protection and utility is notoriously difficult and context-dependent.
   - **Relaxations**: Variants (e.g., approximate DP, Rényi DP) address practical concerns but can be harder to interpret. Overly conservative assumptions can lower utility by adding too much noise.

Overall, differential privacy is a widely accepted framework for protecting individuals in machine learning systems, but implementing it effectively requires careful design and a context-sensitive choice of privacy parameters.

## Terms Related to Data Privacy & Security Compliance

1. **GDPR (General Data Protection Regulation)**

   - **What it is**: A comprehensive data protection law passed by the European Union (EU), effective since May 2018.
   - **Scope & Significance**: GDPR governs how organizations handle personal data of individuals in the EU (and, in many cases, applies to organizations outside the EU that process EU residents’ data).
   - **Key Requirements**: Lawful basis for data processing, transparent privacy notices, enhanced rights for data subjects (access, erasure, portability), strong data security measures, breach notification obligations, and significant fines for non-compliance.

2. **CCPA (California Consumer Privacy Act)**

   - **What it is**: A California state law that grants California residents certain rights over their personal data and imposes specific obligations on businesses that collect or sell that data.
   - **Scope & Significance**: Focuses on transparency about data collection and sharing, giving consumers the right to opt out of the sale of their information, request deletion of their data, and access what is collected.
   - **Key Requirements**: Notice at collection, the right to opt out of sale of personal information, the right to request deletion, and an obligation for businesses to honor these rights.

3. **HIPAA (Health Insurance Portability and Accountability Act)**

   - **What it is**: A U.S. federal law that regulates the privacy and security of protected health information (PHI).
   - **Scope & Significance**: Applies to covered entities (healthcare providers, health plans, healthcare clearinghouses) and their business associates.
   - **Key Requirements**: Safeguarding the confidentiality, integrity, and availability of PHI, breach notification rules, administrative/technical safeguards for ePHI, and potential fines for non-compliance.

4. **ISO/IEC 27001 (Information Security Management Systems Standard)**

   - **What it is**: An international standard published by the International Organization for Standardization (ISO) and the International Electrotechnical Commission (IEC).
   - **Scope & Significance**: Specifies requirements for establishing, implementing, maintaining, and continually improving an information security management system (ISMS).
   - **Key Requirements**: Risk assessment and management of information security risks, defining security objectives, policies, and processes; often used as a certification to demonstrate strong security practices to customers and partners.

5. **SOC 2 (Service Organization Control Type 2)**
   - **What it is**: A report framework developed by the American Institute of Certified Public Accountants (AICPA).
   - **Scope & Significance**: Focuses on a service organization’s controls related to security, availability, processing integrity, confidentiality, and privacy.
   - **Key Requirements**: An independent auditor evaluates and reports on the effectiveness of an organization’s internal controls over a period of time (Type 2). Often demanded by customers or partners to ensure adequate security and compliance practices.
