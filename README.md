# Microsoft Retail Analytics Case Competition
Teams were challenged to envision an AI use case within the retail and ecommerce space and then demonstrate its technical feasibility by developing a prototype using Microsoft Azure's Cloud Services. 

The product was judged in various categories including **orginality**, **technical feasibility** and **impact potential**.

Team Standing: Top 15% out of 300+ submissions

# Our Team's Submission

The following provides a summary of our team's AI use case, and provides an overview of our technical impelementation.

## Business Opportunity

Our target customer is Best Buy Canada. The following table provides an overview of how AI extends the current analytical capabilities of Best Buy.

| Business Opportunity | Status Quo  | Proposed AI Solution  |
| ---   | :-: | :-: |
| Understand the quality of customer in-store experience | In-store sales data | Combine with in-store video analytics |
| Personalize the customer experience through mobile app | Not addressed | Recommender system in mobile app |

## Success Metrics
This solution is aimed to impact the following business growth metrics:

1)	Maximize conversion rate 
2)	Maximize total ticket from the sale

## Technical Implementation Overview
The following table provides an overview of the team's approach to demonstrate technical feasibility of the prototype app.
For this purposes of this competition, the input data is assumed to be available by our customer, Best Buy.

| Proposed AI Solution | Input Data  | How Feasbility is Demonstrated  |
| ---   | --- | --- |
| Video Analytics |  Images from video recordings gathered from in-store surveillance system | From a sample image, automatically extract customer's age, gender, and the location of the detected person within the store. |
| Mobile App Product Recommendations | Historic customer app click data | Deploy an ML Classifier simulated to predict a customer's affinity score to each product category |

### Prototype Architecture

The architecutre used in this prototype is as illustrated below.

![Prototype Architecture](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/prototype_architecture.png)

The architecture uses the following Azure services:

* **Azure Blob Storage**
* **Azure Databricks**
* **Azure Machine Learning service**
* **Azure Container Registry**
* **Azure Kubernetes Service**


### Video Analytics Feature
Please refer to this [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/image_analytics.ipynb) for code implementation details.  

To demonstrate feasibiility, we developed an image parsing tool using **Azure's Computer Vision Analyze Image Rest API**. We then test this tool using a [Test Image](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/img_1_jpeg.jpg) which is intended to resemble the type of images that will be supplied to the app in a real-world application.

The figure below shows an illustration of that test image and resultant metadata outputted by our code. While this simulated test demonstrates that our prototype is capable of generating the intended metadata (i.e. age, gender, location of person in store), further tests are recommended. This includes testing to further ascertain the app's robustness to image blur (e.g. caused by movement by people) and other image quality considerations (e.g. clarity of the captured facial features). These tests are recommended to be performed directly using the input data from the source (i.e. images collected from Best Buy's in-store video surveillance system) to match the real-world setting as much as possible.

![Video Analytics](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/sample_image_read.png)

### Content-Based Recommendation Engine Feature
Please refer to the two notebooks below for code implementation details:
1) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/mmlspark_lightgbm_prototype.ipynb) for collecting the synthetic dataset and training a **LightGBM** classifer model that ranks a customer's affinity to product categories [1]
2) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/lightgbm_prototype.ipynb) for deploying the model on **Azure Kubernetes Services** 

[1] Please note that for the purposes of demonstrating workability of our proposed solution for this competition, we train an _arbitrary_ machine learning model (in this case, a LightGBM) on a synthetic dataset, making our model and its performance results meaningless. However, we describe the intention of our model in a real world setting as below.

![Image_file](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/intent_recommendation_engine.JPG)

The above illustration demonstrates how we determine a customer's affinity to a product category (based on their historic click data and purchases made through the mobile app) and use this to subsequently make product recommendations.

## Impact Potential
Please refer to the [Customer Journey Theoretical Framework](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf) that forms the basis of our proposed AI solution. Reference to this Framework is made in the discussion below.

**Video Analytics (Azure Computer Vision Analyze Image Rest API)**

*	Most Best Buy stores already have an in-store surveillance system in place. This makes the proposed solution **readily adoptable**.
*	The AI extension to the current approach provides the decision makers with **the power to design tests to quantify the impact** of change in pricing, rewards/points, product display and promotions on the customer in-store experience. This can be tracked by monitoring changes in footfall traffic in areas within the store.
*	Footfall traffic analytics provides improved visibility on the [trigger questions](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf) the customers are entering the store with.

**App Recommender System (Azure Machine Learning)**

*	Personalized shopping experiences are delivered through **tailored product recommendations** to optimally support the customer through the **“active evaluation”** phase to maximize probability of arriving at the [moment of commitment](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf). It will also be designed to trigger new [moments of inspiration](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf)

## Product Impact Demonstration
Please refer to the [Sample Dashboard](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Sample%20Dashboard.pdf) illustrating the type of insights our app has the potential to unlock for Best Buy.
