# Self Study Preparation Guide

**⏳ Estimated Prep Time:** 30–45 minutes

Welcome to our flipped-classroom session, where you'll review foundational concepts beforehand to maximize our time for hands-on coding and debugging. This pre-study focuses on **Apache Spark and PySpark**, the industry standards for processing large-scale datasets. By familiarizing yourself with the architecture and syntax now, you will be ready to build performant ETL pipelines and transformation logic during our live workshop.

## **⚡ Your Self-Study Tasks**

Please complete the following activities before our session.

### **📝 Task 1: The "Why" of Distributed Processing (15 Minutes)**

**Activity:** Read the introductory markdown cells in the **"Hands-on with Spark"** notebook (up to the "Installing and Initializing Spark" section) and the **"Part 1"** section of the `lesson.md` file. Focus on the architectural differences between local Python scripts and distributed Spark jobs.

**Guiding Questions:**

* How does PySpark differ from standard Python libraries like Pandas when handling datasets larger than your computer's RAM?  
* The notebook mentions **"Lazy Evaluation."** Why does Spark create an "action plan" rather than executing code immediately? How does this improve efficiency?  
* What is the relationship between the Python code you write and the Java Virtual Machine (JVM) where it executes?

### **📝 Task 2: Interpreting Spark DataFrame Syntax (20 Minutes)**

**Activity:** Scroll through the **"Spark SQL and DataFrames"** and **"DataFrame Operations on Columns/Rows"** sections of the notebook. **You do not need to run the code yet.** Instead, trace the syntax used to manipulate the movies, ratings, and taxi datasets.

**Focus your attention on these key patterns:**

1. **Reading Data:** How spark.read.csv or spark.read.parquet handles different file formats.  
2. **Transformation:** How methods like `.select()`, `.filter()`, and `.withColumn()` are chained together.  
3. **Action:** Notice that data only appears when `.show()` is called.

**Guiding Questions:**

* In the notebook, schemas (data types) are sometimes inferred and sometimes defined manually. What is the benefit of defining a schema manually for large datasets like the taxi data?  
* Look at the filtering examples (e.g., `movies.filter(movies.status \== 'In Production'`)). How does this syntax compare to `SQL WHERE` clauses or Excel filtering?

### **📝 Task 3 (Optional): Bridging SQL and Python**

**Activity:** Skim the **"Spark SQL"** section near the end of the notebook.

**Guiding Questions:**

* How does createOrReplaceTempView("taxi") allow you to switch from Python code to writing raw SQL queries (e.g., `SELECT count(\*) from taxi`)?  
* In a professional team with mixed skills (Data Engineers and Data Analysts), why might this feature be valuable?

## **🙌🏻 Active Engagement Strategies**

To deepen your retention, try one of the following while you review:

* **Analogy Creation:** Try to create a real-world analogy for **Lazy Evaluation**. (e.g., "It's like a chef writing down a recipe but not chopping a single onion until a customer actually orders the dish.")  
* **"Code Commentary":** Select a complex transformation block in the notebook (such as the taxi trip duration calculation) and write a one-sentence comment explaining the business logic being applied.  
* **Pandas vs. Spark:** If you know Pandas, mentally note the differences. For example, `df.head()` in Pandas vs `df.show()` or `df.limit().show()` in Spark.

## **📖 Additional Reading Material**

* [Apache Spark Overview (Official Docs)](https://spark.apache.org/docs/latest/index.html)  
* [PySpark Documentation](https://spark.apache.org/docs/latest/api/python/index.html)

### **🙋🏻‍♂️ See you in the session\!**