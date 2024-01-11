ㅤ
ㅤ
# UAS Object Oriented Analysis & Design

\
__Made for:__
> _Object Oriented Analysis & Design_
>
> [ LEC ] -  Final Semester

\
__Composed by:__
> 2501977941 - Kevin Gunawan
>
> ChatGPT (Best Boi)

ㅤ

## Essay

### Coupling, Cohesion, and Connascence

> **Coupling**:\
This is like how much the blocks depend on each other.

- **High (Close) coupling**:

  Blocks are glued together, so changing one means rebuilding the whole thing. This is bad because it's hard to fix.

  ```java
    class OrderProcessor {
        private PayPalGateway paymentGateway = new PayPalGateway();
    //          this is a concrete implementation  ↑
    //                 thus, it is Highly Coupled

        ...
    }
  ```

- **Low coupling**:

  Blocks simply sit on top of each other. Changing one doesn't break the others, making it easier to build and fix.

  ```java
    interface PaymentGateway {
        void processPayment(double amount);
    }

    class PayPalGateway implements PaymentGateway {
        ...
    }

    class OrderProcessor {
        private PaymentGateway paymentGateway;

        public OrderProcessor(PaymentGateway paymentGateway) {
            this.paymentGateway = paymentGateway;
    //           ↑ dependency injection is one of the best
    //             indicator that your code is loosely coupled.
        }
    }
  ```

> **Cohesion**:\
This is how well the blocks go together within a section.

- **High cohesion**:

    All the blocks in a section are of the same color or shape. They make sense together!

    ```java
    class OrderProcessor {
            private EmailService emailService;
            private InvoiceGenerator invoiceGenerator;
            private InventoryManager inventoryManager;
    //              ↑  Ia mendelegasikan tugasnya ke class yang
    //                 khusus dibuat untuk mengerjakan tugas itu,
    //                 sehingga ia dikatakan team player: atau juga highly cohesive.

            public void processOrder(Order order) {
                emailService.sendOrderConfirmationEmail(order);
                invoiceGenerator.generateInvoice(order);
                inventoryManager.updateInventory(order);
            }
        }
    ```

- **Low cohesion**:

  We have a red block next to a yellow block and a square block next to a circle. It's all jumbled up!

  ```java
    class OrderProcessor {
        public void processOrder(Order order) {
            sendOrderConfirmationEmail(order);
            generateInvoice(order);
            updateInventory(order);
    //      ↑  ketika suatu class melakukan semuanya sendiri,
    //         ia di-compare dengan lone wolf, yang mana tidak
    //         ditemani oleh class lain, sehingga merupakan
    //         kebalikan dari kohesi.
        }
    }
  ```


> **Connascence**:\
This is like knowing which blocks will need to change together if we change one.

- **High connascence**:

  If we change the red block, we might also need to change the yellow block because they're part of the same picture.

  ```java
    class Address {
        private String street;
        private String city;
        private String state;
        private String zipCode;
    }

    class Order {
        private String customerName;
        private Address shippingAddress;
        private Address billingAddress;
    }
  ```

- **Low connascence**:

  Changing the red block doesn't affect the circle block because they're not connected.

  ```java
    class Order {
        private String customerName;
        private String shippingAddress;
        private String billingAddress;
    }
  ```

ㅤ

### System and User Interface
UI is concerned with the `visual aesthetics and layout`; whereas UX encompasses the `entire interaction` a user has with a product.

Usability is a key consideration in UI design, ensuring that the interface is easy to navigate and understand.

Consistent UI design ensures that users can predict how elements behave throughout an application.

Implementing responsive design to ensure a seamless experience across various devices is key consideration for mobile UI design.

In user interfaces, the following are types of navigation controls:
- Keyboard shortcuts and gestures
- Language-based commands and instructions
- Menus and dropdown lists
- Direct manipulation through touch or mouse interaction
- Voice recognition systems for hands-free control

ㅤ

### Designing Tests
This is Designing Tests.

ㅤ

### Developing Documentation

> Remember, without documentation, your system's a recipe for disaster! So grab your pen, write it down, and avoid the mystery-meat madness!

System documentation is like a detailed recipe for building and maintaining a complex system.

It's not just an optional garnish, but a core ingredient that ensures everything functions smoothly and deliciously.

Here's why it's so important:

1. **Clarity and Knowledge Transfer**:

    - Documents act as a single source of truth, capturing all essential information about a system. No more relying on tribal knowledge or memory lapses.

    - New team members can quickly onboard and understand how the system works, reducing training time and frustration.

    - Stakeholders can stay informed about the system's purpose, functionality, and limitations.

2. **Improved Efficiency and Quality**:

    - Documentation guides development, reduces duplication of effort, and prevents reinventing the wheel.

    - Clear instructions and procedures minimize errors and inconsistencies, leading to better quality systems.

    - Well-documented systems are easier to troubleshoot and debug, saving time and resources.

3. **Enhanced Collaboration and Communication**:

    - Documents establish a common language and understanding among different teams working on the system.

    - Collaboration becomes smoother when everyone refers to the same information and terminology.

    - Documentation facilitates communication with external stakeholders like clients or regulators.

4. **Future-proofing and Maintainability**:

    - As systems evolve, well-maintained documentation helps developers understand existing code and make informed changes.

    - It becomes easier to add new features or adapt to changing requirements without getting lost in spaghetti code.

    - Documentation ensures the system's longevity and value even when the original developers move on.

Types of Documentation:

- **System Documentation**: that assists programmers/analyst to build and maintain the system
- **User Documentation**: that assists users on how to operate the system; as most of them will not read the manual before using the system.

- **Reference Documents**: tell operators on how to perform a specific tasks.
- **Procedure Manuals**: describes how to perorm business tasks; and where each procedure entails multiple tasks
- **Tutorials**: teach people on how to use specific components of a system.

Structure of a Documentation:
1. Develop a set of navigation controls that spans different topics of documentation.
2. Topics generally come from 3 sources:
   - Commands and menus in the user interface
   - How to perform certain tasks, which can be found in:
     - Use scenarios
     - WNDs
     - Real use-cases
   - Definitions of important terms
ㅤ


## Case

### Analysing Architecture
A system consists of two parts:

> **Software Components**
>
> Which includes:
>  - Data storage
>  - Data access logic
>  - Application logic
>  - Presentation logic

> **Hardware Components**
>
> Which includes:
> - Clients
> - Servers
> - Network that connects both of the above

\
In response to this, there exsits the following infrastructure:
|  | Server-based | Client-based | Client-Server |
|--|--|--|--|
| Cost of Infrastructure | Very High | Medium | Low |
| Cost of Development | Medium | Low | High |
| Ease of Development | Low | High | Low-Medium |
| Interface Capabilities | Low | High | High |
| Control & Security | High | Low | Medium |
| Scalability | Low | Medium | High |


ㅤ

### Infrastructure Design in Deployment Diagram & Network Model

**Deployment Diagram**: This is like the blueprint of your castle. It shows all the important parts:

- **Towers**: These are your software components, like the main hall, kitchen, or dragon stables (metaphorically speaking!).
- **Walls & Bridges**: These are your servers and networks, connecting everything together.
- **Drawbridges & Gates**: These are security measures that control who can access different parts of the castle.

ㅤ

**Network Model**: This is like the plumbing and wiring of your castle. It shows:

- **Pipes & Tunnels**: These are data channels, carrying information between towers through the walls and bridges.
- **Pumps & Levers**: These are network devices like routers and switches, directing the flow of information.
- **Filters & Traps**: These are security tools that protect your castle from unwanted visitors (or data packets).

ㅤ

**How they're related**: Just like how the plumbing brings water to different parts of the castle, the network model carries data to different software components in the deployment diagram. The deployment diagram shows what components exist, while the network model shows how they talk to each other.