# Microsoft Case Competition

## Business Problem

| Challenge | Status Quo  | Proposed AI Solution  |
| ---   | :-: | :-: |
| Gap 1: Lack of understanding of the quality of customer in-store experience | In-store sales data | Combine with in-store video analytics |
| Gap 2: Personalizing the customer experience through mobile app | Not addressed | Recommender system in mobile app |

## Project Success Metrics

The success metrics of the proposed AI solution are:
1)	Maximize conversion rate 
2)	Maximize total ticket from the sale


## Benefits of Proposed Approach
Our value proposition strives to capture the “low-hanging fruits” using AI i.e. high ratio of impact-to-implementation effort. Moreover, our proposed AI solutions attempts to address the business needs by taking a deep dive into the consumer behaviour. Please refer to the attached Customer Journey Theoretical Framework that forms the basis of our proposed AI solution. Reference to this Framework is made in the discussion below.
Video Analytics (MS Computer Vision)
●	Most (if not all) Best Buy stores already have an in-store surveillance system in place. This makes the proposed solution readily adoptable.
●	The AI extension to the current approach provides the decision makers with added visibility into the impact of change in pricing, rewards/points, product display and promotions on the customer in-store experience.
●	The AI solution will achieve this by measuring footfall traffic and capturing the hot spots within the store to answer key questions such as: Why are customers visiting my store?
●	Improved visibility on the “trigger questions” (refer the Framework) the customers are entering the store with.
●	Please refer to the example dashboard for an illustration of the insights planned to be provided by our video analytics solution

Note: The entire video analytics process will be anonymized i.e. customers will NOT be ID’d to protect their privacy. Only their age and gender (as detected by MS Computer Vision) will be identified. Acceptable privacy and security standards will be identified and applied to the analytics process and data storage.
App Recommender System (Azure ML)
●	Personalized shopping experiences are delivered through tailored product or service recommendations to optimally support the customer through the “active evaluation” phase to maximize probability of arriving at the “moment of commitment” (refer the Framework). It will also be designed to trigger new “moments of inspiration”.
●	This will be achieved by using classification learning based recommender system which will match the customer to a curated list of products/services based on features such as customer’s historic buying patterns, buying patterns of other similar users as the customer, and the customer’s search history using the app. MS Personalizer will also be trained to automatically scrape popular technology websites such as (but not limited to) Techmeme, Recode, TechCrunch and VentureBeat. Using a text-mining similiarity technique (e.g. K-means), it will automatically detect technology trends and be used as an additional feature in the app recommender system. 

Note: It is proposed that both of these AI solutions inform each other. For example, the in-store manager will be able to make in-store optimization decisions based on general market trends . Please refer to the architecture diagram for more details.
4.	What data will be used?

The following data will be used as input to the proposed AI solution:

●	In-store and mobile app transactions by customer (orders, returns, exchanges)
●	News scraped from various online technology websites
●	Product and service list with detailed descriptions
●	App search term history by customer

The following data will be the output from the proposed AI solution:

●	In-store customer age and gender
●	Dwell time of customer-product interactions
●	Footfall traffic
●	Emerging market trends across the tech websites (using a similarity-based algorithm)
●	Customer segmentation using topic modelling


5.	What MS technologies are chosen? Do they meet the needs? 
Please refer to the proposed architecture as illustrated below. The architecture is specifically designed to be scalable as per business requirements. Please refer to this notebook, for some of the sizing decisions to be considered and its business implications.
 







Appendix A - Minimum Viable Product
1.	How does recommender system work?
Please refer to the Github repo for more details on the implementation.
As a demonstration of the technical feasibility of our proposed solution, we use a synthetic dataset adapted from the Criteo dataset, a well known dataset of website ads that can be used to optimize the Click-Through Rate (CTR). The dataset contains a record of historic customer purchases, which is thought to be readily available from the organization’s database. An overview of the dataset is as illustrated below. 

We build a classification model to predict the product category that a customer shows the highest affinity towards.
Customer ID	Customer Name	Product Category	Purchase Value
32423141	Gary Roberts	Video Games and Accessories	$50.45
34324332	Darren Fynn	Karaoke Audio and Recording	$150.69
34234123	Owain Metsy	Outdoor Living	$55.52
23423134	Frank Stable	Wearable Tech, Health and Fitness	$110.47
The model is based on LightGBM, which is a gradient boosting framework that uses tree-based learning algorithms. Finally, we take advantage of MMLSpark library, which allows LightGBM to be called in a Spark environment and be computed distributely. 
2.	How does the video analytics tool work?
Please refer to the Github repo for more details on the implementation and the sample image used.
A summary of the workings of the Computer Vision technology is shown below. The Computer Vision Analyze Image Rest API is used to extract the following metadata :
•	Extract the number of people from a given image
•	Extract the demographics information such as age and gender
•	Extract the location of the person within the store using bounding box coordinates


Azure’s Computer Vision Technology at Work
 

Output from Video Analytics
 










The following provides a high-level overview of the intent.

Business Need: The project aims to fulfill two gaps in brick and mortal retail stores. The target customer for this MVP is Best Buy Canada. 

Gap 1: Lack of understanding of the quality of customer in-store experience. This includes lack of knowledge on the purpose of customer in-store visits. It also includes lack of feedback from customer in-store visits.

Gap 2: Personalizing the customer experience through mobile app. This includes lack of customized shopping experience during use of the Best Buy mobile app.

The project aims to fulfill the identified gaps as follows:
1) Provide for in-store video analytics (img_analytics.ipynb)
2) Build a recommender system in mobile app (mmlspark_lightgbm_prototype.ipynb, lightgbm_prototype.ipynb)

The success metrics of the proposed AI solution are:
1) Maximize conversion rate
2) Maximize total ticket from the sale

Competition result: Top 15% out of 300+ teams.
