---
title: Building Server-Driven Mobile Apps for Web3 world : Part 2
date: 2023-5-6T20:19:19+05:30
draft: true
---

In the first part of this blog series, we explored the benefits of server-driven apps and how they allow you to design applications where both the data and layout are controlled by the server. If you haven't read it yet, you can find it [here](https://ninadmg.in/posts/building-server-driven-mobile-apps-for-web3-world/)

While displaying data is essential, it's only half the story. This part dives into two key aspects:
**User Actions:** Users shouldn't just see data; they should be able to interact with it. We'll discuss how to design server-driven apps that facilitate user actions.
**Analytics:** Understanding how users interact with your app is crucial. We'll explore how server-driven apps can provide valuable analytics data to your product team.

### Actions

In any application, users need ways to interact. For example, clicking a button to move to the next page. In a server-driven world (SDUI), we achieve this by separating user interactions into two parts:

#### Events

These are user actions like taps, long presses, scrolls, etc. Any event, whether user-driven (e.g., "scrolled") or system-driven (e.g., "image loaded"), triggers an action through the SDUI framework. A single event can trigger multiple actions.

#### Actions 

These are the consequences of events. Actions can include things like navigating to a new page or sending an analytics event. Importantly, actions can access properties from the specific UI element (widget) where the user interacted.

By dividing the UI into a set of widgets, events, and actions, we create a modular system. This allows teams to easily mix and match these components to build different functionalities without needing extra coding for every new feature.
Furthermore, since a single event can trigger multiple actions, you can achieve complex interactions efficiently. For example, clicking a button can both open a new page and fire an analytics event to track user engagement with that specific button.

### Analytics

Firing analytics events is not different from any other action.
Events are triggered corresponding to some actions, and one type of action can be specifically designed for firing analytics events.
Here's the power of this approach: since actions have direct access to the widget's properties, they can easily extract relevant data (e.g., button ID, clicked item name) and fire them as analytics events. This simplifies data collection and provides richer insights into user behaviour.


