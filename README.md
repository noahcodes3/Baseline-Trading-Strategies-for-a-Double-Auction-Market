# Baseline-Trading-Strategies-for-a-Double-Auction-Market
Modular agent-based trading simulator in Python exploring signal-driven and zero-intelligence strategies within a discrete market environment.

### Agent-Based Trading Simulator

A modular, object-oriented trading simulator implemented in Python, designed to explore strategy abstraction, order validation, and signal-driven execution within a simplified discrete-time market environment. This project models the behaviour of autonomous trading agents and provides a structured framework for testing different decision-making rules under capital and inventory constraints.

### Project Motivation

Financial markets can be analysed as interacting agents operating under changes to information asymmetry, capital constraints, and execution rules. 

This simulator was built to:
- Explore agent-based modelling concepts
- Implement a modular trading strategy design
- Enforce strict order validation logic
- Simulate portfolio state evolution over time
- Provide a clean framework for strategy experimentation

The architecture is intentionally extensible, allowing additional strategies and market mechanics to be introduced without modifying core components.

### Architecture Overview

The project is structured around a clear separation of concerns. Each trading strategy inherits from a common interface and implements:

- place_order(signal, price)

This returns a structured order object containing:
- Price
- Quantity
- Buy/Sell/Hold
- Trader ID

This abstraction allows strategies to be swapped without altering the simulation engine.

### Agent State

Each agent maintains:
- Cash balance
- Share holdings
- Trader identifier

Orders are validated against:
- Available capital
- Inventory constraints

This prevents invalid trades (e.g. selling without holdings).

### Simulation Layer

Test_Simulator.py runs:
- Signal generation
- Strategy selection
- Order placement
- State updates

This enables rapid experimentation with different behavioural models.

### Implemented Strategies

Zero-Intelligence Agent:
- Submits randomised buy/sell decisions subject to portfolio constraints.
- Used as a behavioural baseline.

Signal-Following Agent
- Places directional trades based on an informational signal.
- Captures simple information-driven behaviour in a controlled setting.

Mixed Strategy
- Randomly samples from available strategies based on predefined probabilities.
- Used to simulate heterogeneous market participants.

### Monte Carlo Simulation & Analysis

The simulator includes a Monte Carlo experiment (100 simulations × 100 timesteps) to analyse aggregate market dynamics under stochastic signal generation.

Outputs include:

Price Evolution
- Mean price path across simulations
- 10–90% uncertainty band
- Visualises emergent price drift under aggregated order flow

Action Frequency
- Aggregate Buy/Sell/Hold counts across all simulations.
- Provides insight into behavioural intensity and directional bias.

Inventory Dynamics
- Mean inventory trajectories for each trader type
- Highlights risk accumulation
- Identifying behavioural divergence

Signal Distribution
- Histogram of generated signals to verify distributional assumptions.

Execution 
- currently modelled using a simplified immediate-fill mechanism.
- A full double-auction clearing engine will be integrated into the complete model.

### How can you run this code

Clone the repository:
- git clone https://github.com/yourusername/your-repo-name.git
- cd your-repo-name

Run the simulator:
- python Trading\ Strategies/Test_Simulator.py
- No external dependencies are required beyond standard Python libraries.

### Design Principles

- Clean object-oriented structure
- Strategy abstraction via a common interface
- Explicit order validation
- Clear separation between strategy logic and simulation engine
- Extensibility for future market mechanisms

### Potential Extensions

Future improvements may include:
- Order book depth modelling
- Market impact dynamics
- Performance analytics (Sharpe ratio, drawdown)
- Monte Carlo simulations
- Vectorised backtesting framework
- Risk constraints and leverage

### Technical Stack

- Python 3
- Object-Oriented Programming
- Agent-Based Modelling Concepts

### Disclaimer

This simulator is a simplified educational framework designed to explore trading logic and agent behaviour. It does not represent real market conditions or execution mechanics. 
