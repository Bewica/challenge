# Technical Challenge

This technical challenge has been designed to assess the technical skills of candidates for our technology team.

It aims to achieve the following objectives:

1. Python coding skills assessment
2. Micro-service building with Docker
3. Basic Machine Learning

The first two objectives should be able to be completed under ten minutes for an experienced programmer in that specific skill. The machine learning challenge is designed to take less than half an hour.

The challenge should be representative of the technologies use in the company.

It should be possible to complete any of the objectives independently.

> Note: It is Ok to complete only some objectives

## Objective I - Python

Create a Python 3 module with one function called `password_check`.

Make the above function take a string parameter representing a password and return a boolean depending on the password being acceptable or not.

Define a dictionary with the following keys to be used as parameters in order to check if a password is acceptable or not:

```json
{
  "length": 10,
  "must_have_numbers": true,
  "must_have_caps": true
}
```

Make the function verify that any given password string complies with the requirements defined in the dictionary.

Add unit tests to verify the correct implementation of the password strength rules.

Make the function executable in the command line in the following way:

```shell
$ python3 password_check.py pa$$word
false
```

Commit the answer to GitHub or pack it in a zip file and email the results.

## Objective II - Micro-services

Create a `Flask` simple application which takes a string using `curl` in the following way:

```shell
curl -H "Content-Type: application/json" \
-d '{"password":"pa$$word"}' \
-X GET http://localhost:5002/password_check
```

Use the function of the previous exercise or just return always true or false if you skipped Objective I.

Create a `Dockerfile` for a docker container which serves the previous application.

Create a `docker-compose.yml` file to serve the previous file.

## Objective III - Basic machine learning

One of the most common problems companies face is CEO impersonation attacks. This is a form of fraud where a scammer sends an email purporting to be from the CEO of a company or another senior executive and commonly requesting the finance team to make a payment to a third party.

In this challenge we're going to use machine learning to automatically detect if an email from a person is legitimate. For that purpose we're going to use the corpus of emails from Enron. You can learn more about the [Enron](https://en.wikipedia.org/wiki/Enron_scandal) scandal in the Wikipedia.

Now imagine that you're a worker from Enron in the year 2000 and you receive an email from the boss [Ken Lay](https://en.wikipedia.org/wiki/Kenneth_Lay) asking you to pay a huge invoice. Fortunately you have access to the email servers files and you can use machine learning to find out if the email is genuine.

![The boss](https://upload.wikimedia.org/wikipedia/commons/c/ce/Ken_Lay.jpg)

Use the following Colab notebook to create a feature vector of 3000 features for each email in the Enron dataset. Populate each feature with the number of times each of the 3000 most frequent English words appears in the email.

Afterwards train a classifier to detect Ken's emails and provide a confusion matrix of the performance.

For your convenience we have already labeled Ken's emails in the dataset and extracted the body of the emails in a separated column.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Bewica/challenge/blob/master/mail_from_ken.ipynb)

> IMPORTANT: Make your own copy of this notebook. Otherwise everyone will be able to see your work (including other candidates)
