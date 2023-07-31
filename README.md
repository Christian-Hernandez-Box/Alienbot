# Alienbot
AlienBot is an exciting project that brings the concept of artificial intelligence and UFO excitement from the 1950s to life. Imagine chatting with an intelligent chatbot that pretends to be an alien from another planet!

The goal of the project is to create an AlienBot that can convincingly fool users into thinking they are interacting with a real extraterrestrial. While it might not pass a true Turing test, the fun challenge is to see if users believe they are talking to a genuine alien (hence the "E.T.uring" test).
```
class AlienBot:
  # potential negative responses
  negative_responses = ("no", "nope", "nah", "naw", "not a chance", "sorry")
  # keywords for exiting the conversation
  exit_commands = ("quit", "pause", "exit", "goodbye", "bye", "later")
  # random starter questions
  random_questions = (
        "Why are you here? ",
        "Are there many humans like you? ",
        "What do you consume for sustenance? ",
        "Is there intelligent life on this planet? ",
        "Does Earth have a leader? ",
        "What planets have you visited? ",
        "What technology do you have on this planet? "
    )

  def __init__(self):
    self.alienbabble = {'describe_planet_intent': r'', 'answer_why_intent': r'why are you( asking me so many questions)\?', 'cubed_intent': r'can you cube the number (\d+)\?', 'describe_planet_intent': r'.*\s*your planet.*'}

  # Define .greet():
  def greet(self):
    self.name = input("Hello! What is your name? ")
    will_help = input(f"Hi {self.name}, I'm Etcetera. I'm not from this planet. Will you help me learn about your planet? ")
    if will_help in self.negative_responses:
      print("Ok, have a nice Earth day!")
    return self.chat()
    

  # Define .make_exit():
  def make_exit(self, reply):
    for words in self.exit_commands:
      if words in reply:
        print("Ok, have a nice Earth day!")
        return True

  # Define .chat():
  def chat(self):
    reply = input(random.choice(self.random_questions)).lower()
    while not self.make_exit(reply):
      reply = input(self.match_reply(reply))
    return

  # Define .match_reply() below:
  def match_reply(self, reply):
    matched_intent = None
    for intent, regex_pattern in self.alienbabble.items():
        found_match = re.match(regex_pattern, reply)
        if found_match:
            matched_intent = intent
            break

    if matched_intent == "describe_planet_intent":
        return self.describe_planet_intent()
    elif matched_intent == "answer_why_intent":
        return self.answer_why_intent()
    elif matched_intent == "cubed_intent":
        return self.cubed_intent(found_match.groups()[0])  # Use the found_match from the loop
    else:
        return self.no_match_intent()


  # Define .describe_planet_intent():
  def describe_planet_intent(self):
    responses = ("My planet is a utopia of diverse organisms and species. ", "I am from Opidipus, the capital of the Wayward Galaxies. ")
    return random.choice(responses)

  # Define .answer_why_intent():
  def answer_why_intent(self):
    responses = ("I come in peace. ", "I am here to collect data on your planet and its inhabitants. ", "I heard the coffee is good. ")
    return random.choice(responses)
       
  # Define .cubed_intent():
  def cubed_intent(self, number):
    number = int(number)
    cubed_number = number**3
    return f"Yes, {number} is {cubed_number}."

  # Define .no_match_intent():
  def no_match_intent(self):
    responses = ("Please tell me more. ", "Tell me more! ", "Why do you say that? ", "I see. Can you elaborate? ", "Interesting. Can you tell me more? ", "I see. How do you think? ", "Why? ", "How do you think I feel when you say that? ")
    reply = input(random.choice(responses))
    return self.match_reply(reply)
```
Expected outcome:
```
Hello! What is your name? Christian
Hi Christian, I'm Etcetera. I'm not from this planet. Will you help me learn about your planet? sure
Is there intelligent life on this planet? yes
Why do you say that? why are you asking me so many questions?
I am here to collect data on your planet and its inhabitants. can you cube the number 3?
Yes, 3 is 27.thats cool
Why? I dont want to talk to you anymore goodbye
I see. Can you elaborate?
```
