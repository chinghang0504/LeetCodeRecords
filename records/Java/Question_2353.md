# [LeetCode Records](../../README.md) - Question 2353 Design a Food Rating System

### Attempt 1: Use a HashMap to store the food and its food item key-value pairs and a HashMap to store the cuisine and its SortedSet of food items
```java
class FoodRatings {

    class FoodItem {

        String food;
        String cuisine;
        int rating;

        FoodItem(String food, String cuisine, int rating) {
            this.food = food;
            this.cuisine = cuisine;
            this.rating = rating;
        }
    }

    private Map<String, FoodItem> foodToFoodItem;
    private Map<String, SortedSet<FoodItem>> cuisineToFoodItems;

    public FoodRatings(String[] foods, String[] cuisines, int[] ratings) {
        foodToFoodItem = new HashMap<>();
        cuisineToFoodItems = new HashMap<>();

        for (int i = 0; i < foods.length; i++) {
            FoodItem foodItem = new FoodItem(foods[i], cuisines[i], ratings[i]);
            foodToFoodItem.put(foods[i], foodItem);

            SortedSet<FoodItem> sortedSet = cuisineToFoodItems.get(cuisines[i]);
            if (sortedSet == null) {
                sortedSet = new TreeSet<>((foodItem1, foodItem2) -> {
                    if (foodItem1.rating != foodItem2.rating) {
                        return foodItem2.rating - foodItem1.rating;
                    } else {
                        return foodItem1.food.compareTo(foodItem2.food);
                    }
                });
                cuisineToFoodItems.put(cuisines[i], sortedSet);
            }
            sortedSet.add(foodItem);
        }
    }
    
    public void changeRating(String food, int newRating) {
        FoodItem foodItem = foodToFoodItem.get(food);
        SortedSet<FoodItem> sortedSet = cuisineToFoodItems.get(foodItem.cuisine);
        sortedSet.remove(foodItem);
        foodItem.rating = newRating;
        sortedSet.add(foodItem);
    }
    
    public String highestRated(String cuisine) {
        SortedSet<FoodItem> sortedSet = cuisineToFoodItems.get(cuisine);
        return sortedSet.first().food;
    }
}

/**
 * Your FoodRatings object will be instantiated and called as such:
 * FoodRatings obj = new FoodRatings(foods, cuisines, ratings);
 * obj.changeRating(food,newRating);
 * String param_2 = obj.highestRated(cuisine);
 */
```
- Runtime: 192 ms (Beats: 76.47%)
- Memory: 73.48 MB (Beats: 67.96%)

<br>
