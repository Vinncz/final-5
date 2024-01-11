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
This is Developing Documentation.

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

Deployment Diagram visualizes the relationships between **HARDWARE** components in a system.

Network Model visualizes **`WHICH SYSTEM COMPONENTS ARE CONSIDERED IMPORTANT ENOUGH`** and **`WHERE ARE THEY LOCATED USING GEO LOCATION`**.

Purpose of a network model:
- Convey the complexity of the system
- Show how the system's software components will fit together.
