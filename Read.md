📚 Book Recommendation Engine using K-Nearest Neighbors
A machine learning-based book recommendation system that uses collaborative filtering and K-Nearest Neighbors (KNN) algorithm to suggest similar books based on user ratings.
🎯 Project Overview
This project implements a book recommendation engine using the Book-Crossings dataset, which contains 1.1 million ratings from 90,000 users on 270,000 books. The system identifies books similar to a given book by analyzing rating patterns across users.
🔧 Technologies Used

Python 3.x
NumPy - Numerical computations
Pandas - Data manipulation and analysis
Scikit-learn - Machine learning (KNN algorithm)
SciPy - Sparse matrix operations
Matplotlib - Data visualization (optional)

📊 Dataset
Book-Crossings Dataset:

1.1 million ratings (scale 1-10)
270,000 books
90,000 users

Source: The dataset is automatically downloaded in the notebook from FreeCodeCamp.
🚀 How It Works
1. Data Preprocessing

Load book and rating data from CSV files
Filter out sparse data:

Remove users with fewer than 200 ratings
Remove books with fewer than 100 ratings


This ensures statistical significance in recommendations

2. Create User-Book Matrix
                User1  User2  User3  User4  ...
Book A            5      0      4      5    ...
Book B            0      3      0      4    ...
Book C            4      5      3      0    ...
3. Train KNN Model

Uses cosine distance metric to measure similarity
Finds the 5 nearest neighbors (most similar books)
Algorithm: Brute force (most accurate for high-dimensional data)

4. Generate Recommendations
The system compares rating patterns (book "fingerprints") to find similar books.
💻 Usage
Basic Function Call
pythonget_recommends("Where the Heart Is (Oprah's Book Club (Paperback))")
Expected Output
python[
  "Where the Heart Is (Oprah's Book Club (Paperback))",
  [
    ["I'll Be Seeing You", 0.8],
    ['The Weight of Water', 0.77],
    ['The Surgeon', 0.77],
    ['I Know This Much Is True', 0.77],
    ['The Lovely Bones: A Novel', 0.72]
  ]
]
Output Format:

First element: Input book title
Second element: List of 5 recommended books with their distances

Lower distance = More similar books
Distance ranges from 0 (identical) to 1 (completely different)



🧮 Algorithm Details
K-Nearest Neighbors (KNN)

Algorithm Type: Lazy learning (instance-based)
Distance Metric: Cosine distance
K Value: 6 (returns 6 neighbors, skip first as it's the input book itself)
Search Method: Brute force

Why Cosine Distance?
Cosine distance measures the angle between rating vectors, making it ideal for comparing user preferences regardless of rating scale differences.
Distance = 1 - (A · B) / (||A|| × ||B||)
📈 Key Features
✅ Collaborative filtering based on user ratings
✅ Handles sparse data efficiently using sparse matrices
✅ Statistical significance through data filtering
✅ Fast recommendations using optimized KNN
✅ Returns books with similarity scores
🔍 Understanding the Results
Distance Interpretation:

0.0 - 0.3: Very similar books
0.3 - 0.6: Moderately similar books
0.6 - 0.8: Somewhat similar books
0.8 - 1.0: Different books

Lower distances indicate stronger recommendations!
📝 Code Structure
├── Data Loading
│   ├── Download dataset
│   └── Load CSV files into DataFrames
│
├── Data Cleaning
│   ├── Filter users (>= 200 ratings)
│   └── Filter books (>= 100 ratings)
│
├── Matrix Creation
│   ├── Pivot table (books × users)
│   └── Convert to sparse matrix
│
├── Model Training
│   └── Fit KNN model
│
└── Recommendation Function
    ├── Find book in matrix
    ├── Get k-nearest neighbors
    └── Return formatted results
🧪 Testing
The notebook includes a test function that validates:

Correct book title returned
5 recommendations provided
Recommended books match expected titles
Distance values within acceptable range (±0.05)

pythontest_book_recommendation()
# Output: "You passed the challenge! 🎉🎉🎉🎉🎉"
📚 Example Recommendations
Input: "The Queen of the Damned (Vampire Chronicles (Paperback))"
Output:

Catch 22 (0.79)
The Witching Hour (0.74)
Interview with the Vampire (0.73)
The Tale of the Body Thief (0.54)
The Vampire Lestat (0.52)

The system successfully identifies other books in the Vampire Chronicles series and similar fiction!
🎓 Learning Outcomes
This project demonstrates:

Collaborative Filtering: Recommending items based on similar user preferences
Dimensionality Reduction: Filtering sparse data for better performance
Distance Metrics: Using cosine similarity for recommendation systems
Data Preprocessing: Handling real-world messy data
Matrix Operations: Working with sparse matrices efficiently

🔗 Resources

Book-Crossings Dataset
Scikit-learn KNN Documentation
FreeCodeCamp Machine Learning Curriculum

👤 Author
Created as part of the FreeCodeCamp Machine Learning with Python certification.
📄 License
This project is open source and available for educational purposes.

Note: This is a learning project demonstrating collaborative filtering and KNN algorithms for recommendation systems. For production use, consider additional optimizations and error handling.