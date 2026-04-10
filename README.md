

#Converts to lowercase
#Removes punctuation
#Makes text uniform
import string
import numpy as np
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity

qa_pairs = {
    "what is python": "Python is a high-level programming language.",
    "what is machine learning": "Machine learning is a field of AI that learns from data.",
    "what is chatbot": "A chatbot is a program that answers user questions.",
    "what is nlp": "Natural Language Processing deals with human language."
}

def preprocess(text):
    text = text.lower()
    text = text.translate(str.maketrans("", "", string.punctuation))
    return text

questions = [preprocess(q) for q in qa_pairs.keys()]

vectorizer = TfidfVectorizer()
question_vectors = vectorizer.fit_transform(questions)

while True:
    user_input = input("User: ")

    if user_input.lower() == "exit":
        break

    clean_input = preprocess(user_input)
    user_vector = vectorizer.transform([clean_input])

    similarity_scores = cosine_similarity(user_vector, question_vectors)
    best_match_index = np.argmax(similarity_scores)
    best_score = similarity_scores[0][best_match_index]

    if best_score > 0.6:
        print("Bot:", list(qa_pairs.values())[best_match_index])
    else:
        print("Bot: Sorry, I don't understand your question.")
