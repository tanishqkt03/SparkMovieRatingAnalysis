
# Movie Ratings Analytics Dashboard

## PySpark + Streamlit + Pandas + Seaborn

This project analyzes movie ratings data (`movies.csv` and `ratings.csv`) using Spark for distributed processing and Streamlit for an interactive dashboard. It also includes instructions for setting up an Apache Spark Master–Worker cluster across Windows 11 machines.

----------

## FEATURES

-   Distributed computation using Spark
    
-   Data cleaning and merging
    
-   Ratings distribution visualization
    
-   Genre popularity analysis
    
-   Top/lowest-rated movies
    
-   User activity analysis
    
-   Correlation heatmap
    
-   Streamlit-powered interactive dashboard
    

----------

## DATA FILES

Place these files in the project directory:

-   `movies.csv`
    
-   `ratings.csv`
    

----------

## REQUIREMENTS

### Python Libraries

Install required packages:

```
pip install streamlit pandas numpy seaborn matplotlib pyspark

```

### Apache Spark

Download and extract Spark to:

```
C:\spark\
```

Download and extract Hadoop (winutils) to:

```
C:\hadoop\bin
```

Set environment variables:

```
SPARK_HOME = C:\spark
HADOOP_HOME = C:\spark\hadoop
PATH += C:\spark\bin; C:\spark\sbin
```



----------

# SETTING UP SPARK CLUSTER (WINDOWS 11)

You can run Spark on multiple laptops:

-   Laptop 1 → Master
    
-   Laptop 2/3 → Worker nodes
    

### Step 1: Verify Java 

```
java -version

```
<img width="1103" height="169" alt="image" src="https://github.com/user-attachments/assets/87da6825-036e-4c9f-9b2f-d53b7331adff" />


### Step 2: Start Spark Master (Laptop 1)

Run:

```
spark-shell 
```

If spark is properly installed, you'll see something like this

![01_spark-shell](https://github.com/user-attachments/assets/d3d7c324-0dd4-4053-8ed0-ebe5faa91d33)


Run:

```
spark-class org.apache.spark.deploy.master.Master
```

Terminal will show the confirmation like this:-

![02-Spark-Master-Deploy](https://github.com/user-attachments/assets/4d2a760f-12a5-4c9d-afaa-fdf643e7813f)


Important : 
Note down the Master URL (something like spark://192.168.43.59:7077)

### Step 3: Start Spark Worker (Laptop 2 / Laptop 3)

Run:

```
spark-class org.apache.spark.deploy.worker.Worker spark://192.168.43.59:7077

```
Terminal will look like this:
![03-Spark-Worker-Deploy](https://github.com/user-attachments/assets/15ed485b-6d42-41b6-94de-6fc5a080bcab)


### Step 4: Verify Spark UI

Open:

```
http://localhost:8080

```

![SparkUI-running_job](https://github.com/user-attachments/assets/59c53a1a-6d92-4169-8a11-00d039ebaff2)

You should see:

-   Master node
    
-   Connected workers
    
-   CPU & memory resources
    

----------

# SIMPLE PYSPARK TEST (OPTIONAL)

Create a file `test.py`:

```
from pyspark import SparkContext
sc = SparkContext("spark://192.168.43.59:7077", "TestApp")
data = sc.parallelize([1,2,3,4,5])
print(data.map(lambda x: x*x).collect())
sc.stop()

```

Run:

```
python test.py

```

----------

# RUNNING THE STREAMLIT DASHBOARD

Start your application using:

```
streamlit run code.py

```

The dashboard opens at:

```
http://localhost:8501

```
<img width="1915" height="868" alt="image" src="https://github.com/user-attachments/assets/8852b7cd-2678-4180-891c-a93b2fc51d7f" />

----------

# IMPORTANT: UPDATE MASTER URL IN CODE

```
MASTER_URL = "spark://192.168.43.59:7077"
sc = SparkContext(MASTER_URL, "SimpleTestApp")

```

----------

# PROJECT STRUCTURE

```
Movie-Ratings-Analytics/
│
├── movies.csv
├── ratings.csv
├── code.py
├── README.md
└── screenshots/

```

----------

# SCREENSHOTS

Screenshots are attached in the screenshots folder with proper naming

----------

