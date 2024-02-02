For a simple network, we can calculate all shortest paths and load them into some nonvolatile storage on each node

But such a static approach has shortcomings:
- Doesn't handle node or link failures
- Doesn't consider addition of new nodes or links
- Implies edge costs cannot change