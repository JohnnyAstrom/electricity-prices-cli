# About the Project  
This is a **CLI-based electricity price analysis tool** built in **Java**.  
The program fetches electricity price data from the [Elpris API](https://www.elprisetjustnu.se/elpris-api) and can also analyze historical consumption from CSV files.  
It supports both **interactive mode** (menu-driven) and **argument mode** for direct execution.  

---

## Key Features  

- **Interactive CLI**  
  - Starts a guided menu if no arguments are provided  
  - Lets the user select a zone (SE1–SE4)  
  - Option to analyze a CSV file with consumption data  

- **Zone analysis**  
  - Fetches electricity prices for today (and tomorrow if available)  
  - Prints the daily average price  
  - Identifies and displays the cheapest and most expensive hours  
  - Uses a sliding window algorithm to recommend the **best charging intervals** for 2h, 4h, and 8h  

- **CSV analysis**  
  - Reads hourly electricity consumption from a semicolon-separated CSV file  
  - Fetches matching historical electricity prices from the API  
  - Calculates the **total electricity cost** for the given period  
  - Shows statistics (average price, cheapest and most expensive hour) based on the consumption data  

- **Zones supported**  
  - SE1 = Luleå / Northern Sweden  
  - SE2 = Sundsvall / Northern Central Sweden  
  - SE3 = Stockholm / Southern Central Sweden  
  - SE4 = Malmö / Southern Sweden  

- **Testing**  
  - Unit tests with **JUnit 5** for price analysis and CSV parsing  

---

## Technologies Used  
- **Language:** Java (JDK 24)  
- **Testing:** JUnit 5  
- **Project Management:** Git & GitHub  
- **Build Tool:** Maven  
- **API:** Elpris API (https://www.elprisetjustnu.se/elpris-api)  

---

## Project Structure
```text
src/main/java/org/example/
├─ App.java                  # Entry point (interactive & argument modes)
├─ PriceFetcher.java         # Fetches price data from API
├─ PriceUtils.java           # Analysis utilities (average, cheapest, best window)
├─ CsvConsumptionReader.java # Reads CSV consumption data
├─ PricePoint.java           # Represents a single price point
└─ ConsumptionPoint.java     # Represents a single consumption data point
```

---

## First time you open the project

### 1: Clone project
- git clone https://github.com/JohnnyAstrom/electricity-prices-cli.git
- cd electricity-prices-cli

### 2: Open in your IDE (IntelliJ / Eclipse)
- Make sure JDK 17+ (or newer) is installed.

### 3: Run the program
- Run the App class in org.example

### 4: Use in different modes  

#### Interactive mode (no args)  
- Starts the program in a **guided menu** where you select zone and (optionally) CSV analysis.  

#### Zone mode  
- Run with a **zone argument** (example: `SE1`) to analyze electricity prices for today (and tomorrow if available).  

#### CSV mode  
- Run with **zone + CSV file** as arguments (example: `SE1 consumption-home-august.csv`) to calculate total cost from consumption data.

### Optional: Run tests
- mvn test
- or run tests directly in your IDE

---

## Notes

- Prices are fetched per day (today + tomorrow if available).
- CSV files must be semicolon-separated and placed in `src/main/resources/`.
- Output values are formatted with decimals (kr/kWh).
- Interactive mode ensures smooth use even without arguments.
