## Question 1

What can you tell me about Mostly AI, a company that offers solutions related to the creation of synthetic data?

## Response

Mostly AI is a pioneering company in the field of synthetic data generation, founded in 2017 in Vienna, Austria. The company specializes in creating highly accurate and privacy-compliant synthetic data for various business sectors, with a focus on AI model development and data privacy[1][2].

## Key Features and Offerings

**Synthetic Data Platform**: Mostly AI's core product is its Synthetic Data Platform, which allows organizations to generate synthetic versions of their proprietary data[3]. This platform can:

- Create synthetic tabular and text data
- Maintain statistical characteristics and referential integrity of original datasets
- Ensure privacy compliance (e.g., GDPR, CCPA)
- Provide accuracy and privacy reports for generated datasets

**Use Cases**:

- AI/ML model training and development
- Data sharing and democratization
- Software testing and quality assurance
- Self-service analytics

## Technology and Approach

Mostly AI leverages advanced AI and machine learning techniques to generate synthetic data:

- Uses GPU-powered technology for scalable data simulation[7]
- Employs pretrained language models for synthetic text generation[1]
- Focuses on preserving statistical patterns and relationships in the original data[3]

## Company Growth and Recognition

- Raised a total of $31.14 million in funding, with the latest being a Series B round[7][9]
- Works with Fortune 100 insurers and banks in Europe and North America[8]
- Recognized as a leader in the synthetic training data market by CB Insights[9]

## Business Impact and Advantages

1. **Privacy Protection**: Synthetic data is immune to re-identification attacks, helping companies comply with data protection regulations[3].

2. **Data Augmentation**: Allows companies to amplify datasets, improving model performance and exploring "what-if" scenarios[3].

3. **AI Explainability**: Enhances the explainability of AI models by providing synthetic data that accurately represents original data characteristics[3].

4. **Cross-Border Data Sharing**: Enables safe sharing of synthetic data across borders, overcoming legal and privacy barriers[3].

5. **Performance Improvement**: Claims to deliver up to 35% performance improvement in downstream text classification tasks compared to other methods[8].

Mostly AI's innovative approach to synthetic data generation positions it as a significant player in addressing AI training challenges and data privacy concerns, particularly as companies seek to leverage proprietary data for AI development while maintaining compliance with stringent data protection regulations.

Citations:
[1] https://mostly.ai
[2] https://www.zdnet.com/article/can-synthetic-data-solve-ais-privacy-concerns-this-company-is-betting-on-it/
[3] https://aws.amazon.com/marketplace/pp/prodview-z4bb3qozmlg3c
[4] https://www.upmarket.co/private-markets/trending/mostly-ai/
[5] https://twimlai.com/solutions/s/mostly-ai-synthetic-data-platform/
[6] https://marketplace.databricks.com/details/0fc15edc-d3c9-488d-980e-b438fcc3c162/MOSTLY-AI_Synthetic-Data-Generator-by-MOSTLY-AI-for-Databricks
[7] https://app.dealroom.co/companies/mostly_ai
[8] https://www.prnewswire.com/news-releases/mostly-ai-launches-synthetic-text-to-overcome-ai-training-plateau-and-unlock-high-value-proprietary-data-302263251.html
[9] https://www.cbinsights.com/company/mostly-ai
[10] https://mostly.ai/handbook/mostly-ai-employee-handbook/why-mostly-ai

## Question 2

Do you have any information on the pricing plans provided by this company?

## Response

Mostly AI offers several pricing plans to cater to different user needs:

## Free Plan

- Allows users to generate up to 100,000 rows of synthetic data per day
- Includes core features of the platform
- No time limit; this is a permanent free option, not a trial[1][2]

## Team Plan

- Priced at $3 per credit
- Suitable for teams collaborating on synthetic data generation
- Provides 500 credits per month[7]

## Enterprise Plan

- Priced at $5 per credit
- Offers more advanced features and higher usage limits[2]

The actual cost for paid plans depends on several factors:

- Number of data subjects (rows)
- Data points per subject (columns)
- Number of creators (users)

For example:

- A Team Plan user with 1 creator, 100 data points per subject, and 100,000 data subjects would pay $1,860 per month or $22,320 per year
- An Enterprise Plan user with the same features would pay $3,100 per month or $37,200 per year[2]

It's worth noting that Mostly AI encourages potential customers to contact them directly for more detailed pricing information, especially for enterprise-level needs. The company also offers deployment options via Kubernetes/OpenShift for organizations requiring scalable cluster environments[3].

Citations:
[1] https://mostly.ai/pricing
[2] https://www.eweek.com/artificial-intelligence/best-synthetic-data-software/
[3] https://mostly.ai/features
[4] https://www.trustradius.com/products/mostly-ai/pricing
[5] https://deepgram.com/ai-apps/mostlyai
[6] https://mostly.ai
[7] https://mostlyai.tenereteam.com
[8] https://aws.amazon.com/marketplace/pp/prodview-z4bb3qozmlg3c
[9] https://mostly.ai/what-is-synthetic-data
[10] https://marketplace.databricks.com/details/0fc15edc-d3c9-488d-980e-b438fcc3c162/MOSTLY-AI_Synthetic-Data-Generator-by-MOSTLY-AI-for-Databricks

## Question 3

Is this company able to generate synthetic data based off of tabular data?

## Response

Yes, Mostly AI is specifically designed to generate synthetic data based on tabular data. The company's Synthetic Data Platform is capable of creating highly accurate and privacy-compliant synthetic versions of tabular datasets[1][2].

Key features of Mostly AI's tabular synthetic data generation include:

1. Preservation of statistical characteristics and referential integrity of original datasets[2]
2. Support for single-table, two-table, and multi-table synthetic data generation scenarios[2]
3. Retention of correlations between columns within tables and among multiple tables[2]
4. Automatic recognition of common data types in table columns[2]
5. Ability to use Large Language Models (LLMs) for unstructured text found in table columns[2]

The platform generates synthetic data that maintains the patterns, correlations, distributions, and dependencies of the original tabular data while ensuring that each generated row does not correspond directly to any specific row in the original dataset[4]. This approach allows organizations to create valuable synthetic datasets that can be used for various purposes such as AI/ML model training, software testing, and data sharing, all while protecting the privacy of the individuals represented in the original data[5].

Citations:
[1] https://mostly.ai
[2] https://mostly.ai/docs/generators/tabular-synthetic-data
[3] https://mostly.ai/docs/synthetic-datasets
[4] https://mostly.ai/docs/concepts/what-is-synthetic-data
[5] https://mostly.ai/what-is-synthetic-data
[6] https://aws.amazon.com/marketplace/pp/prodview-z4bb3qozmlg3c
[7] https://marketplace.databricks.com/details/0fc15edc-d3c9-488d-980e-b438fcc3c162/MOSTLY-AI_Synthetic-Data-Generator-by-MOSTLY-AI-for-Databricks

## Question 3a

What can you tell me about the methods this company uses to generate synthetic data off of tabular data?

## Response

Mostly AI employs advanced machine learning techniques to generate synthetic data from tabular data sources. Their approach involves several key components and methods:

## AI Model Training

- A separate AI model is trained for each data table provided[4]
- These models learn the patterns, correlations, distributions, and dependencies within each table[4]
- The platform requires a minimum of 5,000 data subjects (rows) for optimal results, though smaller datasets can be used[5]

## Synthetic Data Generation Process

- Once trained, the AI model performs random draws to generate new rows of synthetic data[4]
- This process ensures that generated rows do not directly correspond to specific rows in the original dataset[4]
- The resulting synthetic data retains the statistical characteristics of the original data, including correlations and distributions[4]

## Multi-Table Capabilities

- Mostly AI supports single-table, two-table, and multi-table synthetic data generation scenarios[2]
- For multi-table scenarios, the platform maintains referential integrity and aims to preserve correlations between tables[2]
- Users can define relationships between tables, such as foreign key relationships, to ensure proper data structure[2][5]

## Data Type Handling

- The platform automatically recognizes common data types in table columns[2]
- For text columns, Mostly AI can utilize Large Language Models (LLMs) to generate synthetic unstructured text that maintains correlations with other columns[2]

## Advanced Features

- Rebalancing: Allows for adjusting distributions to reduce bias or improve model accuracy[4]
- Imputation: Replaces missing values with AI-generated meaningful data[4]
- Temperature and Top P controls: Adjust the diversity of generated data, including the creation of outliers and edge cases[4]
- Fairness mechanisms: Ensure fair distributions for specified subgroups or attributes[4]

By leveraging these methods, Mostly AI's synthetic data generation platform aims to create highly accurate, privacy-compliant synthetic datasets that can serve as "drop-in replacements" for original tabular data while protecting the privacy of individual data subjects.

Citations:
[1] https://mostly.ai
[2] https://mostly.ai/docs/generators/tabular-synthetic-data
[3] https://mostly.ai/blog/comparison-of-synthetic-data-generation-methods
[4] https://mostly.ai/docs/concepts/what-is-synthetic-data
[5] https://mostly.ai/blog/how-to-generate-synthetic-data
[6] https://mostly.ai/what-is-synthetic-data
[7] https://mostly.ai/docs/synthetic-datasets
[8] https://marketplace.databricks.com/details/0fc15edc-d3c9-488d-980e-b438fcc3c162/MOSTLY-AI_Synthetic-Data-Generator-by-MOSTLY-AI-for-Databricks

## Question 4

Is this company able to generate synthetic data based off of unstructed data (e.g., PDF files, Word Documents)

## Response

Yes, Mostly AI has recently expanded its capabilities to include the generation of synthetic data from unstructured sources such as PDF files and Word documents. This feature, called "Synthetic Text," was launched to unlock high-value proprietary text data for organizations[2].

Key points about Mostly AI's unstructured data synthesis capabilities:

1. Support for various file formats: The platform can handle unstructured free-text data from formats including TXT, PDF, CSV, TIFF, JPG, PNG, JSON, DOCX, and XLSX[1].

2. Text data pipeline: Mostly AI's system can build, schedule, and automate unstructured data pipelines that extract and transform data into a standardized format[1].

3. Privacy protection: The platform automatically detects, classifies, and redacts sensitive information in unstructured data. It can optionally re-seed redactions with synthetic data to maintain the semantic meaning of the original text[1].

4. Named Entity Recognition (NER): Mostly AI uses proprietary NER models trained on diverse datasets spanning various domains, formats, and contexts to ensure sensitive data is identified and protected[1].

5. Quality evaluation: The platform provides tools to evaluate the quality of synthetic text, including analysis of character sets, distribution of character and term frequencies, and term co-occurrence[2].

6. Correlation preservation: Mostly AI's system aims to maintain correlations between synthesized text columns and other features in the dataset[2].

While Mostly AI initially focused on structured (tabular) data types, this expansion into unstructured data synthesis demonstrates the company's commitment to providing comprehensive synthetic data solutions for various data types and formats[2].

Citations:
[1] https://www.tonic.ai/press-releases/tonic-ai-launches-worlds-first-secure-unstructured-data-lakehouse-for-llms
[2] https://mostly.ai/blog/synthetic-text-data
[3] https://www.confident-ai.com/blog/the-definitive-guide-to-synthetic-data-generation-using-llms
[4] https://mostly.ai/what-is-synthetic-data
[5] https://mostly.ai/blog/how-to-generate-synthetic-data

## Question 5

What can you tell me about how easy it is to use the products offered by this company?

## Response

Based on user feedback and reviews, MOSTLY AI's synthetic data platform is generally considered easy to use, though there are some mixed opinions:

## Positive Aspects

- **Intuitive Interface**: Many users praise the platform's user-centric design and intuitive interface. The company has recently revamped its UI to make it more visually appealing and faster to use[3].

- **No Coding Required**: Several reviewers mention that they don't need to write code to produce high-quality synthesized data, making it accessible for non-engineers[2].

- **Quick Data Generation**: Users report that data generation is relatively quick and the results look reasonable[2].

- **Streamlined Process**: The platform allows users to quickly generate synthetic data without writing complex code, saving up to 80% of normal time dealing with synthetic data for some users[2].

## Areas for Improvement

- **Learning Curve**: Some users initially found it difficult to use the platform the way they wanted, suggesting there may be a learning curve for more advanced features[2].

- **UI Elements**: A few users suggested that the UI elements could be improved further, with one specifically mentioning a desire for a dark mode[2].

- **Advanced Features**: Some users expressed a desire to know more about the algorithms used and to have the ability to fine-tune parameters[2].

## Recent Enhancements

MOSTLY AI has made efforts to improve usability:

- They introduced a new intuitive user interface in version 200, aimed at providing more intuitive workflows[10].
- The company has implemented a stepper in the UI so users know exactly where they are in the process of catalog creation[3].
- They've added features like hover-over info buttons for advanced functionality[3].

Overall, while most users find MOSTLY AI's platform easy to use, especially for basic tasks, there may be a slight learning curve for more advanced features. The company appears to be actively working on improving user experience based on feedback.

Citations:
[1] https://mostly.ai
[2] https://aws.amazon.com/marketplace/reviews/reviews-list/prodview-z4bb3qozmlg3c
[3] https://mostly.ai/blog/mostly-ai-new-ui
[4] https://mostly.ai/docs/whats-new
[5] https://aimultiple.com/synthetic-data-generator
[6] https://www.g2.com/products/mostly-ai-synthetic-data-platform/reviews
[7] https://mostly.ai/docs/best-practices
[8] https://slashdot.org/software/p/MOSTLY-AI/
[9] https://www.reddit.com/r/ProductManagement/comments/1avf0jd/how_ai_helped_us_managing_user_feedback_probably/
[10] https://mostly.ai/blog/introducing-the-mostly-ai-synthetic-data-platform-v200

## Question 6

What can you tell me about privacy features offered by the company, security features offered by the company, and overall trustworthiness of the company with respect to the generation of synthetic data?

## Response

MOSTLY AI places a strong emphasis on privacy, security, and trustworthiness in their synthetic data generation platform. Here's an overview of their offerings in these areas:

## Privacy Features

- **No 1:1 Relationship**: The synthetic data generated has no direct correspondence to individual records in the original dataset, preventing re-identification of sensitive information[3][9].

- **Model Overfitting Prevention**: The platform removes excessive linked records that could lead back to a subject, reducing privacy risks[3].

- **Rare Category Value Protection**: MOSTLY AI can generate synthetic data with rare category values to ensure these attributes remain privacy-safe[2].

- **Extreme Value Protection**: The platform removes extreme values from data distributions to prevent revealing exceptional cases or outliers[2].

- **Time Series Protection**: For time series datasets, protection against extreme sequences is implemented to prevent re-identification[2].

- **Differential Privacy Option**: Users can choose to train synthetic data generators with or without differential privacy guarantees, providing mathematical privacy assurances if desired[7].

## Security Features

- **SOC 2 and ISO 27001 Certified**: The solution adheres to these security standards, ensuring robust data protection practices[3].

- **On-Premises and Private Cloud Options**: Available for installation in air-gapped environments or deployed in private cloud infrastructures for enhanced security[3].

- **Automatic Privacy Mechanisms**: State-of-the-art privacy mechanisms are automatically applied to ensure data safety and customer protection[3].

## Trustworthiness

- **Continuous External Audits**: The company undergoes regular external audits and legal assessments to ensure compliance[3].

- **Regulatory Compliance**: The platform complies with requirements of GDPR, CCPA, CPRA, HIPAA, PDPA, and APPI[3].

- **Industry Recognition**: MOSTLY AI is trusted by leading brands and data privacy experts[3].

- **Transparent Approach**: The company provides detailed information about their privacy-protection mechanisms and allows users to choose between empirical and theoretical privacy approaches[7].

- **High Accuracy**: The platform generates synthetic data that maintains statistical characteristics of the original data while ensuring privacy[4].

MOSTLY AI's commitment to privacy and security, along with their transparent approach and industry recognition, contributes to their overall trustworthiness in the field of synthetic data generation. Their platform is designed to mitigate privacy risks while maintaining data utility, making it a viable solution for organizations seeking to leverage their data assets safely and compliantly.

Citations:
[1] https://mostly.ai
[2] https://www.youtube.com/watch?v=RcKq4749qjs
[3] https://mostly.ai/privacy-and-security
[4] https://aws.amazon.com/marketplace/pp/prodview-z4bb3qozmlg3c
[5] https://www.zdnet.com/article/can-synthetic-data-solve-ais-privacy-concerns-this-company-is-betting-on-it/
[6] https://www.techtimes.com/articles/293699/20230714/top-5-best-synthetic-data-software-2023.htm
[7] https://mostly.ai/blog/differentially-private-synthetic-data-with-mostly-ai
[8] https://www.g2.com/products/mostly-ai-synthetic-data-platform/reviews
[9] https://mostly.ai/docs/concepts/privacy-protection

## Question 7

What can you tell me about the general history of this company?

## Response

MOSTLY AI was founded in 2017 in Vienna, Austria as a pioneer in synthetic data generation. Here are some key milestones in the company's history:

## Early Years and Founding

- Established in 2017 by a team of AI experts in Vienna
- Focused on developing AI-powered synthetic data generation technology

## Growth and Funding

- In January 2022, MOSTLY AI raised $25 million in Series B funding led by Molten Ventures
- This represented Europe's largest synthetic data investment at the time
- Total funding raised reached $31.14 million

## Product Development

- In 2022, MOSTLY AI launched version 2.0 of its synthetic data platform
- This version could automatically synthesize complex data structures
- The company expanded capabilities to include unstructured data synthesis in 2022

## Expansion

- While initially focused on Europe, MOSTLY AI began expanding into the US market
- By 2022, the company was working with multiple Fortune 100 banks and insurers in North America and Europe

## Recognition

- Listed as a Sample Vendor in Gartner's 2022 Hype Cycle for AI report
- Recognized in categories including Data-centric AI, Generative AI, and Synthetic Data

## Recent Developments

- Achieved ISO 27001:2013 re-certification in 2022, demonstrating commitment to information security
- Transitioned to a fully remote work model in October 2022
- As of 2022, had grown to 50 employees from 23 different nationalities

Throughout its history, MOSTLY AI has positioned itself as a leader in synthetic data generation, focusing on privacy-compliant solutions for AI/ML development, data sharing, and analytics across industries like banking, insurance, and telecommunications.

Citations:
[1] https://mostly.ai/blog/mostly-ai-2022-recap
[2] https://golden.com/wiki/Mostly_AI-EAVY854
[3] https://www.cbinsights.com/company/mostly-ai
[4] https://mostly.ai/news/mostly-ai-raises-25m-to-bring-synthetic-data-to-every-enterprise
[5] https://canvasbusinessmodel.com/blogs/brief-history/mostly-ai-brief-history

## Question 10

What can you tell me about which companies or organizations use this company to produce synthetic data?

## Response

MOSTLY AI has established partnerships with several prominent companies and organizations across various industries for synthetic data production:

## Financial Services

- Erste Group: A major European banking group that uses MOSTLY AI's synthetic data for accelerating innovation in digital banking and developing AI models for intelligent banking functions.
- JPMorgan: Leverages a synthetic data sandbox to speed up data-intensive proofs of concept with third-party vendors.

## Insurance

- Merkur Versicherung: An Austrian insurance firm that employs MOSTLY AI's synthetic data for innovation and meeting data protection requirements.
- Humana: A major U.S. healthcare company that uses MOSTLY AI's solutions, likely for privacy-safe data sharing and analysis.

## Telecommunications

- Telefónica (O2): Utilizes synthetic customer data for analytics purposes.

## Healthcare

- Anthem: Uses synthetic data for fraud detection and delivering personalized services to members.
- InGef (Institute for Applied Health Research Berlin): Collaborated with MOSTLY AI to develop a healthcare data platform for shareable synthetic health records.

## Other Notable Clients

- MOSTLY AI works with multiple Fortune 100 insurers and banks in Europe and North America.
- The company has expanded its client base to include global enterprises across various sectors.

It's worth noting that MOSTLY AI's typical clients are Fortune 100 banks, insurers, and telecommunications companies, reflecting the platform's appeal to large enterprises in highly regulated industries where data privacy and security are critical concerns.

Citations:
[1] https://mostly.ai
[2] https://mostly.ai/news/mostly-ai-2022-gartner-cool-vendors
[3] https://www.prnewswire.com/news-releases/mostly-ai-launches-synthetic-text-to-overcome-ai-training-plateau-and-unlock-high-value-proprietary-data-302263251.html
[4] https://www.syntho.ai/top-7-synthetic-data-companies-how-to-choose-the-one/
[5] https://www.citi.com/ventures/perspectives/pressrelease/investing-in-mostly-ai.html
[6] https://www.cbinsights.com/company/mostly-ai/customers
[7] https://www.techtimes.com/articles/293699/20230714/top-5-best-synthetic-data-software-2023.htm
[8] https://mostly.ai/what-is-synthetic-data
[9] https://mostly.ai/news/erste-group-embraces-synthetic-data
[10] https://techcrunch.com/2022/01/11/mostly-ai-raises-25-million-to-further-commercialize-synthetic-data-in-europe-and-the-u-s/?guccounter=1
