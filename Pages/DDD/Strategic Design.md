# Strategic Design

## Ubiquitous Language

Establishing a common language that is shared between developers and domain experts.

- **Purpose:** Ubiquitous Language is about establishing a common vocabulary that is shared among all stakeholders involved in the project, including developers, domain experts, and business stakeholders. This shared language is used both in the code and in discussions about the system, ensuring clarity of communication and that all parties have a shared understanding of the domain concepts.
- **Benefits:** Reduces misunderstandings and miscommunication by ensuring that terms and phrases are used consistently throughout the project. It also helps in making the code more readable and aligned with the domain, facilitating easier maintenance and development.

## Bounded Context

Defining explicit boundaries within which a particular model is defined and applicable.

- **Purpose:** A Bounded Context is a logical boundary within which a specific domain model is defined and applicable. It marks the limits of a particular subsystem or area of interest, within which a particular model is valid. Different bounded contexts may have different models for the same concept, depending on their specific needs and interpretations.
- **Benefits:** Helps in dealing with the complexity of large systems by dividing them into more manageable and loosely coupled subsystems. It allows different teams to work independently on different parts of the system without the need for constant coordination. It also facilitates the integration of legacy systems or external systems by defining clear boundaries and interfaces.

## Sub-domains

Identifying distinct areas or categories within the overall domain.

- **Purpose:** Sub-domains are smaller parts of the overall domain, each focusing on a specific aspect of the business or system. They are identified during the domain exploration phase and can be categorized into core domains, supporting sub-domains, and generic sub-domains, based on their relevance and strategic importance to the business.
- **Benefits:** Identifying sub-domains allows organizations to prioritize development efforts, focusing on the core domains that are critical to the business's success. It also helps in organizing the development team structure and in deciding when to build custom solutions versus when to buy or outsource.
