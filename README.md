

## Introduction

This README provides an overview of a Scala programming assignment consisting of two tasks. The first task involves bucketizing an array of double values into specified ranges, while the second task requires analyzing player statistics from a dataset. Each task's solution and approach are outlined along with sample outputs.

## Task 1: Bucketise the given array[Double]

### Explanation

The task involves dividing an array of double values into buckets based on specified range intervals. Each bucket has a range interval of 0.05 between them.

### Approach

- **Bucketization Logic**: 
  - Iterate through the array of double values.
  - For each value, calculate its corresponding bucket range.
  - The lower and upper bounds of each bucket range are calculated based on the given range interval.
  - Format the result to display the lower and upper bounds of each bucket range.

### Sample Output

For the input array `[12.05, 12.03, 10.33, 11.45, 13.50]`, the output would be `[12.050-12.099, 12.050-12.099, 10.300-10.349, 11.450-11.499, 13.500-13.549]`.

## Task 2: Player Statistics

### Explanation

This task involves analyzing player statistics including runs scored and wickets taken from a dataset. Various analyses such as finding the player with the highest run score, top 5 players by runs scored, top 5 players by wickets taken, and ranking players based on overall performance are performed.

### Approach

- **Data Representation**: 
  - Player statistics are represented using a case class in Scala.
- **Analysis Logic**:
  - Finding the player with the highest run score:
    - Utilize the `maxBy` function to find the player with the maximum runs scored.
  - Top 5 players by run scored:
    - Sort the players by runs scored in descending order and take the top 5.
  - Top 5 players by wicket taken:
    - Sort the players by wickets taken in descending order and take the top 5.
  - Ranking players with overall performance:
    - Calculate an overall performance score for each player based on runs scored and wickets taken. (by given hint in question)
    - Sort the players by this performance score in descending order to determine the ranking.

### Sample Output

- Player with the highest run scored: Sam
- Top 5 players by run scored:
  - Sam: 2300
  - Ram: 300
  - Mano: 300
- Top 5 players by wicket taken:
  - Ram: 30
  - Mano: 13
  - Sam: 3
- Rank players with overall performance:
  - Rank 1: Ram (India) - Performance Score: 154.0
  - Rank 2: Mano (India) - Performance Score: 82.5
  - Rank 3: Sam (India) - Performance Score: 115.15


