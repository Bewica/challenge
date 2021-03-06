# Technical Challenge

This technical challenge has been designed to assess the technical skills of candidates for our technology team.

It aims to achieve the following objectives:

1. Go, Node.js or Python coding skills assessment
2. Micro-service building with Docker
3. Basic Machine Learning
4. Web application

The first two objectives should be able to be completed under ten minutes for an experienced programmer in that specific skill. The machine learning and web application challenges are designed to take less than half an hour each.

The challenge should be representative of the technologies use in the company.

It should be possible to complete any of the objectives independently.

> Note: It is Ok to complete only some objectives

## Objective I - Go, Node.js or Python

Create a Go, Node.js or Python 3 module with one function called `password_check` or `passwordCheck`.

Make the above function take a string parameter representing a password and return a boolean depending on the password being acceptable or not.

Define a dictionary or an object with the following keys to be used as parameters in order to check if a password is acceptable or not:

```json
{
  "length": 10,
  "must_have_numbers": true,
  "must_have_caps": true
}
```

Make the function verify that any given password string complies with the requirements defined in the dictionary or object.

Add unit tests to verify the correct implementation of the password strength rules.

Make the function executable in the command line in the following way:

```shell
$ go run passwordCheck.go pa$$word
false
```
or

```shell
$ node password.check.js pa$$word
false
```
or

```shell
$ python3 password_check.py pa$$word
false
```

Commit the answer to GitHub or pack it in a zip file and email the results.

## Objective II - Micro-services

Create a `Go`, `Node.js` or `Flask` simple application which takes a string using `curl` in the following way:

```shell
curl -H "Content-Type: application/json" \
-d '{"password":"pa$$word"}' \
-X GET http://localhost:5000/password_check
```

Use the function of the previous exercise to return the strength of a password (or just return always `1` or `0` for `True` and `False` if you skipped Objective I).

Create a `Dockerfile` for a docker container which serves the previous application.

Create a `docker-compose.yml` file to serve the previous file.

## Objective III - Web application

Cyber security threats evolve over time as well as companies infrastructure. A company's chief information security officer (CISO) should always have an up to date view of the security situation of their company. For this reason, security scans will happen asynchronously in the background and need to be shown to users as soon as they become available.

On this exercise we will need to create a very simple application with the following functionality:

- A React interface that will allow to add users to a Firestore collection named `users`. Each user will have a `name`, `surname` and `email` field.
- A Node.js backed with a route that will allow to check if a certain email has been compromised against the [';--have i been pwned?](https://haveibeenpwned.com/) database of compromised email addresses. This backend function won't return the result and instead will store it directly in Firebase in a new field for the existing user document called `isBreached`. Version 3 of the haveibeenpwned api now requires a subscription, you can mock an api response instead.
- The web application will display the breach results for the existing users as soon as they become available in the users collection.

```
+-------------+          +-------------+
|             |          |             |
|   Crawler   +----------> Realtime DB |
|  (Node.js)  |          | (Firestore) |
|             |          |             |
+---+---------+          +-----^-------+
    ^                          |
    |                   +------v---+
    |                   |          |
    +-------------------+ Web app. |
                        | (React)  |
                        |          |
                        +----------+
```

Note that:

- Credentials to access and unprotected Firestore database will be provided separately as a challenges-*.json file.
- A number of JS libraries exist for the haveibeenpwned API.
- Tests for the Web application are essential.

## Optional: Objective IV - Basic machine learning

One of the most common problems companies face is CEO impersonation attacks. This is a form of fraud where a scammer sends an email purporting to be from the CEO of a company or another senior executive and commonly requesting the finance team to make a payment to a third party.

In this challenge we're going to use machine learning to automatically detect if an email from a person is legitimate. For that purpose we're going to use the corpus of emails from Enron. You can learn more about the [Enron](https://en.wikipedia.org/wiki/Enron_scandal) scandal in the Wikipedia.

Now imagine that you're a worker from Enron in the year 2000 and you receive an email from the boss [Ken Lay](https://en.wikipedia.org/wiki/Kenneth_Lay) asking you to pay a huge invoice. Fortunately you have access to the email servers files and you can use machine learning to find out if the email is genuine.

![Enron](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Logo_de_Enron.svg/200px-Logo_de_Enron.svg.png)

Use the following Colab notebook to create a feature vector of 3000 features for each email in the Enron dataset. Populate each feature with the number of times each of the 3000 most frequent English words appears in the email.

Afterwards train a classifier to detect Ken's emails and provide a confusion matrix of the performance.

For your convenience we have already labeled Ken's emails in the dataset and extracted the body of the emails in a separated column.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Bewica/challenge/blob/master/mail_from_ken.ipynb)

> IMPORTANT: Make your own copy of this notebook. Otherwise everyone will be able to see your work (including other candidates)

> NOTE: A training matrix with 3000 features can take a long time to compute. It's suggested to work with a small number of emails. It's ok to submit the results for a model trained with a subset of the emails even if the performance of the algorithm is not great.
