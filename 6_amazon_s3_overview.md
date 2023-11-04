# **Amazon S3 Cheat Sheet for AWS Machine Learning - Specialty**

- **S3 Basics:**
  - **Service Overview:** Object storage service that offers industry-leading scalability, data availability, security, and performance.
  - **Data Storage:** Store and retrieve any amount of data at any time.
  - **Buckets:** Containers for storing objects. Must have globally unique names.
  - **Objects:** Files stored in buckets, identified by a key (file name and path).
  - **Object Key:** Full path to the file (e.g., `my_bucket/my_folder1/another_folder/my_file.txt`).

- **Important Characteristics:**
  - **Maximum Object Size:** 5 terabytes.
  - **Object Tags:** Key-value pairs for classification, security, and lifecycle management.
  - **Durability:** 99.999999999% (11 9's), ensuring high durability of objects.

- **Machine Learning & Data Engineering:**
  - **Data Lake Foundation:** S3 is often used to create a Data Lake due to its scalability and support for various data formats.
  - **Supported Data Formats:** CSV, JSON, Parquet, ORC, Avro, Protobuf, etc.
  - **Service Integration:** Works with AWS compute services like EC2, Athena, Redshift Spectrum, Rekognition, Glue, etc.

- **Data Partitioning:**
  - **Purpose:** Speeds up range queries by organizing data into logical divisions.
  - **Common Partitioning Strategies:** By date (year/month/day/hour) or by product ID.
  - **Example Path with Partitions:** `s3://my_bucket/my_dataset/year=2022/month=10/day=21/data.csv`.
  - **Partitioning and Athena:** Helps optimize queries in Amazon Athena for data stored in S3.

- **Hands-On Basics:**
  - **Bucket Creation:** Choose a unique name and a region. Default settings are often sufficient.
  - **Uploading Data:**
    - Create a folder structure representing the partition scheme.
    - Upload files into the corresponding partition folder.

- **Tips:**
  - **Global Uniqueness:** Bucket names must be unique across all existing bucket names in S3.
  - **No Pre-provisioning Required:** S3 scales automatically with the amount of data stored.
  - **Decoupling Storage and Compute:** S3 (storage) is separated from services like EC2 (compute), allowing for flexibility in architecture design.

**Example Bucket and Object Structure:**

```
aws-machine-learning-stephane-v4 (Bucket)
└── instructors (Folder)
    └── 2022 (Year Partition)
        └── 10 (Month Partition)
            └── 21 (Day Partition)
                └── instructor_data.csv (Object)
```

**Note:**

- Use the partitioning scheme that best fits your query patterns to minimize costs and improve performance.
- S3 is the backbone for many AWS ML services such as Amazon SageMaker.
- Data lakes on S3 can handle any scale of data across diverse formats and are central to many ML workflows.

## Based on the transcript provided, here are some practice exam questions

1. **Question:**
   What is the maximum object size that can be stored in a single S3 object?
   
2. **Question:**
   Which AWS service allows you to perform serverless queries on data stored in S3 and can benefit from data partitioning?

3. **Question:**
   In the context of S3 and AWS Machine Learning, what is the purpose of object tags?

4. **Question:**
   When creating an S3 bucket for storing machine learning datasets, why might you choose to create a partitioning scheme based on year, month, day, and hour?

5. **Question:**
   As mentioned in the transcript, if you frequently need to query your data by product ID, how should you structure your S3 data partitions?

6. **Question:**
   The instructor created an S3 bucket in a specific AWS region. Why is it important to choose a region that is close to you or your customers?

7. **Question:**
   Describe the benefits of using Amazon S3 for creating a data lake as part of an AWS machine learning infrastructure.

8. **Question:**
   What does the instructor mean when they say that S3 has "infinite sizing" and does not require provisioning?

9. **Question:**
   Which AWS services are considered as the compute side that works with Amazon S3 in the provided centralized architecture for machine learning?

10. **Question:**
    Based on the example in the transcript, what would be the full S3 key path for the file `data.csv` on October 21, 2022?

---

**Answers and Explanations:**

1. **Answer:** The maximum object size for a single S3 object is 5 terabytes.
   
   **Explanation:** The instructor emphasizes the importance of knowing that the largest object that can be stored in S3 is 5 terabytes for the exam. This is significant for machine learning applications because large datasets may need to be split across multiple objects.

2. **Answer:** Amazon Athena.
   
   **Explanation:** Amazon Athena is mentioned as a serverless service that benefits from data partitioning because it allows for faster range queries, which is important when dealing with large datasets in machine learning.

3. **Answer:** Object tags are used for classifying data, and for managing security and lifecycle policies.
   
   **Explanation:** In the AWS machine learning context, object tags can be key-value pairs attached to S3 objects. They help in managing and classifying data, which is crucial for organizing machine learning datasets, as well as for applying security and lifecycle policies.

4. **Answer:** Partitioning based on year, month, day, and hour can speed up range queries on datasets, especially when querying frequently by date.
   
   **Explanation:** Data partitioning in this manner can be a performance optimization strategy. It allows for faster access to data subsets, reducing the amount of data scanned during queries, thus reducing latency and cost.

5. **Answer:** The data partitions should have the product ID as the first level of partitioning.
   
   **Explanation:** Structuring partitions by product ID before other categories allows for efficient retrieval of all data related to a specific product, which is especially useful if queries on the dataset often filter by product ID.

6. **Answer:** Choosing a region close to you or your customers can reduce latency and may also reduce transfer costs.
   
   **Explanation:** AWS regions have different latency and cost implications. Selecting a region near the user or the users' customers can result in faster access to data and potentially lower costs.

7. **Answer:** Amazon S3 is highly durable, infinitely scalable, supports any file format, and is decoupled from compute resources, making it ideal for a centralized data lake.
   
   **Explanation:** The instructor describes S3's high durability, scalability, and support for all file types without provisioning, which makes it suitable for a data lake. These features allow S3 to integrate seamlessly with various AWS compute services for machine learning purposes.

8. **Answer:** S3 has "infinite sizing" because it is designed to provide scalable storage without the need for manual provisioning of storage space.
   
   **Explanation:** "Infinite sizing" refers to the ability to store an unlimited amount of data without pre-provisioning storage capacity, which is beneficial for machine learning projects that can grow unpredictably.

9. **Answer:** Compute services like EC2, Athena, Redshift, Spectrum, Rekognition, and Glue.
   
   **Explanation:** These services are mentioned as part of the compute side of AWS's architecture, which operate separately from S3 storage but integrate with it to process and analyze the stored data.

10. **Answer:** The full S3 key path for the file `data.csv` would be `instructors/2022/10/21/data.csv`.
   
   **Explanation:** Following the instructor's steps for creating folders for year, month, and day as a partition

ing scheme, the path to `data.csv` includes the folder names in sequence, reflecting the partition hierarchy.

By studying these questions and explanations, you can deepen your understanding of S3 and how it relates to AWS machine learning services and practices.
