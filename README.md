# AWS-Cost-Optimization
-------
## AWS S3 Cost Optimization 
### Understanding Amazon S3 Pricing and Storage Classes

Amazon S3 (Simple Storage Service) provides a variety of storage classes designed to cater to different use cases and access patterns. Familiarizing yourself with these classes and their corresponding costs is essential for effective cost optimization.

### S3 Storage Classes Overview

1. **Amazon S3 Standard**
   - **Use Case**: Frequently accessed data.
   - **Pricing**: $0.023 per GB/month for the first 50 TB.

2. **Amazon S3 Intelligent-Tiering**
   - **Use Case**: Unpredictable access patterns.
   - **Pricing**: $0.0025 per 1,000 objects above 128 KB, plus tier-specific storage costs.

3. **Amazon S3 Infrequent Access (IA)**
   - **Use Case**: Infrequently accessed data.
   - **Pricing**: $0.0125 per GB/month.

4. **Amazon S3 One Zone – Infrequent Access**
   - **Use Case**: Infrequently accessed data stored in a single AZ.
   - **Pricing**: $0.01 per GB/month.

5. **Amazon S3 Glacier Instant Retrieval**
   - **Use Case**: Long-term archival with quick access.
   - **Pricing**: $0.004 per GB/month.

6. **Amazon S3 Glacier Flexible Retrieval**
   - **Use Case**: Long-term archival with flexible retrieval times.
   - **Pricing**: $0.0036 per GB/month.

7. **Amazon S3 Glacier Deep Archive**
   - **Use Case**: Rarely accessed archival data.
   - **Pricing**: $0.00099 per GB/month.

### Lifecycle Policies for Cost Optimization

Lifecycle policies allow you to automate the transition of objects between different storage classes based on predefined rules. This can significantly reduce costs by ensuring that data is stored in the most cost-effective class based on its access frequency.

### Running AWS S3 Storage Class Analysis

To identify which objects can be moved to less expensive storage classes:

1. **Navigate to S3 Console**:
   - Choose a bucket.
   - Go to the Metrics tab.
   - Click on Create analytics configuration under Storage Class Analysis.

2. **Configure Analysis**:
   - Name your configuration.
   - Choose whether to analyze the whole bucket or a subset.
   - Optionally export results to CSV.

3. **Analyze Results**:
   - Review the storage versus retrieval patterns.
   - Identify infrequently accessed files that can be moved to cheaper storage classes.

### Creating an S3 Lifecycle Rule

1. **Navigate to the S3 Console**:
   - Choose a bucket.
   - Go to the Management tab.
   - Select Create lifecycle rule.

2. **Define Rule Criteria**:
   - Set transitions based on object age (e.g., move to IA after 45 days, Glacier after 365 days).
   - Set expiration rules for automatic deletion.

### Additional Cost Optimization Tips

1. **Use Cost and Usage Reports (CUR)**:
   - CUR provides detailed insights into your AWS costs.
   - Regularly review CUR to identify potential savings.

2. **Effective S3 Bucket Organization**:
   - Use file prefixes and tags to categorize data.
   - Implement consistent tagging strategies (e.g., by expiration date, team name, or customer).

3. **Monitor Costs with CloudForecast**:
   - Sign up for daily AWS spending alerts.
   - Use CloudForecast's ZeroWaste Health Check to identify buckets without lifecycle policies.

### Summary Tables

**S3 Storage Classes and Pricing**:

| Storage Class                     | Use Cases & Considerations                                                                 | Pricing (US East, N. Virginia)                     |
|-----------------------------------|-------------------------------------------------------------------------------------------|---------------------------------------------------|
| Amazon S3 Standard Storage        | Frequently accessed data, application data, website content                                | $0.023 per GB/month (first 50 TB)                 |
| Amazon S3 Intelligent-Tiering     | Unpredictable access patterns, backup data, disaster recovery                             | $0.0025 per 1,000 objects above 128 KB            |
| Amazon S3 Infrequent Access       | Infrequently accessed data, historical log data, backups                                  | $0.0125 per GB/month                              |
| Amazon S3 One Zone – IA           | Infrequently accessed data stored in one AZ                                               | $0.01 per GB/month                                |
| Amazon S3 Glacier Instant Retrieval | Long-term archival with quick access, business intelligence data, media processing         | $0.004 per GB/month                               |
| Amazon S3 Glacier Flexible Retrieval | Long-term archival without the need for rapid access, record retention                    | $0.0036 per GB/month                              |
| Amazon S3 Glacier Deep Archive    | Rarely accessed archival data, regulatory compliance                                      | $0.00099 per GB/month                             |

**S3 Request & Data Retrieval Pricing**:

| Category                               | Pricing                                       |
|----------------------------------------|-----------------------------------------------|
| PUT, COPY, POST, or LIST requests      | $0.005 per 1,000 requests                     |
| GET, SELECT, and other requests        | $0.0004 per 1,000 requests                    |
| Lifecycle Transition requests          | $0.01 to $0.05 per 1,000 requests             |
| Data Retrieval requests                | $0.05 to $10.00 per 1,000 requests            |

**S3 Data Transfer Pricing**:

| Category                  | Pricing                                              |
|---------------------------|------------------------------------------------------|
| DTI from Internet         | $0.00 per GB                                         |
| DTO to Internet           | $0.09 per GB (first 10 TB/month)                     |
| DTO from S3 to CloudFront | $0.00 per GB                                         |
| DTO to other AWS regions  | $0.01 to $0.02 per GB (depending on destination)     |

By understanding and utilizing these S3 storage classes and associated lifecycle policies, you can optimize your AWS S3 costs effectively.
