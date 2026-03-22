# 🏷️ ShopEase Product Category Classifier

An AI-powered product categorization system for e-commerce platforms. This project uses machine learning to automatically classify products into appropriate categories based on their names and descriptions.

## 🚀 Features

- **Multi-Category Classification**: Supports 8 product categories
- **High Accuracy**: Uses TF-IDF vectorization and Naive Bayes classification
- **Multiple Interfaces**: Web app (Flask), Streamlit app, and API
- **Batch Processing**: Process multiple products at once
- **Beautiful UI**: Modern, responsive web interface
- **Analytics Dashboard**: Visualize model performance and data insights

## 📊 Supported Categories

1. **Electronics** - Phones, laptops, cameras, etc.
2. **Clothing** - Shirts, dresses, shoes, etc.
3. **Home & Garden** - Furniture, decor, tools, etc.
4. **Sports & Outdoors** - Fitness equipment, camping gear, etc.
5. **Books & Media** - Books, movies, games, etc.
6. **Beauty & Health** - Makeup, skincare, supplements, etc.
7. **Automotive** - Car parts, accessories, etc.
8. **Toys & Games** - Toys, board games, etc.

## 🛠️ Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Setup

1. **Clone or download the project files**

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Generate sample data** (optional):
   ```bash
   python data_generator.py
   ```

4. **Train the model**:
   ```bash
   python classifier.py
   ```

## 🚀 Running the Application

### Option 1: Flask Web App
```bash
python app.py
```
Then open http://localhost:5000 in your browser.

### Option 2: Streamlit App
```bash
streamlit run streamlit_app.py
```
Then open the URL shown in the terminal.

### Option 3: Command Line
```bash
python classifier.py
```

## 📁 Project Structure

```
project/
├── requirements.txt          # Python dependencies
├── data_generator.py         # Generate sample training data
├── text_preprocessor.py      # Text preprocessing utilities
├── classifier.py            # Main ML classifier
├── app.py                   # Flask web application
├── streamlit_app.py         # Streamlit application
├── templates/
│   └── index.html          # Web app template
├── product_data.csv         # Sample training data (generated)
├── product_classifier_model.pkl  # Trained model (generated)
└── README.md               # This file
```

## 🔧 Usage

### Web Interface

1. **Single Product Classification**:
   - Enter product name and/or description
   - Click "Classify Product"
   - View predicted category and confidence scores

2. **Batch Processing** (Streamlit):
   - Upload CSV file with product data
   - Process all products at once
   - Download results

3. **Analytics** (Streamlit):
   - View category distributions
   - Analyze price and rating patterns
   - Model performance metrics

### API Usage

```python
import requests

# Single prediction
response = requests.post('http://localhost:5000/predict', json={
    'product_name': 'iPhone 13 Pro',
    'description': 'Latest smartphone with advanced camera features'
})

result = response.json()
print(f"Category: {result['predicted_category']}")
print(f"Confidence: {result['confidence']:.2%}")
```

## 🧠 Model Details

### Architecture
- **Text Preprocessing**: NLTK-based cleaning, lemmatization, stopword removal
- **Feature Extraction**: TF-IDF vectorization with n-grams
- **Classification**: Multinomial Naive Bayes (default)
- **Alternative Models**: Random Forest, SVM

### Performance
- **Accuracy**: ~85-90% on test data
- **Training Time**: < 30 seconds for 1000 samples
- **Prediction Time**: < 100ms per product

## 📈 Customization

### Adding New Categories

1. Update the categories dictionary in `data_generator.py`
2. Add relevant keywords for each category
3. Regenerate training data
4. Retrain the model

### Model Tuning

Modify parameters in `classifier.py`:
```python
# TF-IDF parameters
max_features=5000,
ngram_range=(1, 2),
min_df=2,
max_df=0.95

# Classifier parameters
classifier = MultinomialNB()  # or RandomForestClassifier, SVC
```

## 🐛 Troubleshooting

### Common Issues

1. **Model not found error**:
   - Ensure you've run `python classifier.py` first
   - Check that `product_classifier_model.pkl` exists

2. **NLTK data missing**:
   - The app will automatically download required NLTK data
   - If issues persist, manually download:
     ```python
     import nltk
     nltk.download('punkt')
     nltk.download('stopwords')
     nltk.download('wordnet')
     ```

3. **Port already in use**:
   - Change port in `app.py`: `app.run(port=5001)`
   - Or kill existing process using the port

### Performance Tips

- Use GPU acceleration for large datasets
- Implement caching for repeated predictions
- Consider using a production WSGI server for Flask

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

- NLTK for text processing
- Scikit-learn for machine learning
- Flask and Streamlit for web interfaces
- Bootstrap for UI components

---

**Happy Classifying! 🎉** 
