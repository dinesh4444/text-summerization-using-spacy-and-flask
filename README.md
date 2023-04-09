# Text Summerization Using Spacy and Flask

1. Install Spacy and Flask libraries: You can install both libraries using pip. Open your terminal or command prompt and type

    pip install spacy
    pip install flask

2. Download the Spacy model: Spacy provides various language models, including English, German, French, etc. For this task, we'll use the English language model. Download it using the following command:

    python -m spacy download en_core_web_sm


3. Create a Flask app: Open your code editor and create a new file called app.py. Import Flask and create a new app object.

    from flask import Flask
    app = Flask(__name__)


4. Create a function to summarize text using Spacy: We'll use the en_core_web_sm model to extract the most important sentences from the README file. Here's an example function that you can use:

    import spacy

    def summarize(text):
        nlp = spacy.load("en_core_web_sm")
        doc = nlp(text)
        sentences = [sent.text.strip() for sent in doc.sents]
        keywords = list(doc.noun_chunks)
        summary = " ".join(sentences[:2])
        return summary

This function loads the Spacy model, extracts the sentences from the text, and concatenates the first two sentences as the summary.

5. Create a Flask route to summarize the README file: Add a new route to your Flask app that accepts a GET request and summarizes the README file. Here's an example route:

    @app.route('/summarize')
    def get_summary():
        with open('README.md', 'r') as f:
            text = f.read()
        summary = summarize(text)
        return summary

6. Test the app: Open your browser and navigate to http://localhost:5000/summarize. If everything is working correctly, you should see the summary of your README file displayed in the browser.


# Text Smmerization 
Text summarization is the process of creating a shorter version of a longer text while retaining its most important information. It involves identifying the key points, ideas, and concepts within a text and then condensing them into a more concise form, while still retaining the essence of the original content.

There are two main types of text summarization: extractive and abstractive. Extractive summarization involves selecting important sentences or phrases from the original text and combining them to form a summary. Abstractive summarization, on the other hand, involves generating new sentences that capture the meaning of the original text but may not be present in the original content.

Text summarization has many applications, including news article summaries, email triage, and automatic document summarization. It can save time and increase efficiency by allowing readers to quickly grasp the main points of a document without having to read through the entire text.

