# Spam SMS Classifier Web App

## Overview

This project is a simple, interactive web application that classifies SMS messages as either **spam** or **not spam** using a machine learning model. The app is built with [Gradio](https://www.gradio.app/)

---

## Data

The dataset used in this project is the [SMS Spam Collection Data Set](https://archive.ics.uci.edu/ml/datasets/sms+spam+collection), which includes labeled examples of SMS text messages:

- **Labels**:
  - `spam`: The message is unwanted or unsolicited (e.g., marketing, scams).
  - `ham`: The message is legitimate and not spam.

- **Structure**:
  - Two columns: `label` and `text_message`
  - Approximately 5,575 entries

The data was preprocessed and split into training/testing datasets. A pipeline using `CountVectorizer` and a Naive Bayes classifier (`MultinomialNB`) was trained on this data.

---

## Model Architecture

- **Text Vectorization**: 
  - `CountVectorizer()` to convert raw text into token counts.
- **Classification Model**: 
  - `MultinomialNB` (Naive Bayes), ideal for word count–based features.

- **Pipeline**:
  - `text_clf = Pipeline([('vect', CountVectorizer()), ('clf', MultinomialNB())])`

---

## App Design

The Gradio app is laid out in a **horizontal split**:

- **Left Panel**:
  - Label: "What is the text message you want to test?"
  - Multi-line input box
  - Buttons: `Clear` and `Submit`

- **Right Panel**:
  - Label: "Our App has determined:"
  - Output box showing whether the message is spam
  - `Flag` button for user feedback

All interactive elements are built with Gradio Blocks and launched in a local or public browser session.

---

## Functionality

- The `sms_prediction(text)` function takes raw text input and uses the trained pipeline to classify it.
- The app responds with a message such as:
  - `"The text message: '<your message>' is spam."`
  - `"The text message: '<your message>' is not spam."`
- Additional functionality:
  - Clear input with `Clear` button
  - Submit for prediction with `Submit` button
  - Flag feedback with `Flag` button

---

## Considerations

- **Model Limitations**:
  - The current classifier may mislabel messages with ambiguous language or uncommon spam indicators.
  - Accuracy could be improved with more sophisticated models (e.g., TF-IDF, SVM, LSTM).

- **Interface Design**:
  - Lightweight and user-friendly for quick experimentation
  - Suitable for demo or educational purposes


---

## Author
Dax Kelson
