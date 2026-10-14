# AD-CAT requirements catalog

120 entries (115 requirements and 5 sub-requirements). Origin tags: H = written by the author, AI-K = proposed by the model and kept as is, AI-R = proposed by the model and then rewritten or merged by the author. (AI) = applies only to apps with AI features. (HR) = applies only when the AI system is high-risk under the EU AI Act. (M) = can only be checked by the manufacturer, because it depends on internal records such as the risk management file or the security logs.

## Table 5. Functional suitability requirements (FUN-)

| ID | Requirement description | Source | Origin |
| --- | --- | --- | --- |
| FUN-01 | The app shall state its intended use, intended user profile and intended operational environment in its accompanying documentation. | IEC 82304-1 cl. 4.1 a) | AI-R |
| FUN-02 | The app shall provide correct results with the needed degree of precision and shall perform the functions it claims to perform. | ISO/IEC 25010 cl. 3.1.2; Rickard item 9 | AI-R |
| FUN-03 | The app shall provide guided cognitive behavioural therapy exercises. | Moumou and Idri item CC1 | AI-K |
| [FUN-03-1] | The app shall provide a thought diary helping the user identify and challenge negative thinking patterns. | Qu Table 1, Thought diaries | AI-K |
| FUN-04 | The app shall provide mindfulness or meditation sessions. | Moumou and Idri item CC2; Qu Table 1 | AI-R |
| FUN-05 | The app shall provide acceptance and commitment therapy tools. | Moumou and Idri item CC3 | AI-K |
| FUN-06 | The app shall provide relaxation techniques such as breathing or muscle relaxation exercises. | Moumou and Idri item CC4 | AI-K |
| FUN-07 | The app shall provide psychoeducational content about anxiety and depression. | Moumou and Idri items CC5, EPC25; Qu Table 1 | AI-R |
| FUN-08 | The app shall provide behavioural techniques that guide the user to perform positive behaviours. | Qu Table 1, Behavioral techniques | AI-K |
| FUN-09 | The app shall provide a means for the user to express their emotions. | Qu Table 1, Mood expression | AI-K |
| FUN-10 | The app shall allow the user to record and track their mood over time. | Moumou and Idri item SMR7; Qu Table 1, Tracking mood patterns; Wu Table 4 | AI-R |
| FUN-11 | The app shall allow the user to record triggers or context alongside mood entries. | Moumou and Idri item SMR11 | AI-K |
| FUN-12 | The app shall support tracking of the user's thought patterns. | Qu Table 1, Tracking thought patterns | AI-K |
| FUN-13 | The app shall support ongoing monitoring of the user's depression symptoms during the intervention. | Qu Table 1, Screening and Tracking | AI-R |
| FUN-14 | The app shall provide a screening function for self-assessment of depression using a validated instrument. | Qu Table 1, Self-diagnosis | AI-R |
| FUN-15 | The app shall use its screening results as a basis for personalising the intervention. | Qu Table 1, Basis for personalization | AI-K |
| FUN-16 | The app shall prompt the user for regular emotional check-ins. | Moumou and Idri item SMR8 | AI-K |
| FUN-17 | The app shall allow the user to set reminders for medication or self-care tasks. | Moumou and Idri item SMR9; Wu Table 4 | AI-R |
| FUN-18 | The app shall allow the user to view trends or summaries of their mental health data. | Moumou and Idri item SMR12 | AI-K |
| FUN-19 | The app shall allow the user to track their progress through the intervention and receive feedback on it. | Moumou and Idri item EPC28; Qu Table 1 | AI-R |
| FUN-20 | The app shall provide goal-setting or value-reflection features. | Moumou and Idri item EPC27 | AI-K |
| FUN-21 | The app shall adapt its content to the individual user based on their activity or stated needs. | Moumou and Idri item EPC26; Rickard item 13; Wu Table 4 | AI-R |
| FUN-22 | The app shall provide access to licensed professionals via chat or video. | Moumou and Idri item TCS13 | AI-K |
| FUN-23 | The app shall provide guided therapy modules. | Moumou and Idri item TCS14 | AI-K |
| FUN-24 | The app shall provide peer support forums or group chats. | Moumou and Idri item TCS15 | AI-K |
| FUN-25 | The app shall provide community events or discussion groups. | Moumou and Idri item TCS16 | AI-K |
| FUN-26 | The app shall allow the user to receive encouragement or feedback from peers or moderators. | Moumou and Idri item TCS18 | AI-K |
| FUN-27 | The app shall support offline access to its key features. | Moumou and Idri item TF32 | AI-K |
| FUN-28 | The app shall allow the user to export or share their data with a third party such as a clinician. | Moumou and Idri item TF35; Rickard item 14 | AI-R |
| FUN-29 | The app shall identify the organisation or people responsible for it. | Rickard item 7; Wu Table 4 | AI-R |
| FUN-30 | The app shall reference published research or documented evidence supporting the benefit it claims. | Rickard items 8 and 10; Wu Table 4 | AI-R |
| FUN-31 | The app shall be actively maintained, and the date of its most recent update shall be visible to the user before download. | Rickard item 2 | AI-R |
| FUN-32 | The app shall support upgrade from previous versions while maintaining data integrity. | IEC 82304-1 cl. 4.2 f) 1) | AI-K |
| FUN-33 | The app shall support rollback to the previous version after an upgrade. | IEC 82304-1 cl. 4.2 f) 2) | AI-K |
| FUN-34 (M) | The app shall specify its interoperability requirements. | IEC 82304-1 cl. 4.5 a) | AI-K |
| FUN-35 | The app shall function as expected under its expected load on its specified software and hardware platforms. | IEC 82304-1 cl. 4.5 e) | AI-K |
| FUN-36 | The app shall carry a unique version identifier. | IEC 82304-1 cl. 7.1 | AI-K |

## Table 6. Interaction capability requirements (INT-)

| ID | Requirement description | Source | Origin |
| --- | --- | --- | --- |
| INT-01 | The app shall enable users to recognise whether it is appropriate for their needs. | ISO/IEC 25010 cl. 3.4.1 | H |
| INT-02 | The app shall enable specified users to learn to use its functions within a specified amount of time. | ISO/IEC 25010 cl. 3.4.2 | H |
| INT-03 | The app shall have functions and attributes that make it easy to operate and control. | ISO/IEC 25010 cl. 3.4.3 | H |
| INT-04 | The app shall prevent user operation errors. | ISO/IEC 25010 cl. 3.4.4 | AI-K |
| INT-05 | The app shall present its functions and information in a manner that encourages continued interaction. | ISO/IEC 25010 cl. 3.4.5 | AI-K |
| INT-06 | The app shall be usable by people of various backgrounds, including different ages, cultures, languages and education levels. | ISO/IEC 25010 cl. 3.4.6 | AI-K |
| INT-07 | The app shall be usable by people with the widest range of capabilities, including those with disabilities affecting sight, hearing or motor function. | ISO/IEC 25010 cl. 3.4.7 | AI-K |
| [INT-07-1] | The app shall support accessibility features such as adjustable font size and voice navigation. | Moumou and Idri item TF34 | AI-K |
| INT-08 | The app shall present information where needed to make its capabilities and use obvious without requiring external resources. | ISO/IEC 25010 cl. 3.4.8 | AI-K |
| [INT-08-1] | The app shall explain the purpose and process of its therapeutic exercises. | Moumou and Idri item CC6 | AI-K |
| INT-09 | The app shall implement intuitive navigation patterns. | Moumou and Idri item TF36 | AI-K |
| INT-10 | The app shall be easy to use without prior instruction. | Rickard item 11 | AI-K |
| INT-11 | The app shall provide interactive or multimedia content rather than text alone. | Rickard item 12 | AI-K |
| INT-12 | The app shall use a tone that is simple, informal and friendly. | Moumou and Idri item TF37 | AI-K |
| INT-13 | The app shall allow the user to customise its notifications. | Moumou and Idri item SMR10 | AI-K |
| INT-14 | The app shall provide multi-language support and regional settings. | Moumou and Idri item TF33; IEC 82304-1 cl. 4.5 b) | AI-R |
| INT-15 | The app shall tailor its content to the user group it addresses. | Wu Table 4, Tailoring | AI-K |
| INT-16 | The app shall present its information in a truthful and unbiased manner. | Wu Table 4, Trustworthiness | AI-K |
| INT-17 (M) | The app shall have documented user interface requirements. | IEC 82304-1 cl. 4.2 b) | AI-K |
| INT-18 | The app shall be supplied with accompanying documents including instructions for use. | IEC 82304-1 cl. 4.2 e) | AI-K |
| INT-19 | The app shall make its product identification accessible to the user during use. | IEC 82304-1 cl. 7.1 | AI-K |
| INT-20 | The app's instructions for use shall state its intended use. | IEC 82304-1 cl. 7.2.2.2 a) | AI-K |
| INT-21 | The app's instructions for use shall list its non-self-explanatory system, error and fault messages with their causes and required user actions. | IEC 82304-1 cl. 7.2.2.8 | AI-K |
| INT-22 (AI) | The app shall provide AI transparency information in a clear and distinguishable manner no later than the first interaction. | AI Act Art. 50(5) | AI-K |
| INT-23 (AI) | The app's AI transparency information shall conform to applicable accessibility requirements. | AI Act Art. 50(5) | AI-K |

## Table 7. Security and privacy requirements (SEC-)

| ID | Requirement description | Source | Origin |
| --- | --- | --- | --- |
| SEC-01 | The app shall ensure that user data are accessible only to those authorised to access them. | ISO/IEC 25010 cl. 3.6.1 | AI-K |
| SEC-02 | The app shall protect its data from unauthorised modification or deletion. | ISO/IEC 25010 cl. 3.6.2 | AI-K |
| SEC-03 | The app shall enable actions to be traced uniquely to the entity that performed them. | ISO/IEC 25010 cl. 3.6.4 | AI-K |
| SEC-04 | The app shall verify that the identity of a subject or resource is the one claimed. | ISO/IEC 25010 cl. 3.6.5 | AI-K |
| [SEC-04-1] | The app shall authenticate the user before granting access to their health data. | Moumou and Idri item TF29; IEC 82304-1 cl. 4.2 d) | AI-R |
| SEC-05 | The app shall sustain its operations while under attack from a malicious actor. | ISO/IEC 25010 cl. 3.6.6 | AI-K |
| SEC-06 | The app shall present a privacy policy that is clear and accessible to the user before first use. | Moumou and Idri item TF30; Rickard item 3 | AI-R |
| SEC-07 | The app shall encrypt sensitive user data in storage and in transmission. | Moumou and Idri item TF31; Rickard item 5 | AI-R |
| SEC-08 | The app shall declare where user data is stored. | Rickard item 4 | AI-K |
| SEC-09 | The app shall protect the integrity and authenticity of stored health data. | IEC 82304-1 cl. 4.2 d) | AI-K |
| SEC-10 | The app shall provide protection against malicious intent. | IEC 82304-1 cl. 4.2 d) | AI-K |
| SEC-11 | The app shall be protected against unintended influence by other software sharing the same device resources. | IEC 82304-1 cl. 4.2 c) | AI-K |
| SEC-12 | The app shall support the delivery of timely security patches and updates. | IEC 82304-1 cl. 4.2 f) 3) | AI-K |
| SEC-13 | The app shall be distributed through a mechanism that ensures the integrity of the installation. | IEC 82304-1 cl. 4.2 f) 4) | AI-K |
| SEC-14 | The app shall support irreversible deletion of user data on decommissioning. | IEC 82304-1 cl. 4.2 f) 5) | AI-K |
| SEC-15 | The app shall meet the requirements of applicable data protection regulation for protected information. | IEC 82304-1 cl. 4.2 g) | AI-K |
| SEC-16 (M) | The app shall detect, log and time security compromises occurring during normal use. | IEC 82304-1 cl. 4.5 f) | AI-K |
| SEC-17 | The app shall protect its essential functions when its security has been compromised. | IEC 82304-1 cl. 4.5 g) | AI-K |
| SEC-18 | The app shall allow an authenticated privileged user to retain and recover the product configuration. | IEC 82304-1 cl. 4.5 h) | AI-K |
| SEC-19 | The app's instructions for use shall explain how to safely decommission the app and safeguard personal and health-related data. | IEC 82304-1 cl. 7.2.2.9 | AI-K |
| SEC-20 | The app shall document the technical security options that can be configured within it. | IEC 82304-1 cl. 7.2.3.1 g) | AI-K |
| SEC-21 | The app shall document its behaviour when a failure to maintain security is detected, including the impact on patient care and data. | IEC 82304-1 cl. 7.2.3.1 h) | AI-K |
| SEC-22 (HR) | The app shall be resilient against unauthorised third parties attempting to alter its use, outputs or performance. | AI Act Art. 15(5) | AI-K |
| SEC-23 (HR) | The app shall include measures to prevent and detect data poisoning, model poisoning and adversarial input attacks. | AI Act Art. 15(5) | AI-K |

## Table 8. Safety requirements (SAF-)

| ID | Requirement description | Source | Origin |
| --- | --- | --- | --- |
| SAF-01 | The app shall constrain its operation to within safe parameters when it encounters an operational hazard. | ISO/IEC 25010 cl. 3.9.1 | AI-K |
| SAF-02 | The app shall identify courses of events or operations that can expose the user to unacceptable risk. | ISO/IEC 25010 cl. 3.9.2 | AI-K |
| SAF-03 | The app shall automatically revert to a safe operating condition in the event of a failure. | ISO/IEC 25010 cl. 3.9.3 | AI-K |
| SAF-04 | The app shall warn of unacceptable risks in sufficient time for a response that sustains safe operation. | ISO/IEC 25010 cl. 3.9.4 | AI-K |
| SAF-05 | The app shall maintain safety during and after integration with other components. | ISO/IEC 25010 cl. 3.9.5 | AI-K |
| SAF-06 | The app shall provide crisis resources reachable from within the app, including at least one hotline or emergency contact. | Moumou and Idri item CM20; Wu Results | AI-R |
| SAF-07 | The app shall allow the user to activate an emergency text or call. | Moumou and Idri item CM21 | AI-K |
| SAF-08 | The app shall allow the user to share their location during an emergency, on their own initiative and with explicit consent. | Moumou and Idri item CM22 | AI-R |
| SAF-09 | The app shall allow the user to create and store a personalised safety plan for use in a crisis. | Moumou and Idri items CM23, CM24 | AI-R |
| SAF-10 | The app shall provide access to crisis counsellors or mental health professionals. | Moumou and Idri item TCS17 | AI-K |
| SAF-11 | Where the app assesses the user for suicidality, it shall present crisis resources together with the assessment result. | Wu Results | AI-R |
| SAF-12 | The app's instructions for use shall state known limitations and contraindications to its use. | IEC 82304-1 cl. 7.2.2.2 d) | AI-K |
| [SAF-12-1] | The app shall state clearly that it is not a replacement for professional care. | Rickard item 6; Qu Results | AI-R |
| SAF-13 | The app's instructions for use shall list all safety and security warnings related to its use. | IEC 82304-1 cl. 7.2.2.3 | AI-K |
| SAF-14 (M) | The app shall have its safety and security characteristics, identified hazards and estimated risks documented. | IEC 82304-1 cl. 4.1 b) | AI-K |
| SAF-15 (M) | The app shall implement risk control measures for risks assessed as unacceptable. | IEC 82304-1 cl. 4.1 c) | AI-K |
| SAF-16 (M) | The app shall implement at system level the risk control measures derived from its initial risk assessment. | IEC 82304-1 cl. 4.5 c) | AI-K |
| SAF-17 (HR) | The app shall state in its instructions for use the known or foreseeable circumstances of use or misuse that may lead to risks to health and safety. | AI Act Art. 13(3)(b)(iii) | AI-K |
| SAF-18 (HR) | The app shall provide a means to interrupt its AI system's operation and bring it to a halt in a safe state. | AI Act Art. 14(4)(e) | AI-K |
| SAF-19 (AI) | The app shall allow an operator to intervene in its AI system's functioning to prevent harm or hazard. | ISO/IEC 25059 cl. 3.2.4 | AI-K |

## Table 9. AI requirements (AI-)

| ID | Requirement description | Source | Origin |
| --- | --- | --- | --- |
| AI-01 | The app shall inform the user that they are interacting with an AI system. | AI Act Art. 50(1) | AI-K |
| AI-02 | The app shall mark synthetic audio, image, video or text output in a machine-readable format as artificially generated. | AI Act Art. 50(2) | AI-K |
| AI-03 | The app shall provide a chatbot for simulated therapeutic conversations. | Moumou and Idri item TCS19 | AI-K |
| AI-04 | The app shall allow the user or an authorised external agent to intervene in the functioning of its AI system in a timely manner. | ISO/IEC 25059 cl. 3.2.1 and 5.2 | AI-R |
| AI-05 | The app's AI system shall maintain its level of functional correctness under varying circumstances. | ISO/IEC 25059 cl. 3.2.5 | AI-K |
| AI-06 | The app shall communicate appropriate information about its AI system to relevant stakeholders. | ISO/IEC 25059 cl. 3.1 | AI-K |
| AI-07 (HR) | The app shall automatically record events over the lifetime of its AI system. | AI Act Art. 12(1) | AI-K |
| AI-08 (HR) | The app's AI system shall be designed so that its operation is sufficiently transparent for its output to be interpreted and used appropriately. | AI Act Art. 13(1) | AI-K |
| AI-09 (HR) | The app shall declare in its instructions for use the level of accuracy, robustness and cybersecurity against which its AI system was tested and validated. | AI Act Art. 13(3)(b)(ii) | AI-K |
| AI-10 (HR) | The app shall provide human-machine interface tools enabling effective human oversight of its AI system during use. | AI Act Art. 14(1) | AI-K |
| AI-11 (HR) | The app shall allow the person exercising oversight to disregard, override or reverse its AI system's output. | AI Act Art. 14(4)(d) | AI-K |
| AI-12 (HR) | The app's AI system shall perform consistently in accuracy, robustness and cybersecurity throughout its lifecycle. | AI Act Art. 15(1) | AI-K |
| AI-13 (HR) | The app's AI system shall be resilient to errors, faults and inconsistencies arising from its interaction with users or other systems. | AI Act Art. 15(4) | AI-K |
| AI-14 (HR) | Where the app's AI system continues to learn after deployment, it shall mitigate the risk of biased outputs influencing future operations through feedback loops. | AI Act Art. 15(4) | AI-K |
