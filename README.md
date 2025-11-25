# Restroom-Redoubt-Assignment

Restroom Redoubt - Day 14 Solution
A C# solution for the "Restroom Redoubt" puzzle from Advent of Code, simulating robot movement with wrap-around behavior and calculating safety factors based on quadrant distributions.

🎯 Problem Description
The Historians need to access a bathroom protected by security robots moving in predictable straight lines. Each robot has:

Position (p=x,y): Coordinates relative to top-left corner

Velocity (v=x,y): Movement per second (positive x = right, positive y = down)

Key Features:
Grid Wrapping: Robots teleport to opposite side when hitting edges

Quadrant Analysis: Count robots in four quadrants after 100 seconds

Safety Factor: Multiply quadrant counts for final result

Grid Specifications:
Example: 11×7 tiles

Actual: 101×103 tiles

Time: 100 seconds simulation

🚀 Solution
This C# implementation:

Parses robot positions and velocities from input

Simulates movement with proper edge wrapping

Counts robots in each quadrant (excluding middle rows/columns)

Calculates safety factor by multiplying quadrant counts

📁 Project Structure

RestroomRedoubt/
├── Program.cs          # Main application with simulation logic
├── input.txt           # Puzzle input data (robot positions/velocities)
└── README.md           # Project documentation

Input Format:
Each line should follow: p=x,y v=vx,vy

p=0,4 v=3,-3
p=6,3 v=-1,-3
p=10,3 v=-1,2

Robot Movement Logic:

public void Move(Tuple<int, int> dimensions, int steps)
{
    var pX = position.Item1 + (velocity.Item1 * steps) % dimensions.Item1;
    var pY = position.Item2 + (velocity.Item2 * steps) % dimensions.Item2;
    
    // Handle wrap-around for negative coordinates and boundaries
    if (pX < 0) pX += dimensions.Item1;
    if (pX >= dimensions.Item1) pX -= dimensions.Item1;
    // ... similar for Y coordinate
}

Quadrant Counting:
Q1 (Top-left): x < 50, y < 51

Q2 (Top-right): x > 50, y < 51

Q3 (Bottom-left): x < 50, y > 51

Q4 (Bottom-right): x > 50, y > 51

*Note: Middle values (x=50, y=51) are excluded*


📊 Example Output
For the sample problem, the solution outputs the safety factor:

[Calculated Safety Factor]



🎯 Algorithm Details
Time Complexity: O(n) where n is number of robots

Space Complexity: O(n) for storing robot positions

Grid Dimensions: 101 (width) × 103 (height)

Simulation Time: 100 seconds


⚡ Performance
Direct mathematical calculation avoids expensive iterative simulation

Efficient modulo operations for coordinate wrapping

Minimal memory footprint with tuple-based position storage

🧪 Testing
The solution handles:

Negative velocities and positions

Large coordinate values

Edge case wrapping scenarios

Various input sizes

📝 Notes
Robots can occupy same tiles (no collision detection)

Solution assumes proper input formatting

Middle exclusion uses integer division (50, 51 for 101×103 grid)
