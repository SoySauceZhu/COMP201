# Requirement engineering process

## Requirement engineering process
- Requirement Elicitation
    - What service do the user requires of the system
- Requirement Analysis: 
    - How to classify priorities and negotiate the requirement
- Requirement validation
    - Does the proposed system complete what user requires. i.e. send draft to user 
- Requirement management
    - Manage changes to the requirements document

## Feasibility Studies
Whether the proposed system is worthwhile

- If the system contributes to organisational objects
- If the system can be engineering using current tech technologies and within budget
- If the system can be integrated with other system that are used currently
- Is there a simple way of doing so
   
**Feasibility reports**  

A report should include:

- Technical feasibility
- Legal feasibility
- Economic feasibility
- Scheduling feasibility

## Elicitation and Analysis
- Aka requirement discovery
    - Gathering information
- Technical staff working with customer to work out:
    - Application domain
    - Desired service
    - Operational constraints

**Problems**

- Stakeholder don't know what they really want
- Stakeholder express requirement in their own term
- Different stakeholder may have conflict requirements
  
### Viewpoint

Viewpoints are the way of structuring the requirements to represent the perspectives of different stakeholders.  
Stakeholder may be classified at a different viewpoints.  
This multi-perspective analysis is important as there is no single correct way to analyze system requirements.

Viewpoints may be:

- Provider and receiver of the system services
- Regulation as standard
- Sources of business and non-functional requirements
- Engineers The responsible to develop and Maintain the system
- Marketing staff

### Techniques to develop elicitation:
- Prototyping
- Interviewing
- Ethnography:
    - People do not really put forward their requirement, explain or articulate their work.
    - Technical staff only observing and analysis how people actually work.
    - Social and organizational factors of importance may be observed.
    - Ethnographic studies have shown that work is usually richer and more complex than suggested by simple system models.
- Focused Ethnography
    - Combines ethnography with prototyping

### Security Requirement
- Confidentiality requirement: Keep data secure
    - Hard security: Encryption - on data side
    - Soft security: Permission - on IO side
    - Data should be secure in storage, on transition and as long as reasonably possible
- Integrity
    - i.e. Hash check, CRC check, asymmetric cipher
    - You should know data is modified when it is not integrity
- Authentication & Authorization
- Non-repudiation
    - Sent message cannot be denied later. Non-regrettable
- Availability (Performance security)
    - Resilience to power off, flood, damage of server