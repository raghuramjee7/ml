# Machine Learning Basics

## Classification
1. Supervised, Unsupervised, Semi Supervised, Self Supervised
2. Online Learning, Batch Learning
3. Instance Based, Model Based

### Supervised
In supervised learning, you have training data that teaches your model how to predict.  
Examples - Classification, Regression

### Unsupervised
Here, there is no output in training data to train with. We just analyse and get insights from the data.   
Examples - Clustering, Visualisation, Dimensionality Reduction, Anamoly detection, Novelty detection, associate rule learning

### Semi Supervised
We have partially labelled data here. 

### Self Supervised
Here, all the data is unlabelled, we get the labels by predicting the type of species. Lets say we have images of pets, we mask some part of the image and train a model to repair the image, in this way it will be able to group the pets and we can label them.

### Reinforcement Learning
Here, we have a learning system called an agent, this performs actions in an environment and it gets rewards/penalities in return. It must then devise the best strategy, called policy to improve its reward.  

### Batch Learning
In this learning, the system is not capable of learning on the go, once it is trained, it is deployed, and cannot be trained as we go. This is called offline learning. This model performance decays over time and this is called `model rot` or `data drift`. To train this, we train it fresh with new data + old data and deploy it. 

### Online Learning
Here, we continuously feed new data to the model, in instances or mini batches. `Out of core learning` means that all the data cannot fit in a single memory, the cpu processes it batch wise. We have an important concept called `learning rate`. This tells the model how fast to adapt to changing data. High learning rate means rapidly adapting to new data, and quickly forget new data. Here, the major problem is that if we have bad data, the models adapts to it and spoils very quickly.

### Instance based
Here, the model learns each instance by heart and makes new predictions by comparing this to everything else. 

### Model Based
Here, you build a model from a given set of training data and then predict outcomes based on the generalised rules (generalisation)

**NOTE**
1. Performance measures can be of two types, Fitness function, that tells us how good our model is, or cost function that tells us how bad our model is. 
2. Sampling bias originates from sampling noise (no true representation of data)
3. Overfitting is when the model fits too well to the training data and fails in the testing data. This can be avoided with making the model simple. The process of making a model simple and constraining it, to reduce overfitting is called `regularisation`.
4. A hyperparameter is a parameter of the learning algorithm and not the model. It must be set prior to training and remains the same throughout.
5. Underfitting is when the model fails on both training and testing data, this can be avoided by using a more complex model. 
6. Error is also called generalisation error or out of the box error. 
7. We use validation set to test between different models and choose something, and train it with full set and then test it. This is called holdout validation.  
8. We can also use cross validation but training time will be high.  
9. NFL (No Free Lunch) Theorem - If you make no assumption of data, then there is no reason to choose one model over another. 


