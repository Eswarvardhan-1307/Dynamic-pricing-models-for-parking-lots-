# Dynamic-pricing-models-for-parking-lots-

## A Breif Overview of the Project 

Dynamic Pricing Models for Parking Lots with Real-Time Simulation
This project simulates dynamic pricing for urban parking spaces for 14 urban parking lots to improve their utilization. 
using real time real time data streams ,Pathway(for streaming),and Bokeh(for visualization).
Our main goal is to build a pricing engine that adjusts parking fees in real-time based on a variety of factors.

Objective: Develop a pricing model that updates a base price of $10 in real-time. The price changes should be smooth and explainable,
Methodology: You are required to build three models from scratch using only Python, Pandas, and Numpy

The Models:
Baseline Linear Model: A simple starting point where the price increases linearly with the parking lot's occupancy.
Demand-Based Model: A more advanced model where you create a demand function based on occupancy, queue length, traffic, and other features to set the price.
Competitive Pricing Model (Optional): An advanced model that incorporates the prices of nearby competitor parking lots, determined by their geographic location.
These models caluculates prices based on demand , occupancy, traffic, and nearby competitors 


## 🧰 Tech Stack
- **Python** – Core programming language
- **Pandas, NumPy** – Data preprocessing and for Exploratory data analysis
- **Pathway** – Real-time streaming and processing engine
- **Bokeh** – Real-time visualization of pricing
- **Google Colab** – Development IDE environment
- **Mermaid** – Architecture diagrams


## 🗺 Architecture Diagram

![Architecture Diagram](architecture.png) 


## 🧠 Project Architecture & Workflow

1. *Data Source*  
   - Simulated from historical CSV dataset of parking data  
   - Contains occupancy, traffic, queue length, special day indicators, etc.

2. *Streaming with Pathway*  
   - Data is streamed row-by-row to simulate real-time updates  
   - Uses pw.io.csv.read() in streaming mode with timestamp parsing  

3. *Feature Processing*  
   - Data cleaning and feature transformation (occupancy ratio, traffic weights, etc.)
   - Features are transformed in Real Time
   - such as  Occupancy by time , Occupancy over a hour of the day , queue lemgth over the time , traffic condition ,
   occupancy vs traffic condtions , occupancy by vehicle type and its traffic conditions 

4. *Pricing Models Implemented*  
   - *Model 1:* Linear pricing  based on (occupancy only)  
   - *Model 2:* Demand-based pricing using multiple features  
   - *Model 3:* Competitive pricing based on nearby lot prices (only for one lot) , adjusted based on nearby competitor prices  

5. *Price Output*  
   - Prices are calculated in real-time and output continuously  
   - Final prices are streamed to a live dashboard
   -  Final price is Computed using @pw.udf logic inside the pathway stream 

6. *Bokeh Visualizations*  
   - Plots update in real time using ColumnDataSource.stream()  
   - Shows how prices evolve for each model (especially Model 3)
  
7. Of course, here is a more detailed elaboration on the six points of the project architecture.

### 🧠 Project Architecture & Workflow

1.  ***Data Source***
    A historical CSV file containing past parking data is used to create a realistic, simulated live data stream. [cite_start]This file includes key information for each parking lot, such as its current **occupancy**, nearby **traffic** levels, the number of cars in the **queue**, and indicators for **special days** like holidays or events[cite: 7, 10].

2.  ***Streaming with Pathway***
    [cite_start]Pathway's `pw.io.csv.read` function ingests the data row-by-row from the CSV file in **streaming mode**[cite: 74]. This process simulates a real-time environment where data arrives sequentially. [cite_start]Pathway intelligently manages the data by its timestamp, ensuring that the information is processed in the correct chronological order as if it were coming from a live sensor network[cite: 74].

3.  ***Feature Processing***
    As the raw data streams in, it is processed in real-time to create more meaningful features for the pricing models. [cite_start]This involves cleaning the data and performing transformations, such as calculating the **occupancy rate** (occupancy divided by capacity) or converting categorical traffic levels (like "Low" or "High") into numerical weights[cite: 75].

4.  ***Pricing Models Implemented***
    [cite_start]Three distinct pricing models are built to run on the streaming data[cite: 40]:
    * [cite_start]**Model 1 (Linear)**: A baseline model where the price increases in a straight line as occupancy goes up[cite: 43, 44].
    * [cite_start]**Model 2 (Demand-Based)**: A more sophisticated model that calculates a "demand" score from multiple features (occupancy, queue length, traffic, etc.) to set a more nuanced price[cite: 49, 50].
    * [cite_start]**Model 3 (Competitive)**: The most advanced model, which, in addition to demand factors, also considers the prices of nearby competing parking lots to make strategic price adjustments[cite: 66, 68].

5.  ***Price Output***
    [cite_start]For every new piece of data that comes through the stream, the pricing models instantly **recalculate the price** for each parking lot[cite: 76]. These newly computed prices are then broadcasted as a continuous output stream, ready to be used by other systems, such as a live dashboard or a user-facing application.

6.  ***Bokeh Visualizations***
    [cite_start]A live dashboard built with Bokeh visualizes the price outputs in real-time[cite: 84]. It uses a feature called `ColumnDataSource.stream()` to efficiently update the graphs without redrawing them entirely. [cite_start]This allows you to watch **line plots of the prices** as they evolve and change in response to the incoming data, providing a clear and immediate justification for the models' behavior[cite: 85, 87].


  




