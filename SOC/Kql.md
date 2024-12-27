# KQL (Kusto Query Language) Resources

Welcome to the KQL resources page! This document provides a comprehensive guide to learning and mastering KQL, a query language designed for Azure Data Explorer, Azure Monitor, and other Microsoft services. With KQL, you can extract insights and perform data analysis efficiently.

## 📚 Learning Resources

### 1. **[Official Microsoft Documentation](https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference)**
   - **Description:** Comprehensive reference guide and tutorials from Microsoft.
   - **Topics Covered:** Basics, functions, operators, and advanced concepts.

### 2. **[KQL Tutorials on Microsoft Learn](https://learn.microsoft.com/en-us/training/paths/intro-to-kusto-query-language/)**
   - **Description:** Free step-by-step learning paths.
   - **Skill Level:** Beginner to Advanced.

### 3. **[Pluralsight Course: KQL for Beginners](https://www.pluralsight.com/)**
   - **Description:** Video-based training for learning KQL fundamentals.
   - **Features:** Interactive exercises.
   - **Skill Level:** Beginner.

### 4. **[Udemy - Mastering KQL](https://www.udemy.com/)**
   - **Description:** In-depth course covering real-world use cases.
   - **Features:** Lifetime access and quizzes.
   - **Skill Level:** Intermediate.

## 🛠️ Tools and Platforms for Practicing

### 1. **[Azure Data Explorer](https://dataexplorer.azure.com/)**
   - **Description:** A platform to run and test KQL queries.
   - **Features:** Interactive data exploration.

### 2. **[Log Analytics](https://azure.microsoft.com/en-us/products/monitor/log-analytics/)**
   - **Description:** Analyze log data using KQL.
   - **Features:** Built into Azure Monitor.

### 3. **[KQL Playground](https://aka.ms/kqlinteractive)**
   - **Description:** Free sandbox environment for practicing KQL.
   - **Features:** Preloaded datasets for experimentation.

### 4. KC7 Cyber Detective Game
   - **Description**: An interactive cybersecurity detective game for learning and problem-solving.
   - **Features**: Players solve puzzles, analyze data, and practice various cybersecurity skills.

### 5. Kusto Detective Agency
   - **Description**: A platform for running queries with KQL (Kusto Query Language) to analyze and investigate data.
   - **Features**: Query-based data investigation, real-time data exploration, and insights for cybersecurity tasks.

## 💻 Example Queries

### Basic Query
```kql
StormEvents
| where StartTime > datetime(2023-01-01)
| summarize Count = count() by State
```

### Aggregation and Visualization
```kql
StormEvents
| summarize TotalDamage = sum(DamageProperty) by EventType
| render piechart
```

### Joins
```kql
TableA
| join kind=inner (TableB) on Key
```

## 🔗 Useful Links
- **[KQL Reference](https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference)**
- **[Azure Monitor Overview](https://learn.microsoft.com/en-us/azure/azure-monitor/)**
- **[GitHub - KQL Cheat Sheet](https://github.com/yourrepo/kql-cheat-sheet)**

## 💡 Contributing
Found an awesome KQL resource? Submit a pull request or open an issue to share it with the community.

---

Happy querying with KQL! 🚀
