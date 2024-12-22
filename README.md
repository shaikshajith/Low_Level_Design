# Low_Level_Design


E-Commerce Review System - Low-Level Design (LLD)
1. Problem Statement
The design objective of this document is to construct an E-Commerce Review System using Object-Oriented Programming (OOP) concepts in Java. In the proposed system, users can place their reviews of products, browse all reviews, and thus compute a final rating of the product.

This paper establishes the class structure, relations between classes, and interaction that provide the skeleton for the application. The approach is a best practice software in terms of simplicity, reusability, and maintainability.

2. Requirements Specification

2.1 Functional Requirements
Product Management:
	Products must be uniquely identifiable and have a product ID along with a name.
	Products can hold multiple reviews submitted by users.

Review Management:
	Users can submit a review that includes their name, text feedback, and an integer rating from 0 to 5.
	There should not be repetition of reviews by the same user.
	Ratings will be classified as "Poor," "Ok," or "Excellent."

Overall Rating:
	The system determines an overall product rating as the average of all submitted ratings.

Review Display:
	Users can see all submitted reviews and the overall product rating.

2.2 Non-Functional Requirements
Scalability:  Efficient handling of multiple products and reviews.
Performance:  Fast addition and retrieval of reviews.
Maintainability:  The design must follow modular principles to make updates easier in the future.


3. Class Design

3.1 Product Class
The `Product` class holds all product-related data and logic.
Attributes:
	`productId` (String): The unique identifier of the product.
	`productName` (String): The name of the product.
	`reviews` (List<Review>): The list holding all reviews submitted for this product.

Methods:
1. `addReview(Review review)`
	Adds a new review to the product.

2. `getReviews()`
	Returns a read-only list of reviews for safety.

3. `calculateOverallRating()`
	Calculates and returns the average rating of all submitted reviews.

3.2 Review Class
The `Review` class is a user review.
 
Fields:
	`reviewerName` (String): Name of the reviewer.
	`reviewText` (String): Textual feedback from the user.
	`rating` (double): Numeric rating, e.g., 4.5.
Methods:
1. `getReviewerName()`
   - Returns the reviewer's name.

2. `getReviewText()`
   Returns the review text.

3. `getRating()`
   Returns the numeric rating.

3.3 ReviewSystem Class
The `ReviewSystem` class is a product manager.

Attributes:
`products` (List<Product>): A list of all products in the system.

Methods:
1. `addProduct(Product product)`
	Adds a product to the system.

2. `getProductReviews(String productId)`
	Retrieves all reviews for a specific product.


3.4 Main Class
The `Main` class holds the program's entry point. It exemplifies the following aspects:
1. Product creation and addition of default reviews.
2. Interactive acceptance of user reviews.
3. Elimination of duplicate reviews from the same user.
4. Rating categorization into:
   • Poor (0–2)
   • Ok (2–4)
   • Excellent (4–5)
5. All reviews display and overall product rating.

4. Key Scenarios
4.1 Adding Reviews
	Input: Product ID, Product Name, Reviewer Name, Review Text, Rating.
	Validation: Check for duplicate reviews by reviewer name.
	Output: Confirm review addition and display the rating category.

4.2 Viewing Reviews
Action: Prompt user to view all reviews.
Output:
	All submitted reviews with reviewer name, rating, and feedback.
	Overall rating for the product.


5. Code Walkthrough

Main.java
	Entry point for the program.
	Manages user inputs and coordinates the interaction between the `Product` and `Review` classes.

Product.java
	Holds product information and manages all reviews related to it.
	Calculates the overall rating of the product.

Review.java
	Defines the structure of a review, including the reviewer's name, text feedback, and numeric rating.

ReviewSystem.java
	Adds and manages products.

6. Demonstration (Sample Output)

Step 1: Add Preloaded Reviews
	`Deepak` - 4.8 - "Amazing product! Highly recommend."  
	`Santosh` - 4.0 - "Good value for the money."
  'Shajith' - 3.5 - "Its Ok"

Step 2: User Adds a New Review  
	Input:Reviewer Name: `John`  
	Review: "Needs improvement in packaging."  
	Rating:`3.5`  
	Output: "Rating category: Ok"

Step 3: Prevent Duplicate Review  
	Input: Same Reviewer Name: `John`
	Output: "User John has already submitted a review."

Step 4: View All Reviews  
Output:
   Overall Rating for Product: 4.3
	Reviewer: Deepak, Rating: 4.8, Feedback: Amazing product! Highly recommend.
	Reviewer: Santosh, Rating: 4.0, Feedback: Good value for the money.
	Reviewer: John, Rating: 3.5, Feedback: Needs improvement in packaging.
   


7. Conclusion
The E-Commerce Review System showcases Object-Oriented Design principles as the system is divided into well-thought classes (`Product`, `Review`, `ReviewSystem`). A user can add reviews and calculate an overall rating in addition to displaying feedbacks quite smoothly.


