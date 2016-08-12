# Interview Dry-Run 

## Question 1
#### What is the most influential book or blog post you’ve read regarding web development?

While not specifically written material, I discovered the JavaScript Jabber podcast a while ago. It introduced me to the ember.js framework. 
Unfortunately, I never got the opportunity to implement it in my daily work life as my company at the time focused primarily on Flash development, 
but it definitely inspired me to learn more about emerging web technologies.

Since then, I've delved into Ruby on Rails, Python, and Django. This ultimately lead to a slightly more formal program through Udacity in full stack web development.

---

## Question 2
#### Tell me about a web application you have built. Why did you choose to build it? What did you learn? What challenges did you face and how did you overcome them?

I built a web application to assist in setting up a board game. The basic functionality of the app was to randomize the teams players use that can be customized with filters and other setup options. 
It initially started as a down-and-dirty javascript project that pulled data from and XML file. That was usable, but I had some ideal functionality that I didn't know how to implement. 
I wanted to allow multiple people to access the same setup on multiple devices. This required some sort of persistent data storage, but I had never worked with databases before.

I didn't want to turn to Flash since it doesn't play well on mobile devices, which are most likely to be used at the gaming table. My brother had worked in the industry for a few years, 
so I invited him to the project. He then showed me node.js and mysql, as well as current development environments that I had no idea about. I've now transitioned that project to a python back-end with postgres integration.

---

## Question 3
#### Write a function that takes a list of strings and returns a single string that is an HTML unordered list `(<ul>...</ul>)` of those strings. You should include a brief explanation of your code. Then, what would you have to consider if the original list was provided by user input?

```python
def unordered_list(strings):
  # creating unordered list tag
  lst = '<ul>'

  # iterate over strings
  for s in strings:
    # append list item tag with contents of one element in strings
    lst += '<li>%s</li>' % s

  # append closing unordered list tag
  lst += '</ul>'
  return lst

```

If the original list is supplied by user input, the function should check if the input is a list, and if the list contains strings.

---

## Question 4
#### List 2-3 attacks that web applications are vulnerable to. How do these attacks work? How can we prevent those attacks?

DDoS attacks are common to web applications. The attacker spams the web server with requests until it can no longer serve content. 
There is no known protection against this kind of attack, but the more robust the web server is, the more traffic it can handle before being overloaded.

Cross-site request forgery is when the attacker pretends to be a user it is not to gain access during authentication during oauth verification. 
Sending a generated state token with the authentication request to be checked when the response is returned can prevent this.

Brute force attacks are used to gain access to password-protected sections and content. Utilities like fail2ban can automatically configure a 
firewall to deny access from IP addresses after a certain number of failed attempts.

---

## Question 5
#### Here is some starter code for a Flask Web Application. Expand on that and include a route that simulates rolling two dice and returns the result in JSON. You should include a brief explanation of your code.

```python
from flask import Flask
app = Flask(__name__)

import json
import random


@app.route('/')
def hello_world():
  return 'Hello World!'

# Route takes one argument, the number of sides on the die
@app.route('/roll_dice/<int:sides>/json')
def roll_dice(sides):
  """Return the result of two dice with user-specified number of sides
  being rolled as a json object"""

  # Assign the result of the die roll
  die1 = random.randint(1,sides)
  die2 = random.randint(1,sides)

  # Return the results of the dice rolled as json string, sorted by key
  return json.dumps({'die1': die1, 'die2': die2}, sort_keys=True)

if __name__ == '__main__':
  app.debug = True
  app.run()

```

I've added the functionality to roll two dice and return the result as a json string. 
I've included the ability to pass the number of sides the dice have to the function since it wasn't specified and expands the functionality. 
The result of each die roll is assigned to a variable. The function returns the results of json.dumps(), sorted by key.

---

## Question 6
#### If you were to start your full-stack developer position today, what would be your goals a year from now? 

##### Full Stack Engineer
I would like to increase and share my knowledge of web app development. I'd also like to be an influential and integral part of my team. 
I'd like to spearhead the implementation of new technologies since collaboration and assisting others are passions of mine.
