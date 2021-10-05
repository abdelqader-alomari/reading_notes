# Read: 08 - OO Design

## Don’t Repeat Yourself - Rule of Three

![DRY](https://th.bing.com/th/id/R.af08481a86c571383af37b90e78039a1?rik=z19QwrgNXIlzhQ&pid=ImgRaw&r=0)

"Don't repeat yourself" (DRY) is a principle of software development aimed at reducing repetition of software patterns, replacing it with abstractions or using data normalization to avoid redundancy.

The DRY principle is stated as "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system". it's apply to include "database schemas, test plans, the build system, even documentation".When the DRY principle is applied successfully, a modification of any single element of a system does not require a change in other logically unrelated elements. Additionally, elements that are logically related all change predictably and uniformly, and are thus kept in sync. Besides using methods and subroutines in their code...

**Wet:** Violations of DRY are typically referred to as WET (Write everything twice) solutions. A DRY approach eliminates that redundancy by using frameworks that reduce or eliminate all those editing tasks except the most important ones, leaving the extensibility of adding new knowledge variables in one place.

**AHA:** AHA (Avoid Hasty Abstractions) is rooted in the understanding that the deeper the investment we've made into abstracting a piece of software, the more we perceive that the cost of that investment can never be recovered (Sunk cost fallacy). Instead of starting with an abstraction, or abstracting at a specific number of duplications, software can be more flexible and robust if abstraction is done when it is needed, or, when the duplication itself has become the barrier and it is known how the abstraction needs to function.

**"Rule of three:**
("Three strikes and you refactor") is a code refactoring rule of thumb to decide when similar pieces of code should be refactored to avoid duplication. It states that two instances of similar code do not require refactoring, but when similar code is used three times, it should be extracted into a new procedure. The rule was popularized by Martin Fowler in Refactoring and attributed to Don Roberts.

Duplication is considered a bad practice in programming because it makes the code harder to maintain. When the rule encoded in a replicated piece of code changes, whoever maintains the code will have to change it in all places correctly.

However, choosing an appropriate design to avoid duplication might benefit from more examples to see patterns in. Attempting premature refactoring risks selecting a wrong abstraction, which can result in worse code as new requirements emerge and will eventually need to be refactored again. The rule implies that the cost of maintenance certainly outweighs the cost of refactoring and potential bad design when there are three copies, and may or may not if there are only two copies." -> Wikipedia.

## You Aren’t Gonna Need It & Minimum Viable Product

**You aren't gonna need it** (YAGNI) is a principle of extreme programming (XP) that states a programmer should not add functionality until deemed necessary. Always implement things when you actually need them, never when you just foresee that you need them.
YAGNI is a principle behind the XP practice of "do the simplest thing that could possibly work" (DTSTTCPW).

**Minimum Viable Product:**
![MVP](https://th.bing.com/th/id/R.28b9b0038496d7cdb9f921ea9764cca2?rik=KPVP2Z7XHXpInQ&pid=ImgRaw&r=0)

Focus on releasing an MVP means that developers potentially avoid lengthy and (ultimately) unnecessary work. Instead, they iterate on working versions and respond to feedback, challenging and validating assumptions about a product's requirements.
As it tests a potential business model to customers to see how the market would react, it is especially useful for new/startup companies who are more concerned with finding out where potential business opportunities exist rather than executing a prefabricated, isolated business model.

Purposes: Be able to test a product hypothesis with minimal resources,accelerate learning, Reduce wasted engineering hours
Get the product to early customers as soon as possible, Base for other products,To establish a builder's abilities in crafting the product required,and Brand building very quickly.

Testing is the essence of minimum viable products. As described above, an MVP seeks to test out whether an idea works in market environments while using the least possible expenditure. This would be beneficial as it reduces the risk of innovating.

The MVP is a strategy that may be used as a part of Blank's customer development methodology that focuses on continual product iteration and refinement based on customer feedback. Additionally, the presentation of non-existing products and features may be refined using web-based statistical hypothesis testing, such as A/B testing.

Business Model Canvas: The Business Model Canvas is used to map in the major components and activities for a company starting out. The minimum viable product can be designed by using selected components of the Business Model Canvas.

Customers: MVP determine whether the selected customer segment actually wants that product, validating the market with the least possible cost, test whether a newly proposed method of value delivery (for example new channels of distribution, innovations in supply chains) works.

Relationship: As its name implies, relationships refer to how a business attracts and maintains its customers by providing them with the treatment and care they expect. MVPs here would be used to learn if customers would better appreciate a new method of relationship building, and true to the MVP concept the test would seek to learn as much as possible whilst sacrificing the least amount of brand equity, reputation, or costs possible.
