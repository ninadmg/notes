---
title: Building Server-Driven Mobile Apps for Web3 world
date: 2023-12-31T20:19:19+05:30
draft: false
---


The world of web3 is a rollercoaster of innovation, pushing boundaries and evolving at breakneck speed. At OKTO, we're building a bridge between this dynamic web3 terrain and the established web2 landscape. But bridging these worlds means mobile app development needs to shift gears – away from slow, siloed processes and towards the lightning-fast iteration of web3.

This blog dives into how we built a server-driven UI framework capable of keeping pace with the web3 whirlwind. Say goodbye to months-long feature rollouts and hello to instant updates controlled directly by product managers!

**The Bottleneck**: Building for a nascent space like web3 demands rapid iteration. Imagine this familiar cycle:

- **Product Manager hatches a brilliant idea:** A sleek new feature or a crucial change emerges.
- **Design sprints into action:** Mockups take shape, visualizing the potential.
- **Engineering tackles the code:** Dev team picks up the baton, translating dreams into lines of code.
- **QA takes the reins:** Testing ensures everything runs like a charm.
- **Finally, release!:** The app store becomes the final hurdle, followed by the agonizing wait for user adoption.

But in the dynamic realm of web3, this well-worn path is a recipe for sluggish progress. Each team's backlog adds another roadblock, stretching the time to market until that brilliant idea feels lost in the dust.

**The Answer: Server-Driven Agility**

Our solution lies in flipping the script. Every page displayed on a mobile app boils down to two crucial decisions:

![how_what](/images/how_what.png)


- **What data to show?** The information users crave.
- **How to present it?** The visual design that brings it to life.

Traditionally, these choices reside within the app itself, chained to the slow release cycle. But what if we handed the reins to the product manager, empowering them to tweak content and presentation on the fly?

That's exactly what our server-driven UI framework achieves. By shifting these critical decisions to the server, we break free from the app store shackles. 

  

**Tech Deepdive**

  

Time to peek behind the curtain and explore the technical underpinnings that make our server-driven UI framework tick. Here's a deep dive into the key architectural elements:

**Widget-Centric World:**

Taking a cue from Flutter's elegant approach, we embrace a widget-based architecture. Every visual component on the screen is represented as a widget, possessing its properties and a collection of child widgets. This modular structure enables flexible UI composition.


**API Schema: The Blueprint for Server-Client Communication**

Every widget has an ID, some properties of its own and a list of children. so let's start from there. 

```
{
widget_id: "name of widget"
data:{}
children:[]
}
```

Not all data displayed on the screen necessarily originates from the SDUI server. Sometimes, it might come from other services. To handle this, the framework provides a powerful data binding mechanism.

- **Flexible Data Sources:** The SDUI framework can fetch data from various sources, including APIs and local databases. The server-side API provides instructions on how to retrieve the data for each widget.
- **Unified Data Model:** To simplify data manipulation, the framework utilizes a common data model. This model acts as a bridge between diverse data sources and ensures consistent data representation within the widgets.
- **Mapping for Transformation:** The SDUI API response also includes mapping instructions. These instructions define how to transform the retrieved data into the desired format for the widget's data model.

![flow](/images/engine_flow.png)

This means that the data API schema looks something like this  

```
data: {
	bindings: [
		{
		source_type: api
		source: http://....
		mapping: {
			title: token.name
			subtitle: token.price}
		}
	]
} 
```

here the source API would return something like

```
{
token:{
	name: "bitcoin"
	price:"$234534.34"
	}
}
```

Thanks to this flexibility, a single widget can seamlessly combine data from multiple sources. 

Let's peel back the layers and explore the core architecture of our SDUI library. Here are the key components:

1. **Repository:** This layer acts as the gatekeeper of data, responsible for storing information and handling API calls. It provides an interface for the SDUI engine to fetch and manage data.
2. **SDUI Engine:** The heart of the framework, this layer is where the magic happens. It transforms API responses into view model objects, orchestrating the construction of the UI.
3. **Unified Data Model:** These objects serve as the backbone of the UI, holding the data that powers each component's visual representation. They provide a structured way to encapsulate and manage the information needed for rendering.
4. **Widgets:** The final layer, widgets are the building blocks that assemble the visual interface. They take the Unified Data Model as input and translate them into the UI elements seen on the screen.

**How It Works:**

1. **API Response to Tree Structure:** The SDUI engine parses the API response, constructing a hierarchical widget tree. This tree mirrors the intended structure of the UI, laying the foundation for rendering.
2. **Recursive Data Fetching:** Starting with the root widget, the engine iteratively fetches the data required for each widget and its children (This includes additional API calls if the data needs to be fetched from another service). This process continues recursively until all leaf widgets have their corresponding view models populated.
3. **Unified Data Model Tree Creation:** As data is fetched, the engine crafts a view model tree that mirrors the widget tree. This tree holds the structured data that will power the visual representation of the UI.
4. **Mapping to Widget Tree:** Once the Unified Data Model tree is complete, the framework seamlessly maps it to the widget tree. This mapping triggers the rendering process, bringing the UI to life on the screen.

We've just explored the core here. But the journey doesn't end here.

In Part 2 of this blog series, we'll delve deeper into the intricate workings of the SDUI framework, tackling crucial aspects like:

- **Analytics:** How do we seamlessly capture user interactions and measure the impact of dynamic content?
- **Actions:** How can users engage with the UI, triggering actions
- **Navigation:** How do we navigate between different views 
- **Edge Cases:** How do we handle widgets that need data from other widgets