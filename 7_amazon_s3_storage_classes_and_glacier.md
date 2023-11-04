# Amazon S3 Storage Classes Cheat Sheet

#### **General Classes**
- **S3 Standard - General Purpose**: High availability (99.99%), designed for frequently accessed data, low latency, high throughput. Use cases include big data analytics, mobile and gaming applications, content distribution.

#### **Infrequent Access**
- **S3 Infrequent Access (S3 Standard-IA)**: Cost-effective for less frequently accessed data, but requires rapid access when needed. Availability is 99.9%. Suitable for disaster recovery and backups.
- **S3 One Zone-IA**: Stores data in a single Availability Zone (AZ). If the AZ is destroyed, data may be lost. Availability is 99.5%. Used for storing secondary backups or data that can be recreated.

#### **Glacier Storage for Archiving**
- **Glacier Instant Retrieval**: Quick access to archived data (milliseconds retrieval), minimum storage duration is 90 days. Ideal for data accessed infrequently (e.g., once a quarter).
- **Glacier Flexible Retrieval**: Offers Expedited (1-5 minutes), Standard (3-5 hours), or Bulk (5-12 hours) retrieval options, with a 90-day minimum storage duration.
- **Glacier Deep Archive**: Lowest cost, for long-term storage with Standard (12 hours) or Bulk (48 hours) retrieval times. Minimum storage duration is 180 days.

#### **Intelligent Tiering**
- **S3 Intelligent-Tiering**: Moves objects between tiers based on usage patterns. Includes frequent access, infrequent access, archive instant access, and deep archive access tiers. No retrieval charges, but has a small monthly monitoring and auto-tiering fee.

#### **Durability and Availability**
- **Durability**: 11 9's (99.999999999%) - Highly unlikely to lose data (1 in 10 million objects every 10,000 years).
- **Availability**: Varies by class, affects how readily available the service is. S3 Standard has the highest availability.

#### **Use Cases by Class**
- **Frequent Access**: S3 Standard - Big data, content delivery, high usage applications.
- **Infrequent Access**: S3 Standard-IA - Disaster recovery.
- **Cost-Effective Infrequent Access**: S3 One Zone-IA - Secondary backups, replaceable data.
- **Archiving**: Glacier - Data archiving with varying retrieval needs.
- **Automated Tiering**: S3 Intelligent-Tiering - Dynamic data with unknown access patterns.

#### **Pricing Notes**
- Pricing is based on storage amount, retrieval cost, and minimum storage duration.
- Review pricing charts in the AWS Pricing page for detailed cost estimates.

## Practice exam questions

1. **Question**: What is the durability level of objects stored in Amazon S3?
   - A. 99.99%
   - B. 99.999999999% (11 9's)
   - C. 99.9%
   - D. 99.5%

2. **Question**: Which S3 storage class would be most suitable for frequently accessed data with low latency and high throughput requirements?
   - A. Amazon S3 Standard - General Purpose
   - B. Amazon S3 - Infrequent Access
   - C. Glacier Flexible Retrieval
   - D. Amazon S3 One Zone - Infrequent Access

3. **Question**: Amazon S3 One Zone - Infrequent Access differs from S3 - Infrequent Access in that:
   - A. It is less expensive and provides faster data retrieval.
   - B. It is stored redundantly across multiple availability zones (AZs).
   - C. It is stored in a single AZ and may be lost if the AZ is destroyed.
   - D. It has a higher availability rate than S3 - Infrequent Access.

4. **Question**: Which S3 storage class offers a retrieval time in milliseconds and is designed for data that might be accessed once a quarter with a minimum storage duration of 90 days?
   - A. Glacier Deep Archive
   - B. Glacier Instant Retrieval
   - C. Glacier Flexible Retrieval
   - D. Amazon S3 - Intelligent Tiering

5. **Question**: Amazon S3 Lifecycle configurations can be used to:
   - A. Move objects to a different AWS account.
   - B. Move objects automatically between different S3 storage classes.
   - C. Back up objects to an on-premises server.
   - D. Configure objects to expire after a certain date.

---

### Answers and Explanations:

1. **Answer**: B. 99.999999999% (11 9's)
   - **Explanation**: Amazon S3 provides a durability level of 99.999999999%, often referred to as "11 9's". This implies that you can expect to lose a single object once every 10,000 years if you store 10 million objects with Amazon S3, making it highly reliable.

2. **Answer**: A. Amazon S3 Standard - General Purpose
   - **Explanation**: The S3 Standard storage class is designed for frequently accessed data, offering low latency and high throughput. It's also capable of sustaining two concurrent facility failures, making it suitable for a wide range of use cases including big data analytics, mobile and gaming applications, and content distribution.

3. **Answer**: C. It is stored in a single AZ and may be lost if the AZ is destroyed.
   - **Explanation**: The Amazon S3 One Zone - Infrequent Access class stores data in a single AZ, and unlike S3 - Infrequent Access, which stores data redundantly across multiple AZs, the data in One Zone - IA can be lost if the AZ is destroyed. This is why it costs less and has lower availability.

4. **Answer**: B. Glacier Instant Retrieval
   - **Explanation**: Amazon S3 Glacier Instant Retrieval is designed for data that is not accessed frequently but requires millisecond access times when retrieved, such as data accessed once a quarter. It has a minimum storage duration requirement of 90 days.

5. **Answer**: B. Move objects automatically between different S3 storage classes.
   - **Explanation**: Amazon S3 Lifecycle configurations are used to manage objects efficiently and cost-effectively by automating the process of moving objects between different S3 storage classes as they age or according to certain patterns of access.
