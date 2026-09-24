
# THE CANVAS
## Next-Generation Modular Smartphone Open Platform
### Original Design Draft (v5 - Open Discussion Edition)

> "CANVAS is not merely an attempt to redesign the smartphone, but to redesign the industrial structure centered around it."

This document is an integrated grand design combining the fundamental principles, architecture, operational philosophy, and market significance of THE CANVAS agreed upon to date. Rather than presenting final mass-production specifications, its purpose is to establish a clear backbone, enabling engineers, enterprises, and researchers to concretize and validate the platform following its release.

---

# 1. Fundamental Concepts of CANVAS

CANVAS adopts a two-layer structure: a "high-performance common base terminal + expansion gadgets complying with published common standards."

While traditional smartphones integrate cameras, audio, gaming, special sensors, communication, and storage into a single device, CANVAS organizes the main body as a high-performance common computing foundation and separates specialized functions into vendor-specific gadgets.

```text
                    CANVAS OS
                       │
             ┌─────────┴─────────┐
             │   Common Base     │
             │ SoC / Battery / UI │
             │ Comm / Basic I/O  │
             └─────────┬─────────┘
                       │
       ┌───────────────┼───────────────┐
       ↓               ↓               ↓
    Camera           Audio           Gaming
    Gadget           Gadget          Gadget
       ↓               ↓               ↓
    Sensor          Storage        Special Radio
    Gadget           Gadget          Gadget
                       │
                    HUB / Bridge

What CANVAS provides is not an "all-in-one device," but a market where specialized companies can compete on top of a common foundation.
Core Principles
 * Separate the common foundation from specialized products.
 * Publish basic specifications.
 * Do not bind internal implementations to specific methods.
 * Do not hinder free market entry for enterprises.
 * Do not unnecessarily restrict user choices.
 * Do not break legacy products unnecessarily with new standards.
 * Do not obstruct repair, replacement, upgrades, and rebuilding.
 * Aim for "basically everything works," excluding necessary safety and security restrictions.
 * Reuse existing OS, USB, communication, and security mechanisms as much as possible.
 * Separate what should be standardized from what should be left to market competition.
2. Base Terminal
2.1 Form Factor
Current basic dimensions:
| Type | Dimensions |
|---|---|
| Regular | 147.5 × 71.5 × 7.85 mm |
| Large | 160.7 × 77.6 × 7.85 mm |
Stable layers such as form factor, connection positions, and basic interfaces shall be maintained for as long as possible. However, if size changes become necessary due to future technology, regulations, or manufacturing circumstances, such changes are not prohibited. CANVAS principles will be maintained through adapters, generational coexistence, new standards, or gadget-side bridges.
2.2 Display
 * Front: Touch-enabled main display
 * Sides: Notification/status display
 * Back: Notification/status display
The sides and back can display notifications, status, color bars, time, and gadget-specific UIs. Critical system, safety, and security notifications cannot be completely blocked or altered by gadgets.
2.3 Physical Buttons
 * 3 general-purpose buttons
 * 1 power button
General-purpose buttons can have their functions reassigned by the OS, gadgets, or apps.
2.4 Minimum Base Configuration
 * High-performance SoC
 * Device cooling system
 * Sufficient capacity base battery
 * Basic detection and connection sensors
 * Minimum camera for daily use and QR/barcode scanning
 * Front touch display
 * Side and rear displays
 * Standard cellular communication
 * Wi-Fi
 * Bluetooth
 * Microphones sufficient for calls, voice, and AI applications
 * Minimum speakers required for calls, notifications, video, and music
 * CANVAS gadget interface
 * CANVAS OS
 * Biometric authentication
 * Standard internal storage
High-performance cameras, audio, gaming inputs, specialized sensors, ultra-large capacity batteries, special radios, and large storage will be externalized into gadgets.
3. Gadget Connection & Mechanical Structure
Gadgets are slid and inserted from the long edge.
Gadget → Guide / Positioning → USB-C Connection → Mechanical Latch Fixation
                                      │
                              Latch Status Detection
                                      │
                         Trust / Manifest / Power

USB-C handles electrical and data connections, while structural loads are borne by the frame, guides, and mechanical latches.
Connection Process
 * Slide insertion
 * Guide positioning
 * USB-C connection
 * Mechanical latch fixation
 * Latch sensor verification
 * Device Trust / Capability check
 * Power and data activation
Removal Process
 * Status check
 * Wait for process completion if necessary
 * Stop power supply
 * Release connector
 * Release latch
 * Removal
Hall sensors, optical sensors, or protected switches can be used for latch detection; the latch itself is not used as an electrical contact.
Flexible layers such as TPE, silicone, or fluoroelastomer are provided at the contact area between the gadget and the display surface, while structural loads are absorbed by the hard frame.
Cooling
Standardized ventilation and cooling areas are secured on both long edges. A core condition is that attaching gadgets must not block these areas.
The base handles its own SoC and battery cooling, while gadgets handle heat generated by their own specific components.
Weight and Large Gadgets
CANVAS does not uniformly regulate weight or size itself. Manufacturers are responsible for mass, center of gravity, impact resistance, load distribution, and housing design. CANVAS only specifies common connection, safety, and load conditions.
4. Power, Communication & Data
4.1 Bidirectional Power
The base terminal and gadgets can exchange power bidirectionally. Gadgets may incorporate their own batteries.
CANVAS Base ⇄ USB-C / Power Delivery ⇄ Gadget

Allowable safety upper limits are determined mutually by the terminal and connected device. Within that safe range, users can select base-priority, gadget-priority, automatic, balanced, or user-defined modes. The default is automatic control.
With multiple batteries, external batteries are prioritized, with automatic switching to the internal battery in case of anomalies.
4.2 USB-C
USB-C ports are placed on both long sides and treated in principle as general-purpose ports for:
 * Charging
 * Data
 * Gadgets
 * HUBs
 * Wired audio
 * Dynamic role swapping
4.3 Communication
The base provides standard smartphone cellular, Wi-Fi, and Bluetooth connectivity. Satellite communications, special radios, and industrial radios can be implemented via gadgets.
4.4 Data Routing
Direct communication between gadgets, communication via HUBs, and routing through the base are all permitted. CANVAS does not force all data to route through the base.
4.5 Data & Storage
Basic data can be stored on the base, while specialized and large-scale data can be stored on gadgets. Storage locations can be selected as base-only, gadget-only, both, or categorized by use case. Backups utilize existing OS and cloud infrastructures; a proprietary CANVAS cloud is not mandatory.
5. CANVAS OS / Device Trust / Capability
5.1 CANVAS OS
Shared Responsibilities:
 * Connection and disconnection
 * Identification
 * Device Trust
 * Permissions
 * Power control
 * Data communication
 * Common APIs
 * Display and input interfaces
 * Resource management
 * Safe removal
 * Firmware updates
 * Common backup/restore
Gadget-specific UIs, brands, internal processing, and detailed settings remain with the manufacturers.
5.2 Device Trust
Gadgets possess individual cryptographic IDs.
Example states:
 * Registered / Trusted
 * Unknown / Guest
 * Compromised / Restricted
Registration is treated as trust information rather than an access permit. Only a compromised individual unit can be revoked and isolated without expelling the entire manufacturer.
> "Keep the entry open, but isolate compromised devices from the OS side."
> 
5.3 Capability / Device Manifest
Upon connection, gadgets declare minimal capabilities:
 * Device type
 * Required power
 * Required bandwidth
 * I/O
 * Required permissions
 * Supported CANVAS APIs
 * Available capabilities
 * Safety requirements
Specific manifest items and formats will be open to post-release technical discussions.
5.4 Runtime Resource Request
Resources such as CPU, GPU, NPU, memory, bandwidth, and power can be dynamically requested during runtime. CANVAS OS allocates these within safe usable limits. Performance degradation, partial functionality, or low-power adjustments under insufficient resource conditions are decided by the gadget side.
5.5 Feature-level Compatibility
Compatibility is handled on a feature-by-feature basis rather than all-or-nothing.
New Gadget
 ├─ Common Features → Available
 ├─ New Features → Available if OS supports
 └─ Unsupported Features → Only that specific feature is disabled

New gadgets can utilize common parts on older CANVAS devices as much as possible. Protocol differences can be absorbed by MCUs, FPGAs, ASICs, or firmware on the gadget side.
6. Software & Peripherals
Leverage standard mechanisms of existing operating systems as much as possible.
Upon connection:
Connection → Identification → Trust → Permissions → Capability/Compatibility → Use

Trusted devices require fewer prompts, while major security or capability changes trigger re-authentication.
App Distribution
A dedicated CANVAS store is not mandatory. Existing app stores can be utilized, allowing manufacturers or third parties to provide catalogs, stores, and management apps on existing distribution platforms.
> "CANVAS does not build a store; it provides an environment where stores can be built."
> 
Cameras, Audio, Sensors, Inputs & External Displays
Connected devices are recognized via common APIs and selected by users or applications. Existing standards (such as USB HID) are actively utilized.
Notifications & Settings
CANVAS manages only the minimal common states, while detailed settings can be decoupled into manufacturer apps.
7. Lifecycle, Compatibility & Repair
7.1 Specification Evolution
Original principles and basic rules are rarely changed. However, technical specifications will evolve.
 * Minor changes: Prioritize backward compatibility
 * Major changes: New versions
 * Legacy standards: Maintained as long as possible
 * New features: Additive approach preferred
 * No forced updates on existing products
> "Do not break old things just to add new things."
> 
Existing features will be modified or deprecated only when necessary for safety, security, or legal compliance, with clear reasoning and migration paths provided.
7.2 Repair, Upgrades & Rebuilding
CANVAS does not render older products obsolete. It does not obstruct:
 * Repairs
 * Part replacements
 * Internal board replacements
 * Control IC replacements
 * Connector replacements
 * Firmware updates
 * Upgrades
 * Rebuilding
It leaves room to update internal technologies while preserving reusable assets such as housings and optical systems.
> "Ensure the continued use of previous-generation products as long as possible while avoiding obstruction to repairs, part replacements, upgrades, and rebuilds by manufacturers and other entities."
> 
Compatible marks, Device Trust, and product liability for modified goods shall comply with existing certification and manufacturer responsibility frameworks.
7.3 Failures
In case of anomalies, actions such as warnings, permission limits, power throttling, communication stops, and logical disconnections are executed, maximizing existing safety mechanisms like USB-C and USB PD.
In the event of base failure, gadgets autonomously execute minimal safety procedures such as halting communication, cutting power, saving states, or entering standby.
7.4 Hot-Swapping
Supported gadgets permit replacement during operation. CANVAS OS provides common processes such as status checks, safe stops, power cuts, and re-recognition.
7.5 Multiple Devices & Users
Using the same gadget across multiple CANVAS terminals is not prohibited. Each terminal independently processes trust and permissions. User profiles and data isolation are left to the manufacturers.
8. Standard Publication, IP & Governance
8.1 Openness
CANVAS basic specifications are open:
 * Accessible to anyone
 * Implementable by anyone
 * Developable without being a member company
 * Unbound to specific internal implementation methods
 * No forced disclosure of proprietary technologies
8.2 Intellectual Property
Common parts required for the CANVAS standard are treated as a shared foundation. Meanwhile, proprietary company technologies remain the intellectual property of respective entities.
Distinction Between Proprietary Tech and Proprietary Standards
CANVAS does not hinder companies from developing and utilizing proprietary technologies. Technical differentiation in cameras, audio, AI, cooling, batteries, compression, and sensors is entirely free.
Conversely, unnecessary lock-in using proprietary standards or structures that unreasonably restrict the use by other companies or new entrants conflicts with CANVAS core principles.
> "Winning through technology is free. Winning by closing off connectivity contradicts the philosophy of CANVAS."
> 
Companies are not prohibited from adopting proprietary standards outside of CANVAS. Within CANVAS, competition on technology, quality, price, and service over a common foundation is the baseline. This aims to increase economic incentives for joining an open market rather than legally banning closed standards.
8.3 Governance
CANVAS Original Principles
           │
           ▼
Origin & Basic Principle Review
           │
           ▼
Technical Specifications
           │
           ▼
Implementation by Companies

The purpose of origin reviews is not to judge technological superiority, but to determine:
> "Is this CANVAS?"
> 
It checks for vendor lock-in, suppression of market entry, unreasonable restrictions on user choice, destruction of the separation between the common foundation and specialized gadgets, and monopolistic closing by specific entities.
It does not automatically ban things unmentioned in the origin text, but judges consistency with its spirit.
Technical specifications evolve through proposals and discussions among participating companies, engineers, and researchers. Financial investment alone does not grant the right to rewrite basic principles.
8.4 Joint Development Organization
A lightweight LLC-type joint organization is envisioned for:
 * Specification management
 * Documentation
 * Test environments and coordination
 * Product registration information
 * Working groups
 * Specification interpretation
 * Responsibility organization for common domains
The LLC is not a massive central corporation, but a vessel to maintain the common foundation. Each manufacturer remains responsible for its own products.
9. CANVAS Compatible
The Compatible mark is not a statutory certification, but a reference point for users.
Meaning:
> "Products verified to conform to published CANVAS common standards."
> 
Unregistered products are also permitted to connect as long as they follow the published standards.
Examples of published information:
 * Product name
 * Model number
 * Manufacturer
 * Supported CANVAS version
 * Supported features
 * Registration status
 * Last verification date
 * Known limitations
10. Regulations & Circular Economy
CANVAS assumes compliance with existing laws, safety regulations, and communication standards in respective jurisdictions. Proprietary CANVAS certification does not substitute for statutory certifications, and specific compliance responsibilities rest with each product manufacturer.
Structures facilitating common form factors, standard connections, repairs, replacements, reuse, rebuilding, and cross-generational gadget usage exhibit strong affinity with systems prioritizing resource efficiency, repairability, and circular economies.
CANVAS does not "completely guarantee future regulations," but aims for a structure capable of accommodating increasingly stringent demands regarding maintainability, resource efficiency, and product longevity.
11. Specific Benefits Brought by CANVAS
11.1 Lowering Barriers to Enterprise Entry
Eliminates the need for a single company to develop an entire smartphone, allowing specialized enterprises in cameras, audio, gaming, sensors, communications, storage, healthcare, and industry to enter from their respective domains.
Large enterprises, SMEs, startups, R&D companies, and software firms can compete on the same common foundation.
11.2 Decoupling Product Lifespan of Base and Gadgets
The base can be used long-term through repairs and replacements, while gadgets can span multiple generations. Older products can also be updated with new value via repairs, part replacements, upgrades, and rebuilding.
11.3 A New Market Model of "Premia"
Traditional accessories tend to lose value when device generations change.
With CANVAS, high-performance cameras, optical equipment, acoustic devices, and special sensors can be designed as independent long-term assets.
Purchase
   │
   ▼
Multi-generation Use
   │
   ▼
Repair
   │
   ▼
Internal Upgrade
   │
   ▼
Rebuilding
   │
   ▼
Resale & Secondary Market
   │
   ▼
Long-term Value Retention

This creates a market model where "specialized products accumulate value the longer they are used."
11.4 Repair & Part Standardization
By minimizing base functions and adopting common standards, it facilitates repairs, parts supply, refurbishment, secondary circulation, and remanufacturing.
11.5 Pre-empting Regulatory & Safety Compliance
While assuming compliance with regional regulations and safety standards, it easily accommodates institutional environments emphasizing repairability, resource efficiency, and product longevity.
11.6 User Freedom
Users can select environments suited to their needs—whether for photography, music, gaming, work, outdoor activities, medical research, or industrial use.
> From "buying a finished product prepared by a manufacturer" to "building one's own environment on top of a common foundation."
> 
11.7 New Businesses & Industries
Establishes room for new business domains such as gadgets, HUBs, converters, repair, rebuilding, parts, drivers, secondary/refurbished markets, distribution, and marketplaces.
11.8 Opening Pathways into the Smartphone Industry
CANVAS expands not only product openness but the very method of participating in the smartphone industry.
Traditionally, terminal makers had to integrate cameras, audio, gaming, sensors, communication, and storage into a single finished product. With CANVAS, besides base terminal makers, specialized gadget makers, HUB/converter makers, app/service enterprises, repair/rebuild businesses, and secondary market players can participate from their respective domains.
Base Terminal Makers
        ↕
Gadget Makers ─ HUBS / Converters
        ↕
Apps & Services
        ↕
Repair & Rebuild ─ Secondary / Refurbished Market

Rather than excluding major corporations, CANVAS's market design allows large firms, SMEs, startups, and cross-industry players to compete with distinct strengths on the same common base.
> "CANVAS is not a standard that changes the smartphone, but a standard that changes how you participate in the industry centered around smartphones."
> 
11.9 Changes to Existing Markets
CANVAS does not simply negate existing smartphone markets. However, it presents a market structure distinct from models where a single company vertically integrates terminals, OS, peripherals, and services.
If a market is established where enterprises enter freely, users combine freely, and products can be utilized, repaired, and updated long-term, it can stimulate competition and expand choices in existing markets.
CANVAS aims to serve as a "catalyst" adding new choices to existing smartphone market structures.
12. Market & Economic Models (Provisional)
Provisional cost estimates:
| Model | Estimated Manufacturing Cost | Estimated Retail Price |
|---|---|---|
| CANVAS Standard | Approx. 100,000 JPY | Approx. 130,000 JPY |
| CANVAS High-End | Approx. 120,000 JPY | Approx. 160,000 JPY |
These are rough preliminary assumptions and not fixed prices. Mass production costs, R&D expenses, initial investment, and recovery periods depend on verification by actual manufacturers, component makers, investors, and experts.
12.1 Economic Perspective of CANVAS
CANVAS does not aim to directly boost corporate profits. Through a common foundation, it curbs unnecessary costs such as market fragmentation, redundant investments, individual compatibility maintenance, and isolated infrastructure upkeep, aiming to build a market structure where enterprises do not unjustly lose opportunities to earn profits through competition.
In other words, CANVAS is not a "scheme to make companies rich," but aims to create a market foundation ensuring companies do not lose profit opportunities through competition.
Assumed Profit Opportunities
 * Base terminal makers: Device sales, maintenance, updates
 * Gadget makers: Specialized device sales, repairs, upgrades, rebuilds
 * HUB/converter makers: Connection/conversion hardware sales
 * Software firms: Apps, services, enterprise systems
 * Repair/remediation businesses: Repairs, remanufacturing, refurbishment, secondary distribution
 * Joint organization: Specification management, optional conformance checks, testing environments, registration info management, technical support, etc.
Mandatory fee collection for standard usage itself is basically avoided as it conflicts with free enterprise entry. Operating costs for the joint organization will be supported through optional services or administrative tasks as appropriate.
CANVAS does not guarantee profits. Alongside development and compatibility cost reductions via standardization, standard compliance costs and intensified competition will also occur, meaning final profitability must be verified on a per-business basis.
12.2 Changes in Industrial Structure
Following the introduction of CANVAS, multi-layered markets centered on a common base may form alongside traditional vertically integrated single-company smartphone structures.
               CANVAS Common Foundation
                          │
       ┌──────────────────┼──────────────────┐
       ↓                  ↓                  ↓
 Base Terminal    Specialized Gadgets     Software
       │                  │                  │
       └────────┬─────────┴─────────┬────────┘
                ↓                   ↓
          HUBs / Converters   Repair & Rebuild
                                    │
                                    ↓
                       Secondary / Refurbished Market

In this structure, companies do not need to "build everything" to enter the smartphone market. They can commercialize only their specialized domains and combine them with other companies' products on the common foundation.
12.3 Initial Introduction Strategy
Initial validation of CANVAS value is expected to start not with a simultaneous rollout to the consumer market, but from industrial DX, digital twins, specialized operations, enterprise terminals, and high-end professional applications.
In these markets, requirements for cameras, ranging, temperature/humidity, vibration, special communications, specialized inputs, and industrial I/O vary greatly by application, making it easier to validate the structural advantage of a "common base + application-specific gadgets."
Industrial DX & Specialized Use
              │
              ▼
   Validation via Real Operation
              │
              ▼
    Gadget Tech Maturity
              │
              ▼
     Mass Production / Cost Reduction
              │
              ▼
     Consumer Market
              │
              ▼
 Secondary & Rebuild Market

For digital twin applications, the CANVAS base can serve as a general-purpose on-site computing foundation, adding cameras, LiDAR/ranging, environmental sensors, vibration sensors, and special radios as needed. Sending field data to clouds/AIs to connect with digital twin analysis and simulation is also envisioned.
This does not mean dedicated terminals for specific uses will invariably be eliminated; improvements in TCO, operational efficiency, and maintainability will be evaluated through application-specific demonstrations.
12.4 Global Product Market Trends & CANVAS Compatibility
In global product markets, emphasis is growing on longevity, repairability, component supply, software updates, common connectivity, interoperability, resource efficiency, and transparency of product information for electronic devices including smartphones.
For example, in the EU, eco-design requirements regarding durability, battery life, key component supply, repair info, and OS updates have applied to smartphones and tablets starting June 20, 2025. Furthermore, common USB-C charging applies to mobile phones as of December 28, 2024, and laptops as of April 28, 2026.
Although CANVAS is not designed to match specific regional regulations, its structure—featuring common form factors, standard connections, repair/replacement/reuse, and long-term compatibility—shows strong structural affinity with these market directions.
Market Deployment Timeline Image
| Period | Market Changes |
|---|---|
| Immediately after launch | Base terminal and gadget markets form |
| 1–3 years | Gadget addition, replacement, and repair markets form |
| 3–5 years | Some gadgets continue usage even after base terminal generation updates |
| 5–7 years | Repaired, upgraded, and rebuilt products increase |
| 7+ years | Long-term use including secondary, recycled, and reconfigured markets is established |
While traditional smartphones follow a structure of "purchasing an integrated product and replacing the entire unit upon generational updates," CANVAS targets a market structure of "separating the common base from specialized products, replacing and updating only what is needed."
> "CANVAS does not prophesy future regulations; it applies the already unfolding product market shift of 'use longer, fix, replace, reuse' directly to the massive smartphone market structure."
> 
13. What CANVAS Deliberately Leaves Undefined
 * Gadget internal circuitry
 * Gadget internal OS
 * Detailed UI
 * Branding
 * Proprietary APIs
 * Proprietary algorithms
 * Proprietary cooling
 * Proprietary repair methods
 * Gadget-specific data formats
 * Gadget-specific backup methods
 * Inter-gadget HUB specifications
 * Individual sales methods
 * Proprietary marketplaces
 * Design philosophies per specialized application
CANVAS is not a standard designed to "standardize everything."
> "It is a standard to standardize what is necessary to expand the market, leaving the rest to free competition."
> 
14. CANVAS Responsibility Boundaries
| Domain | CANVAS / Joint Organization | Product Manufacturer |
|---|---|---|
| Common Standards | ○ | Propose & Implement |
| Common APIs | ○ | Implement |
| Device Trust Base | ○ | Provide Device ID |
| Gadget Internal Design | — | ○ |
| Gadget Cooling | — | ○ |
| Gadget Safety Design | Common Conditions | ○ |
| Product Quality | — | ○ |
| Regulatory Compliance | Common Policy | ○ |
| Product Warranty | — | ○ |
| Proprietary IP | — | ○ |
| Repair Methods | Respect Principles | ○ |
| Proprietary UI | — | ○ |
| Dedicated Apps | — | ○ |
15. The Ultimate Goal of CANVAS
What CANVAS aims for is not "building the best smartphone by a single company."
It is building the best common foundation and creating a market where many enterprises can compete on their respective expertise.
Keep the base minimum.
Publish the standards.
Keep internal implementation free.
Make gadgets long-lasting.
Do not obstruct repairs, replacements, upgrades, and rebuilding.
Users choose only what they need.
Enterprises do not own CANVAS itself, but utilize CANVAS as a common foundation to compete.
> "CANVAS is not a standard to remake smartphones.
> It is a common foundation to redesign the very industrial structure of 'making, selling, using, fixing, and updating' centered around smartphones.
> Not only opening the product, but opening the pathway into the market."
> 
Appendix A — Original Principles and Technical Standards
             CANVAS ORIGINAL PRINCIPLES
                         │
                         ▼
         Origin & Basic Principle Review
                         │
                         ▼
             Technical Specifications
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
      Manufacturer     Startup       Researcher
          │              │              │
          └──────────────┼──────────────┘
                         ▼
                  CANVAS Ecosystem

Appendix B — Basic Responsibility Boundaries
                       CANVAS
                          │
             ┌────────────┴────────────┐
             │                         │
      Common Foundation Area     Free Competition Area
             │                         │
      ┌──────┼──────┐          ┌──────┼──────┐
      │      │      │          │      │      │
     Trust   API   Power     Hardware  UI   Software
      │      │      │          │      │      │
      └──────┼──────┘          └──────┼──────┘
             │                         │
    CANVAS Joint Organization   Respective Manufacturers

Appendix C — CANVAS in One Sentence
> "Broadening entry points through standardization, protecting corporate freedom through separation, and accumulating product value through long-term compatibility."
> 
Appendix D — CANVAS Minimum Specification
This chapter outlines what must minimally be established as CANVAS at the time of release, without newly locking down specific numerical specifications or implementation methods.
D.1 Established Minimum Structure
The minimum qualifying condition for CANVAS is having the following structure:
           High-Performance CANVAS Base
                        │
         CANVAS Common Interface
                        │
             Specialized Gadget

The base side holds a common foundation comprising a high-performance SoC, memory, storage, power supply, cooling, communications, displays, and CANVAS OS, separating specialized functions into gadgets as needed.
Gadgets utilize common resources such as base computation, communications, storage, and display via the common interface.
D.2 Minimum Common Functions
At least the following must be established as a common foundation:
 * Mechanical connection and fixation
 * Basic power and data connection using USB-C
 * Individual identification
 * Device Trust
 * Capability / Device Manifest
 * Permission management
 * Power control
 * Runtime Resource Requests
 * Data communication
 * Safe connection and disconnection
 * Firmware updates and recovery
 * Basic policy for CANVAS cross-generational compatibility
D.3 Undefined Aspects
Specific dimensions, tolerances, power limits, communication protocols, encryption methods, official APIs, thermal design values, etc., will be determined through PoCs, safety testing, standardization, and inter-manufacturer discussions.
Appendix E — CANVAS Proof of Concept
A CANVAS PoC is not merely an "experiment connecting USB devices to a smartphone."
The core to be ultimately verified is:
> "Adding interchangeable specialized functions to a high-performance common computing foundation, and enabling those specialized functions to operate utilizing the foundation's resources."
> 
E.1 PoC-1: Interface Concept Proof Using Existing Equipment
Verifying the equivalent of the CANVAS common interface using existing smartphones, SBCs, and development boards.
Existing Computer
       │
       ├─ Mechanical Fixation
       ├─ USB-C
       ├─ Device ID
       ├─ Trust
       ├─ Capability
       ├─ Power
       ├─ Data
       └─ Safe Removal
            │
         Prototype Gadget

This stage aims to confirm the feasibility of the common interface, not to complete the CANVAS terminal itself.
E.2 PoC-2: High-Performance Common Foundation Verification
The stage verifying the true value of CANVAS.
Connecting a specialized gadget to a common base equipped with a high-performance SoC, confirming that the gadget's functions can utilize the base's computation, storage, communication, and display capabilities.
For example, configurations such as:
Camera Gadget
      │
      ▼
Imaging & Preprocessing
      │
      ▼
CANVAS Base
      │
 ┌────┼────┐
 ↓    ↓    ↓
CPU  GPU  NPU
      │
      ▼
Storage, Comm, & Display

Conversely, configurations mounting dedicated ASICs, FPGAs, or ISPs on the gadget side:
Gadget-side Preprocessing
           │
           ▼
      CANVAS Base
           │
           ▼
Final Processing, Storage, & Comm

are also permitted.
The key point is that even when separating the common foundation from specialized functions, sufficient computing resources, power, communications, and OS coordination are established to function as a product.
E.3 PoC-3: Scalability Verification via Multiple Specialized Gadgets
To demonstrate ultimate scalability, multiple different specialized gadgets are used with the same base.
Examples:
 * High-performance camera
 * LiDAR / ranging
 * Environmental sensors
 * Special communications
 * Large capacity storage
 * Specialized input devices
This stage does not aim for simultaneous connection of all gadgets. It verifies that OS resource management, priority control, power/thermal constraints, and safe removal function in practice.
E.4 PoC Success Criteria
At a minimum, verify that:
 * Mechanical safe connection is possible.
 * USB-C and mechanical latches can coexist.
 * Individual gadgets can be identified.
 * Trust states can be managed.
 * Capabilities can be acquired.
 * Power can be managed bidirectionally and safely.
 * Runtime resource requests can be processed.
 * Safe removal during processing is handled.
 * Anomalous gadgets can be restricted and isolated.
 * Room for future generational expansion is preserved.
 * Specialized gadgets can utilize high-performance base computational resources.
 * The basic structure of the common base is maintained even when gadgets are swapped.
E.5 What Does Not Need to Be Completed in PoC
Initial PoCs do not require completion of:
 * Final mass-production housings
 * Final exterior materials
 * Final high-performance SoCs
 * Mass-production molds
 * Completed CANVAS OS
 * Final encryption methods
 * All APIs
 * All gadget categories
 * Full optimization for simultaneous multi-gadget use
 * Final Compatible certification system
The objective of a PoC is not to complete everything, but to validate the structural hypothesis of CANVAS.
Appendix F — Comparison Between CANVAS and the PC Market
The market structure of CANVAS is closer to the PC market than the traditional smartphone market.
| PC Market | CANVAS |
|---|---|
| PC Main Unit | CANVAS Base |
| CPU / GPU / Memory Common Foundation | High-Performance SoC / Memory / Storage, etc. |
| Graphics Card, etc. | Specialized Gadgets |
| Peripherals | CANVAS Gadgets |
| USB / PCIe, etc. | CANVAS Common Interface |
| OS | CANVAS OS |
| PC Manufacturer | Base Terminal Manufacturer |
| Component/Peripheral Maker | Gadget Manufacturer |
| DIY, Replacement, Upgrades | Gadget Replacement, Repair, Rebuilding |
CANVAS does not directly replicate internal PC structures. Its essence lies in:
> "Applying the structure seen in the PC market—where specialized companies compete and cooperate on top of a common foundation—to mobile devices like smartphones."
> 
Furthermore, CANVAS does not aim to replace USB-C, USB PD, existing OSes, app stores, clouds, or authentication tech. It integrates them into a product/market structure of "high-performance common foundation + interchangeable specialized functions" while leveraging existing standards.
Appendix G — Specific Use Cases at Release
Use cases are not restricted by standards, but serve as examples to illustrate the potential of the common foundation.
G.1 Industrial DX & Digital Twins
Field Site
    │
    ▼
CANVAS Base
 + Camera
 + LiDAR / Ranging
 + Temp / Humidity
 + Vibration / Acceleration
 + Special Comm
    │
    ▼
Data Collection
    │
    ▼
Cloud / AI
    │
    ▼
Digital Twin
    │
    ▼
Analysis & Prediction
    │
    ▼
Feedback to Field

Adding required sensors and communication devices per site to serve as a general-purpose on-site computing foundation. Effects on TCO and work efficiency are judged through individual demonstrations.
G.2 Professionals & Creators
 * High-performance camera + external storage → Video production
 * High-quality audio + dedicated inputs → Music production
 * Specialized measuring instruments + communication gear → Technical & maintenance operations
 * Specialized inputs + high-performance processing → Professional terminal use
G.3 General Consumers
 * Focus on photography → High-performance camera gadget
 * Focus on gaming → Gaming input gadget
 * Focus on music → High-quality audio gadget
 * Focus on travel → Large capacity battery, special comms, etc.
Users choose only what they need rather than packing every feature into every device.
Appendix H — Mechanical, Thermal & Power Responsibility Boundaries
H.1 Mechanical Interface
Defined by CANVAS side:
 * Connection positions
 * Guide structures
 * USB-C connection
 * Mechanical latches
 * Connection detection
 * Basic load and safety conditions
 * Ventilation and cooling areas
 * Common interface
Responsible on the gadget manufacturer side:
 * Gadget weight
 * Center of gravity
 * Form factor
 * Impact countermeasures
 * Internal reinforcement
 * Gadget-specific cooling
 * Dedicated structures
Specific loads, torques, insertion/removal durability, and tolerances are determined through prototyping, endurance testing, and safety testing.
H.2 Thermal & Power
The CANVAS Base manages safe operating ranges for its own SoC, battery, internal circuitry, and common power interface.
Gadgets are responsible for their own heat generation, cooling, power supply circuits, dedicated batteries, power consumption, and exterior/heat dissipation structures.
CANVAS OS allocates power and computing resources requested by gadgets within system-wide safe ranges.
CANVAS does not require the base side to uniformly resolve the thermal design of all connected gadgets.
Appendix I — CANVAS Security Threat Model
CANVAS assumes connection with devices including unknown manufacturers and does not unconditionally trust connected equipment.
Representative threats:
 * Malicious gadgets
 * Counterfeit devices posing as genuine products
 * Compromised genuine gadgets
 * Unauthorized data access
 * Abnormal power, communication, or resource requests
 * Base-side compromise or failure
The foundational flow follows:
Device Trust → Capability → Permission Management → Resource Control → Anomaly Detection → Isolation & Disconnection
Being registered does not imply absolute safety; modifying or revoking trust status on an individual unit basis is standard.
Specific methods for cryptographic algorithms, certificate systems, key management, and secure elements are not fixed in this document.
Appendix J — Open Questions
The following are deliberately left open for concretization by experts, enterprises, and researchers, rather than redefining foundational ideas.
J.1 Mechanical Specifications
 * Latch shapes and dimensions
 * Tolerances
 * Insertion/removal durability cycles
 * Allowable loads and moments
 * Contact surface materials
 * Compatibility with waterproof/dustproof structures
J.2 Power & Thermal
 * Specific maximum power between Base and Gadget
 * Power distribution algorithms
 * Specific temperature monitoring thresholds
 * Detailed thermal interfaces
 * Detailed control during multi-battery usage
J.3 Capability / API
 * Formal format for Capability Manifest
 * Formal protocol for Runtime Resource Requests
 * API / ABI
 * Event architecture
 * Gadget SDK
 * Developer test environments
J.4 Device Trust
 * Certificate systems
 * Key management
 * Implementation methods for secure elements
 * Offline trust models
 * Detailed revocation and recovery procedures
J.5 Generational Compatibility
CANVAS does not establish fixed "N-generation guarantees."
Cross-generational compatibility is maintained as much as possible, but compatibility is not forced beyond physical, electrical, communication, safety, regulatory, or other structural technical limits.
Meanwhile, realizing compatibility with older generations via adapters, HUBs, converters, bridges, control boards, or firmware is not prohibited.
J.6 What is Not Decided at Release
CANVAS does not aim to fix all technical specifications at release.
> "Defining the backbone of basic principles, common foundations, expandability, compatibility, trust management, and security, while specific technical specifications built upon them are developed through PoCs, standardization, inter-manufacturer discussions, and expert verification."
> 
Appendix K — Boundaries of Design Decisions in the Public Edition
When discussing CANVAS design, three layers are distinguished:
Original Principles & Basic Rules
               │
               ▼
   What CANVAS "Is"
               │
               ▼
  Common Technical Specifications
               │
               ▼
How to Implement CANVAS
               │
               ▼
Company Products, Technology & Business

Original principles are not easily rewritten. Technical specifications can be updated via PoCs and standardization. Corporate products, technologies, and businesses are free to compete.
The purpose of CANVAS is not to unify everything into one, but to standardize only what expands the market through commonality, leaving the rest to free competition.
Appendix L — Scope Left to Post-Release Discussions
Following publication, proposals are expected from engineers, manufacturers, researchers, security experts, and manufacturing businesses regarding:
 * Feasible mechanical specifications
 * Power and thermal design
 * Communication protocols
 * APIs
 * Security architectures
 * Manufacturing methods
 * Endurance testing
 * Regulatory compliance
 * Standardization procedures
 * PoC implementation
 * Industrial demonstrations
 * Formation of the gadget market
These will be concretized through empirical results and expert discussions within ranges that do not alter the fundamental philosophy of CANVAS.
> "A solid backbone enables discussion. Open details leave room for discussion."
> 

