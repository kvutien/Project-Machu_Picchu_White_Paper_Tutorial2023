# Project-Machu Picchu White Paper
*(version January 2023)*

##	What is Machu Picchu?
Machu Picchu is a decentralized and trusted social network, where the Persons-in-Need ("**PnD**") post their profiles, their activities, their needs, while keeping ownership of their data. 

Using Machu Picchu, all services to the **PnD** can use this trusted social network to provide assistance to these beneficiaies via decentralized protocols and smart contracts.

Watch the 1-minute video here: https://youtu.be/joPwVTsLojU

##	Reading guide
This white paper can also be read in a reverse way, as a tutorial to learn coding blockchain, showing hands-on how current state-of-the-art technology can help change significatively the efficiency of humanitarian actions.
- After reading the white paper, if you —as a humanitarian executive— are convinced that this approach may help ease existing pains, you can follow the tutorial part, learning how to implement it for real. No prerequisite in programming.

- To read the blockchain programming Tutorial, go here: [*Tutorial Link*](./README_2.md)
  
Finally, this document can serve as input for hackathon teams, as a guide and some prototype components, for them to use the purpose, hack advanced tools to a purposeful result and win.

![reading guide](./images/00-Reading%20guide.png)

# 1.Machu Picchu Big Picture
##	1.1 Introduction to the concept of a *Strategy-Driving Policy*
A Policy is in general composed of many steps, among them writing a White Paper. To better understand the process, let's see the example of a nation's military policy. Then we will transpose this example to Machu Picchu. 
Such a policy is composed of:
1.	**A White Paper**, to set out the final purpose of the action and the means to accomplish it. 

- For example, would an army's mission be only for territorial defense and deterrence, or rather for proactive attack, and can it include civil emergency rescue tasks? would eventual attacks be carried out as a flash operation or be capable of a sustained duration war? is there any large maritime area or any oceanic island involved? are there remote projections to support an alliance? are there any new threats (cyberwar, space war)? what are the limiting means (budget, personnel, technology) to carry out this mission? what are the weaknesses and the strengths?

Sample: https://english.defensie.nl/downloads/publications/2022/07/19/defence-white-paper-2022

The below White Paper describes what is the mission of Machu Picchu.

2.	**An implementation strategy**, to identify the skills and industry to be acquired and supported.
-	Budget: what budget is available and how would tradeoffs be made?
-	Base weapons: what vectors are needed for ground, for naval, for air? respectively for attack and for defense?
-	Support technology: what support technologies are required? For example turbo-engines, micro-electronics, cryptography, communication and transport network?

This White Paper lists the technologies that Machu Picchu needs (blockchain, decentralized storage, market making protocols, Earth Observation, mobile applications etc.).

3.	**An acquisition & maintenance strategy**, to guide the logistics
-	Acquisition:  can the arms and munitions be externally procured, or a national know-how needs be developed? what skills exist? which ones must still be acquired? for which arms (ground-sea-air)? on which time scale? For example, despite its huge investment since a long time, China is still much dependent on Russia for its air force because lack of the engine technology.
-	Maintenance: what levels of expertise are needed for base maintenance, field maintenance? what level of spare supplies? how are they distributed?

4.	**A doctrine and a training strategy**, to bring coherency in operations and guide technological developments.
-	Doctrine: national defense or attack? flash operations or long duration war? conscripts or professionals? hierarchical command flow or autonomous initiative? multi-vector coordinated operations vs. isolated and specialized operations?
-	Training (depends on doctrine): what minimum proficiency? how much and how often run exercises? which depth of realism?

5.	**A lobbying and funding strategy**: what talk lines to use to obtain public support and funding? what technology development and use cases to put forward?

## 1.2 Application to Machu Picchu
1.	**White Paper**, to set out the final purpose of the action. 
- Machu Picchu is a collaborative open-source project. It aims at producing and maintaining accurate data about the persons-in-need ("**PnD**").
- For this purpose, Machu Picchu lets each **PnD** publish on the Internet their profile and their needs (a kind of LinkedIn profile). These people keep ownership of their data and can selectively allow humanitarians, governmental agencies and any service provider to access these data against micro-payments, to best program their aids and services. 
- To achieve this purpose, Machu Picchu provides ready-made tools for each type of stakeholder: the **PnD**, the field sponsor, the humanitarian organization. Peripheral stakeholders like service providers (banks, insurers, input suppliers, food companies…) will develop their own tools.
- The final purpose is to use the stat-of-the-art technologies to enhance financial inclusion and reduce the costs and administrative burdens on humanitarian aids.
2.	**Implementation strategy** 
Machu Picchu is open source. It uses the following technologies:
-	the Internet and the mobile network to distribute and collect data (SMS or UDDS),
-	the mobile apps to implement the frontend (user interface) and avoid serving screens from centralized computers,
-	the blockchain and decentralized storage to achieve resilient data distribution and to implement the backend processes,
-	the low-cost Single Board Computers of type Raspberry Pi to run decentralized storage and to validate transactions,
-	the Earth Observation and open mapping data to monitor crop status,
-	blockchain security and cyber security.

At the initial phase, Machu Picchu implementation will be ad-hoc and based on available funding and needs. Prototyping will be done in hackathons, or with humanitarian partners if they can fund it.
Priority is given to functions to facilitate adoption by the field sponsor, then to functions useful to the PnD, then to the needs of the international Helper Institutions.

3.	**Acquisition & maintenance**
- Network skills
- Blockchain and Decentralized Finance (DeFi) skills
- Earth Observation 

# 2. Machu Picchu White Paper
This document is the 2nd draft of the Machu Picchu White Paper. The first one dates back in October 2021. The following White Paper describes:
1.	The humanitarian context and the pains each community faces,
2.	How the answer brought by Machu Picchu is structured,
3.	How each of the pieces of the solution contributes to it,
4.	Where we go from here.

## 2.1	Humanitarian Operating layers

![humanitarian layers](./images/01-Humanitarian%20operating%20layers.png)

As laypersons **Donors**, we receive solicitation and information from **Helper Institutions** and we donate to them, mostly to those who are officially recognized as such. Examples of Helper institutions are:
-	UNICEF
-	Red Cross
-	Caritas
-	Mercy Corps
-	etc.

The Helper Institutions can themselves be organized in layers globally, by country, by region.

The **Persons-in-Need ("PnD")** are supported by field staff persons, who work for **Local Field Helper Associations**, at the local level of each country and region. These associations are not known to us the individual donors who live in developed countries, but they are known to and agreed by international Helper Institutions. 

This separation of circuits optimizes the relationships. 
-	between Donors and Helper Institutions, relationship is many-to-one, collecting funds. 
-	between Local Field Helper Associations and Persons-in-Need, relationship is one-to-many, distributing aids.

The two circuits are connected when the Helper Institutions collect funds and meet with Local Helper Associations to build programs and allocate the funds.

For Helper Institutions to build programs, distribute funds and inform donors of the correct use of them, they are fed with information and reporting coming from local actors of Helper Associations. It is well established that the quality of these data is degraded on their way up, from the field operations to the headquarters of Helper Institutions.

# 2.2	Identified Pains
Helper Institutions and Local Helper Associations together are doing a wonderful job, but they are all hampered by the 2 following pains:

### Lack of reliable data about the target population:
In a report of November 2020, https://www.hivenetwork.online/blockchain-for-good/, the following weaknesses were cited:
-	silo effect between different Helper Institutions and between programs of a same institution, difficulty to reconcile identity systems to improve traceability,
-	data inconsistent naming and semantics between short-term relief programs and long-term development and education programs,
-	outdated information for a same person, leading to incoherencies,
-	etc.

### Excessive financial and prudential costs overhead: 
For lack of adequate decentralized technology, current money flows and insurance process are concentrated in a small number of licensed financial operators. This concentration requires elaborate reporting to make sure that banks don't make hazardous use of money that is not theirs and that insurers remain solvent for the risks they accepted to bear.

In addition existing regulations focus more on anti-money laundering & combating the financing of terrorism than on facilitating assistance to the poor. By consequence the financial overhead is very high relative to the small size of each single operation.

## 2.3	Possible solution by Decentralized Finance
In Traditional Finance, a Market Maker is an entity that has deep pockets enough to absorb the random events that may happen when doing trading and commerce. For example:
-	The average person has a monthly income of a few thousands USD. To buy a car worth a few dozens of thousands USD or a house worth a few hundreds of thousands USD, they take a loan from a bank. The bank is a Market Maker who accepts to advance the money and by paid back in settlements.
-	The average person has a monthly income of a few thousands USD. To cover a car accident of the same magnitude, or a health treatment costing a few hundred of thousands USD, they contract an insurance from an insurer. The insurer is a Market Maker who accepts to cover a risk against a punctual, monthly or annual premium.
-	The average farmer wants to exchange a few hundreds USD worth timber to obtain the equivalent in cereals, or a company wants to exchange local money to get some hundreds of thousands USD to import a product. They go to a commodity exchange or a currency exchange. The exchange is composed of Market Makers who always have enough currency liquidity in a pair of goods to do the exchange in either way.

In Traditional Finance, Market Makers must have deep pockets to average out the risks among a large number of customers. Wealth means power, this explains why governments created strict reporting, reserve and solvency regulations to protect the customers.

With the blockchain's fast settlement and low cost of transaction, researchers have designed protocols where any person who is interested can participate using their own **Liquidity Pool** (LP) managed by a smart contract called an **Automated Market Maker** (AMM). The latter makes sure that the money of each LP is locked and dedicated to a sole purpose.

- *We observe that this is a **community-based practice** that **existed since centuries** in antique and medieval rural communities, for banking, self-help and goods exchange.*

![decentralized finance](./images/02-Decentralized%20Finance.png)

Decentralized Banking and Decentralized Exchange have already been implemented successfully, handling billions USD of Total Locked Value (TVL). A **commented source code** of Uniswap is available in https://github.com/casweeney/Uniswap-ALL-IN-ONE.

A decentralized risk-sharing using AMM protocol has been published by University of Basle in December 2023, opening way to Decentralized Insurance. The protocol is described in https://arxiv.org/abs/2212.10308. The **source code** is available in https://github.com/cifunibas/decentralized-insurance.

However, the current official regulations for reporting, reserve and solvency remain focused on regulating a market made of a small number of registered liable entities. These rules are not applicable to scattered participation and peer-to-peer operations. Regulators are still struggling to understand how to adapt them.

## 2.4	Machu Picchu Solution
The current technologies allow affordable networking, affordable computing and affordable storage. This is bringing progressively decentralized solutions, using cryptography to secure ownership and integrity of the data, straight at design stage.

Let's illustrate with a story how it works:
-	The Persons-in-Need ("PnD") post and maintain their data using SMS on a simple cellular phone, in conjunction with a “sponsor person” who has a smartphone and a tablet and can access the blockchain. The data is secured by use of multi-signature involving the cryptographic keys of the PnD and of the sponsor person. This sponsor person can be their chief of village, their trusted NGO field staff, or any trusted person who has a smartphone or a tablet that can do blockchain transactions.
-	The credentials of the PnD (name, signature, location, owned money etc.) are stored on the blockchain. The data are stored on IPFS (a decentralized storage that is backed-up on several “nodes”) or equivalent. The cryptographic digests (the “hash”) of the data, required to access it, are stored on the blockchain, as well as a list of entities allowed to read the data. This keeps the data under ownership of the PnD and complies with the GDPR data protection regulation.
-	Any helper organization can agree with a PnD and the sponsor person to have read access to the data of this person-in-need against a promise of payment of some Cash & Voucher assistance. This promise is materialized as a blockchain fungible token. The higher the quality (accuracy, age of data, match with the purpose) the higher the promised payment. This rewards the PnD and the sponsor person to maintain the data up to date and in timely fashion.

![Machu Picchu solution](./images/03-Machu%20Picchu%20solution.png)

In Web 2, the GAFA built their fortune by making each user maintain personal data for the benefit of the central operator who monetize them. In the Web 3 world and in Machu Picchu, each user maintains personal data for their personal benefit. The privacy protection of GDPR is satisfied by design.

## 2.5	Benefits of Machu Picchu solution
The promises of payment are materialized as blockchain fungible tokens (crypto-currencies, stable coins or Central Bank Digital Currencies). Therefore, the reporting to donors of the use of the funds is immediate, using many existing “blockchain explorers”.

These tokens can be redeemed at the NGOs as cash, as mobile money, or used directly as digital currency (stablecoins or Central Bank Digital Currency). They can also be exchanged at a DEX (Decentralized Exchange) against other reputable NGO tokens that the local bank can accept.

In addition to the assistance purpose, among many others, one can consider financial services such as
-	fidelity rewards from agri-food international companies. Nestlé, Lipton, Mars and Pepsi do this to motivate their providers to follow their recommended culture practices.
-	fidelity rewards from international input providers (seeds, fertilizers, pesticides etc.).
-	incentives from governmental agencies: child education and protection, gender equality, health practices, carbon practices etc.
-	mutual protection against crop loss or international price variations (this is NOT insurance, but a self-help community compatible with the Islamic "takaful" definition).
-	informal credit rating data.

Important points such quality of the data, reputation of the sponsor persons and of the village, incentive to operate a data storage node, values of the tokens etc. have technical solutions that have been implemented as commercial blockchain protocols such as Ocean Protocol (data quality), Filecoin (storage incentive) etc. They are not explained further in this White Paper.

# 3	Machu Picchu Implementation 
## 3.1	Machu Picchu Structure 
Machu Picchu has a B2B2C business model. It offers services to all organizations that are in direct contact with the Persons-in-Need ("**PnD**") world-wide. By adhering to the Machu Picchu community, these organizations have access to quality data to accomplish their missions.

We can compare Machu Picchu with the USA highway Route 66. It is a public service. It has given birth around it to a successful economy composed of hotels, restaurants, garages, industries, doctors, etc. in all cities along this Route 66. Nobody owns Route 66; nobody owns Machu Picchu either. With Machu Picchu, “*data is a public service*”.

When there is a solvable need, there is a business. Machu Picchu’s business model is composed of:
-	**A foundation**: a community of operations composed of all organizations providing services to the persons-in-need,
-	**A forum**: a community of software developers for good, that is open source and collaborative (as cooperative as Linux, Wikipedia, Open Street Map etc.), for example on Discord,
-	**A commercial company**: a paid service that provides specific training, consultancy, and development services to the market.

Software-wise, Machu Picchu is a LEGO box of software components . Each organization picks what suits best their field needs and develop the complements. They are strongly advised (but not obliged) to share in open source their developments. It’s the MIT standard license.

Any developer may contribute to the software building blocks when possible, and whatever they feel useful to Machu Picchu.

There is no strictly mandatory architecture because the field needs are very diverse, and the possibilities of collaborative innovation are vast.

If an organization has a precise need and can finance the development of the solution, Machu Picchu can generate a sub-project with a different name and manage this development is a more “business-like” manner. It becomes a consultancy sub-project.
## 3.2	Machu Picchu Implementation
Machu Picchu is a decentralized social network, where the data of each participant remain property of each person, unlike current centralized social networks that own and monetize the data of their users, as in Facebook, Tweeter, WhatsApp, LinkedIn etc.

The other differences are:
-	it has 2 distinct categories of users: write-only users are the **Persons-in-Need (PnD)** and read-only users are the **Helper Organizations**,
-	users don't make "friends". They can "support" the existence and credibility of other users and this community-sovereign authorization and authentication is the only identity system in Machu Picchu. There are several levels of credibility a person can give.

The implementation of Machu Picchu is made by possible by all the decentralized infrastructure and tools that are available as Open-Source. Because Machu Picchu is bottom-up, final targets hardware must be of low acquisition cost, low power consumption and ease of replacement (and ease of use).
-	frontend is composed of mobile equipment: feature phones, smartphones or tablets
-	backend is composed of Single Board Computers (Raspberry-style) and Solid-State Disks (SSD).

![Machu Picchu components](./images/04-Machu%20Picchu%20components.png)

## 3.3	Machu Picchu Doctrine

Doctrine is a list of priorities, of target markets (where we stop), and how to make trade-offs when a choice must be done. It guides the decisions to develop, deploy, train, acquire users and customers.
Machu Picchu's implementation doctrine is to rely on Internet and SMS or UDDS, using decentralized, low cost – low consumption equipment (tablets, feature phone, Raspberry Pi).

Development keeps the blockchain part reduced to the minimum required. All the business logic and business data are on the frontend mobiles or on the legacy architectures and servers of Helper Associations and Helper Institutions.
Deployment priority is bottom-up.

Training is focused on field sponsors' staff to use simple software tools.
## 3.4	Machu Picchu Acquisition Strategy
### 3.4.1	The progression
The doctrine of Machu Picchu is to proceed bottom-up. This means that focus is made first on the end-users, who unfortunately can't afford paying development nor services nor learning blockchain. For this reason and without funding, Machu Picchu has to first acquire leveraging sources. The resources that Machu Picchu can leverage are the community of Developers-for-Good and one or several Field Local Helper Associations.

![Machu Picchu Acquisition Strategy](./images/05-Machu%20Picchu%20Acquisition%20Strategy.png)

The progression is:
-	In the initial phase, Machu Picchu implementation is ad-hoc and based on available funding and needs. With developers-for-Good, Machu Picchu participates to hackathons and makes prototypes of interesting technologies (see chapter "Machu Picchu Implementation" above).
-	After the hackathons, re-engineer the prototypes to make reusable toolbox components, document their usage, make tutorials. Priority is given to functions to facilitate adoption by the field sponsor / field partner, then to functions useful to the Person-in-Need (PnD), then to the needs of the international Helper Institutions.
-	When the toolbox is sufficiently populated to make viable prototypes, convince one or several local Helper Associations to give a try by deploying an usable pilot on the field. They will organize the workflow and training. If needed, they will raise the fundings necessary for field operations.
-	When the pilots made their proofs, together with local Helper Associations, convince International Helper Institutes to join and add functions as required. These organizations will also develop if needed donor reporting apps using blockchain explorers, for their own specifications.
### 3.4.2	What's in for each stakeholder
Each stakeholder has a specific concern to satisfy:
-	The Person-in-Need main concern is "*how can I feed my kids and myself today?*"
-	The local Helper Association main concern is "*how can I anticipate on the survival of the communities of Person-in-Need I'm sponsoring?*"
-	The international Helper Institution main concern is "*how can I convince donors to fund my activities?*"

To be successful, Machu Picchu addresses these concerns at every step.
-	For the **PnD** and in routine mode, Machu Picchu brings a simple way to receive financial aid from international Helper Institutions by the quality of personal data on the **PnD** and the easy way to distribute digital cash. However, at the beginning, there is no significant funding for this purpose. Machu Picchu could instore a simple decentralized lottery where can participate only the PnD who keep regular update of their data in Machu Picchu.
-	For the local Helper Association, Machu Picchu brings a mobile app to allow the field staff to keep contact with the sponsored persons, and a low cost, no fuss and resilient server based on Single Board Computer (SBC) like a Raspberry Pi that uses less than 10 UAD per year of electricity and stores data for thousands of PnD as NTFS and blockchain records. 

To start immediately, Machu Picchu includes a free satellite Earth Observation tool to monitor the crops of these persons, anticipate the evolutions and actions required. An example prototype exists, "Steve Observer": https://youtu.be/joPwVTsLojU.

![Machu Picchu Earth Observation](./images/05a-Machu%20Picchu%20Steve%20Observer.png)

-	For the international Helper Institution, Machu Picchu brings reliable data, available without any complex maintenance, and instant reporting of the use of the funds to donors.

Data is stored as flat data (noSQL), in large quantities, in resilient IPFS-like servers. Tools to traverse the data are available in open-source and are battlefield tested.
### 3.4.3	The final target: inclusive finance
When a critical mass of Persons-in-Need (PnD) is achieved (a lot), Machu Picchu can start and implement open-source Decentralized Finance (DeFi) and Decentralized Insurance (DeInsur). 

True Decentralized Finance and Decentralized Insurance are ancestral practices. The difference between Traditional Finance and Decentralized Finance has been described in the above chapter "White Paper", section "Possible solution by Decentralized Finance".
-	**Decentralized payment**: Bitcoin, 2008
-	**Decentralized loans**: MakerDAO, 2017
-	**Decentralized trading**: Uniswap, 2018
-	**Decentralized risk-sharing**: Basle University, 2022
Source code here:
-	Uniswap: https://github.com/casweeney/Uniswap-ALL-IN-ONE
-	Risk-Sharing: https://github.com/cifunibas/decentralized-insurance

# Where do we go from here?
Here ends the White paper of Machu Picchu. If you are convinced, Continue reading. The next step is the coding tutorial using Machu Picchu as an application theme.
