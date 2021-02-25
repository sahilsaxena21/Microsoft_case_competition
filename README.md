# Microsoft Retail Analytics Case Competition
Teams were challenged to envision an AI use case within the retail and ecommerce space and then demonstrate its technical feasibility by developing a prototype using Microsoft Azure's Cloud Services. 

The product was judged in various categories including **orginality**, **technical feasibility** and **impact potential**.

Our Team's Result: Top 15% out of 300+ submissions

# Our Team's Submission

The following provides a summary of our team's selected AI use case, and provides an overview of our technical impelementation.

## Business Opportunity

Target Customer: Best Buy Canada

| Business Opportunity | Status Quo  | Proposed AI Solution  |
| ---   | :-: | :-: |
| Understand the quality of customer in-store experience | In-store sales data | Combine with in-store video analytics |
| Personalize the customer experience through mobile app | Not addressed | Recommender system in mobile app |

## Project Success Metrics

1)	Maximize conversion rate 
2)	Maximize total ticket from the sale

## Technical Implementation Overview

| Proposed AI Solution | Input Data  | Demonstrating Technical Feasbility  |
| ---   | --- | --- |
| Video Analytics |  Images from video recordings gathered from the in-store surveillance system | Extract in-store customer's age, gender, and location of person within the store mapped to pre-defined areas of the store (e.g Isle 3, cashier queue etc.) | Combine with in-store video analytics |
| Mobile App Product Recommendations | In-store and mobile app transactions and other activity performed by the customer (orders, returns, exchanges) *	Product and service list with detailed descriptions | Probabilistic classifier to rank customer affinity to product categories |

### Prototype Architecture

![Prototype Architecture](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/prototype_architecture.png)

As per the proposed architecture, the following Azure services are used in the app:

* **Azure Blob Storage** is a storage service optimized for storing massive amounts of unstructured data. The input data is stored here.
* **Azure Databricks** is a managed Apache Spark cluster where model training and evaluating is performed.
* **Azure Machine Learning service** is used in this scenario to register the machine learning model.
* **Azure Container Registry** is used to package the scoring script as a container image which is used to serve the model in production.
* **Azure Kubernetes Service** is used to deploy the trained models to web or app services.

### Content-Based Recommendation Engine Feature

Please refer to the two notebooks as follows:
1) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/mmlspark_lightgbm_prototype.ipynb) for collecting the synthetic dataset and training a **LightGBM** classifer model
2) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/lightgbm_prototype.ipynb) for deploying the model on **Azure Kubernetes Service** 

### Video Analytics Feature
Please refer to the [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/image_analytics.ipynb) for the code implementing this app feature

![Video Analytics](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/sample_image_read.png)

As illustrated in the above figure, **Azure's Computer Vision Analyze Image Rest API** is able to extract the following metadata from the sample image provided:
* date and time of when the image was taken
* age and gender of detected individuals in the input image
*	the location of the person within the store using bounding box coordinates. This is then mapped to particular areas within the store.

## Benefits of Proposed Approach
Our value proposition strives to capture the “low-hanging fruits” using AI i.e. high ratio of impact-to-implementation effort. Please refer to the attached [Customer Journey Theoretical Framework](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf) that forms the basis of our proposed AI solution. Reference to this Framework is made in the discussion below.

**Video Analytics (Azure Computer Vision Analyze Image Rest API)**

*	Most Best Buy stores already have an in-store surveillance system in place. This makes the proposed solution **readily adoptable**.
*	The AI extension to the current approach provides the decision makers with **the power to run tests to quantify the impact** of change in pricing, rewards/points, product display and promotions on the customer in-store experience.
*	The AI solution will achieve this by **measuring footfall traffic** and capturing the **hot spots** within the store to answer key questions such as: Why are customers visiting my store?
*	Improved visibility on the [trigger questions](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf) the customers are entering the store with.

Note: The entire video analytics process will be **anonymized** i.e. customers will NOT be ID’d to protect their privacy. Only their age and gender (as detected by MS Computer Vision) will be identified. Acceptable privacy and security standards will be identified and applied to the analytics process and data storage.

**App Recommender System (Azure Machine Learning)**

*	Personalized shopping experiences are delivered through **tailored product recommendations** to optimally support the customer through the **“active evaluation”** phase to maximize probability of arriving at the [moment of commitment](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf). It will also be designed to trigger new [moments of inspiration](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf)

## Next Steps
Please refer to the [Sample Dashboard](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Sample%20Dashboard.pdf) illustrating the type of insights our app has the potential to deliver to our target customer (Best Buy).
