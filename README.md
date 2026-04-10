# Q&A Chatbot

A simple yet effective question-answering chatbot that uses TF-IDF vectorization and cosine similarity to match user questions with predefined answers.

## Features

- **Natural Language Processing**: Preprocesses user input by converting to lowercase and removing punctuation
- **TF-IDF Vectorization**: Uses scikit-learn's TfidfVectorizer to convert text to numerical vectors
- **Similarity Matching**: Employs cosine similarity to find the best matching answer
- **Intelligent Threshold**: Only returns answers if similarity score exceeds 0.6 threshold
- **Interactive Console**: Simple command-line interface for user interaction

## Requirements

- Python 3.x
- numpy
- scikit-learn

## Installation

Install the required packages:

```bash
pip install numpy scikit-learn
```

## Usage

Run the chatbot:

```bash
python app.py
```

### Example Interaction

```
User: what is python?
Bot: Python is a high-level programming language.

User: what is machine learning
Bot: Machine learning is a field of AI that learns from data.

User: how is weather?
Bot: Sorry, I don't understand your question.

User: exit
```

## How It Works

1. **Preprocessing**: User input is converted to lowercase and all punctuation is removed
2. **Vectorization**: Both predefined questions and user input are converted to TF-IDF vectors
3. **Similarity Calculation**: Cosine similarity is computed between user input and all predefined questions
4. **Matching**: The question with the highest similarity score is selected
5. **Response**: If similarity > 0.6, the corresponding answer is returned; otherwise, a default message is shown

## Predefined Q&A Pairs

- "what is python" → "Python is a high-level programming language."
- "what is machine learning" → "Machine learning is a field of AI that learns from data."
- "what is chatbot" → "A chatbot is a program that answers user questions."
- "what is nlp" → "Natural Language Processing deals with human language."

## Customization

To add more Q&A pairs, edit the `qa_pairs` dictionary in `app.py`:

```python
qa_pairs = {
    "your question": "your answer",
    "another question": "another answer",
    # Add more pairs here
}
```

To adjust the similarity threshold (higher = stricter matching), change the value in this line:

```python
if best_score > 0.6:  # Change 0.6 to your desired threshold
```

## Exit

Type `exit` to quit the chatbot.
