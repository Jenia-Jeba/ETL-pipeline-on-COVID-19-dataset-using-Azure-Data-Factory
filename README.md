# ETL-pipeline-on-COVID-19-dataset-using-Azure-Data-Factory

Working on an interesting project of building a real-world ETL pipeline using Azure Data Factory on COVID-19 dataset! Here are the summary of the steps from my project journey so far:

![data ingestion requirements](https://github.com/Jenia-Jeba/ETL-pipeline-on-COVID-19-dataset-using-Azure-Data-Factory/assets/39514905/a286b6e8-c5ca-4241-b142-4988203f26e4)

I have utilized two approaches --- 1) from HTTP link (https://www.ecdc.europa.eu/en/covid-19/data) and 2) Azure Data Factory's Blob storage, to successfully ingest COVID-19 dataset and Eurostat's population data, meticulously categorized by age groups, into Azure data lake. My work encompassed mastering the copy activity, establishing link services, configuring datasets, and expertly crafting control flow activities for pipelines for adeptly managing real-world scenarios. Moreover, I've introduced triggers to automate workflows, adhering to best practices and naming conventions.

![Data ingestion - from HTTP](https://github.com/Jenia-Jeba/ETL-pipeline-on-COVID-19-dataset-using-Azure-Data-Factory/assets/39514905/f098f286-9527-40da-975d-e04634ab69c6)


![Data ingestion - from blob storage](https://github.com/Jenia-Jeba/ETL-pipeline-on-COVID-19-dataset-using-Azure-Data-Factory/assets/39514905/afe98201-c2b1-4ab2-a1f2-cd1a593786d5)


I've harnessed the power of Azure Data Factory to meticulously ingest crucial COVID-19 data sourced from the ECDC website, which means, from http connection into the data lake. This entails extracting data via HTTP requests. Navigating through four distinct files, each containing vital EU country information, I've leveraged the foundation laid in the previous module. I've introduced advanced scalability concepts, effectively refining the pipeline's architecture. My work encompasses in-depth website exploration, thorough data overviews, initial pipeline setup, dynamic variables and parameters, and the strategic utilization of control flow activities like "Lookup" and "ForEach." The result is a robust, metadata-driven pipeline, establishing a solid framework for efficient and effective data integration. 


I have parameterized the pipeline for enhanced flexibility, utilizing parameters instead of variables. I have explored schedule triggers to automate pipeline execution, connecting triggers to pipelines and passing parameters at runtime. The focus was on enhancing pipeline reusability and efficiency. I have also demonstrated how to consolidate multiple triggers into a single pipeline execution for copying various datasets.


By utilizing a configuration JSON file, I've enabled the simultaneous processing of four files through a single pipeline using a trigger. This configuration file contains the necessary data for processing, including URLs and filenames. After uploading the file to Azure storage, I've made adjustments within Azure Data Factory. I've created a Lookup activity to retrieve data from the configuration file, and a Foreach activity to iterate through each file entry. The copy activities within the Foreach loop are dynamically parameterized using the obtained values. After addressing initial errors and fine-tuning the configuration, I've successfully executed the pipeline through the trigger, copying all four files concurrently. This consolidation significantly enhances the efficiency and scalability of the data integration process.





I've embarked on building an efficient data flow using Azure Data Factory. By enabling debugging and configuring the source, I ensured accurate data manipulation. I made strategic decisions between inline sources and data sets, optimizing for consistency and reusability. Crafting a tailored data set for Data Lake Storage Gen2, I controlled schema validation and fine-tuned data sampling through sample files. This laid the groundwork for seamless data manipulation, with projection, partitioning, and schema inspection enhancing accuracy. The upcoming phase involves implementing a filter transformation for precise data extraction based on specific criteria. Stay tuned as I navigate data orchestration in Azure Data Factory! 

I harnessed the power of the Filter Transformation within Azure Data Factory. With a clear objective to refine my data, I skillfully curated information related to Europe while excluding non-relevant data points, such as total figures. By leveraging the expression editor and utilizing functions like "not is null," I achieved a streamlined dataset that aligns precisely with my analytical goals. This transformative step paves the way for more focused insights and enhanced data quality. Join me in the next phase as I explore the Select Transformation for further data shaping! 


I delved into the intricacies of data transformation using Azure Data Factory's Select Transformation. With a focus on efficiency, I streamlined my data flow by dropping irrelevant columns like continent and Rate 14 Day. Leveraging fixed and rule-based mappings within the Select Transformation, I adeptly renamed columns and transformed data types to suit my project's requirements. This skill empowers me to fine-tune data for precise analysis, ensuring only essential information is carried forward. Stay tuned for the next stage as I continue enhancing my data orchestration journey! 


I employed the Pivot Transformation within Azure Data Factory to refine and reshape my data. By focusing on European countries and merging columns, I pivoted daily counts into distinct categories: confirmed cases count and deaths count. This transformation streamlined the dataset, allowing for clearer insights into the pandemic's impact. As I navigated through the process, I also gained proficiency in using aggregate functions and column naming conventions. Join me in the upcoming stages as I continue to mold my data into a more informative and actionable form! 

I tackled the task of enriching our data by integrating a Lookup Transformation within Azure Data Factory. The goal was to incorporate a 2-digit country code to our dataset, which already featured a 3-digit country code. We began by setting up a data set for the lookup file and establishing the source. Then, utilizing the Lookup Transformation, we merged the new country code data with our existing records through a left outer join. Additionally, we took the opportunity to streamline our output by implementing a Select Transformation, optimizing our columns for the desired result. With this step complete, our data is now more comprehensive and structured for the upcoming phases of our project. Stay tuned as we proceed with further enhancements and insights! 


I honed in on the Sink Transformation within Azure Data Factory to encapsulate the outcomes of our data transformations into an output file. To initiate this process, we crafted an ADF data set within Data Lake Storage Gen2 and defined the file structure. Through this process, we ensured that the Spark cluster would write and partition the data in line with our specifications. Our journey culminated in the establishment of the pipeline that will execute the data flow, effectively sending our enriched dataset through the transformations and into the designated sink. This crucial stage will witness the culmination of our efforts as our data is processed and finalized for analysis and insights. Join us in the next lesson as we delve into the execution of the pipeline, translating our preparations into tangible results. 

![Azure Transformation - Data flow 2](https://github.com/Jenia-Jeba/ETL-pipeline-on-COVID-19-dataset-using-Azure-Data-Factory/assets/39514905/ae93d39d-415f-458c-8b94-8746b1168692)


In this concluding lesson, we orchestrated the execution of the Data Flow by creating a pipeline within Azure Data Factory. Through this pipeline, we invoked our meticulously designed Data Flow, initiating its execution and enabling the processing of our transformed data. We embarked on both manual and triggered executions, unveiling the intricate balance between cluster startup time and the actual transformation process. A glance at the execution details and performance metrics highlighted the efficiency of the process, with the cluster intelligently starting, executing, and concluding without incurring extra runtime charges. We dived into the Sink Transformation settings, exploring options like single-file output and partitioning strategies. Ultimately, the pipeline's culmination materialized in the generation of a processed CSV file, a tangible result that marked the successful execution of our Data Flow. This journey equipped us with the skills and insights necessary to wield Azure Data Factory for orchestrating complex data transformations and extracting valuable insights from raw data. 

![Dataflow pipeline](https://github.com/Jenia-Jeba/ETL-pipeline-on-COVID-19-dataset-using-Azure-Data-Factory/assets/39514905/efc2880f-b6c3-4fb8-a871-1b6879a8f3a0)
