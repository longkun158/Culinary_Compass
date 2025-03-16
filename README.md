# Culinary Compass
## Goals

### Culinary Compass is an recommendation system built to be your new trusted food advisor. It helps users to try new food and new taste based on your own unique preferences.
### User experience:

- Input: Flavors (Salty, sour, ...) + Allergy (Peanutes, Almond, ...)
- Output: Menu Dishes (Plus restaurant information, dish descriptions, ...)
- Interaction: User will rate the "positive" or "negative" for the chosen dish after ordering.

## Methodology

Culinary Compass leverage Flavor Graphs (Read more here: https://github.com/lamypark/FlavorGraph), a Graph Neural Network with more than 6600 ingredients and 2000 chemical compounds describing the relationship of ingredients. This food science background is the backbone for Culinary Compass. Each ingredients and chemical compound is represented in a map with 300 coordinate embeddings.

The application uses IPCA, Cosine Similarity and Bayesian Personalized Ranking (BPR) as main algorithm to recommend dishes.

## Algorithm:
- Using IPCA to reduce dimenson for each embedded dishes restaurant. Each dish contains several ingredients, meaning they will have several dimensons. IPCA will reduce these dimensons while maintaining the most information (variance).
- Cosine Similarity is used to compare the processed embeddings of Flavors and Dishes. The highest similarity will be shown.
- Bayesian Personalized Ranking (BPR) is used to increase/reduce the weight of each interacted dish by the user after they rate. The weights are stored under each user ID to learn dinamically for each usage.

## Data Description:

- new_menu.csv (Output): A data set includes dishes, restaurant information, ingredients, ... from Toronto area. There are 523 dishes.
- new_flavorgraph_df.csv (Input): A dateset includes flavor/preferences of users. There are 11 inputs
- menu_embedded.pkl: Embedded dishes from new_menu.csv 
- flavor_embedded.pkl: Embedded flavors from new_flavorgraph_df.csv
- new_nodes.csv and FlavorGraph Node Embedding.pickle: Two main files contain embeddings regarding ingredients and chemical compounds from Flavor Graphs.

## Limitation and Future Work:

### Limitations:
- The Menu data set is now only in the Greater Toronto Area. With larger Food Menu Dataset, user will have more relatable options.
- Input are only flavors and preferences at this moment. With a comprehensive data set, the application can implement other features, such as: Cuisine, Temperature (Hot or cold), Location, ...
- The system needs user to use the app to learn preferences from them. The more they use, they better its accuracy.

### Future work:
- New and comprehensive data set can improve the features of the app immensely.
- A Graph Neural Network can be built (When we have enough data) to build relationship between Users - Dishes - Ingredients. This new algorithm promises to have a better understanding of the complex relationships between Users - Dishes - Ingredients to have even better personalized results.

