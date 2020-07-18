# Facebook_Friend_Recommendation_Project
Built ML models that recommend new friends to a user.

### About the Project

- Data for this project is taken from Facebook's recruting challenge on Kaggle.
- It can be downloaded from [here](https://www.kaggle.com/c/FacebookRecruiting).
- Data contains two columns:  
    - source_node         (int64)  
    - destination_node    (int64)
- Given data is basically a directed social graph, we have to predict missing links to recommend users.
- It is basically a Link Prediction problem in graph theory.
- Each data point basically represents an edge between the source node and the destination node.

### Approach to the Problem
- The problem could be mapped to a supervised learning problem of binary classification.
  - If an edge exists between two nodes, we represent it by 1 and by 0 otherwise.
  - Since, we are only provided with class labeled 1 datapoints i.e. node exists between them, we generate class labeled 0 datapoints i.e. node doesn't exist between them, after closely analyzing the data.
- Using the given data, we generated training samples of good and bad links from the given directed graph and for each link got some features like:
  - no. of followers,
  - is he followed back,
  - page rank,
  - katz score,
  - adar index,
  - some svd fetures of adj matrix,
  - some weight features etc.

and trained ML models based on these features to predict links. 
- Some reference papers and videos :  
    - https://www.cs.cornell.edu/home/kleinber/link-pred.pdf
    - https://www3.nd.edu/~dial/publications/lichtenwalter2010new.pdf
    - https://kaggle2.blob.core.windows.net/forum-message-attachments/2594/supervised_link_prediction.pdf
    - https://www.youtube.com/watch?v=2M77Hgy17cg

### Business objectives and constraints:  
- No low-latency requirement.
- Probability of prediction is useful to recommend high probability links.

### Performance metric for supervised learning:  
- Both precision and recall is important so F1 score is a good choice
- Confusion matrix
