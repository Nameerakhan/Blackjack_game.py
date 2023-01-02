# Blackjack_game.py

import random

import clear

logo = """
.------.            _     _            _    _            _    
|A_  _ |.          | |   | |          | |  (_)          | |   
|( \/ ).-----.     | |__ | | __ _  ___| | ___  __ _  ___| | __
| \  /|K /\  |     | '_ \| |/ _` |/ __| |/ / |/ _` |/ __| |/ /
|  \/ | /  \ |     | |_) | | (_| | (__|   <| | (_| | (__|   < 
`-----| \  / |     |_.__/|_|\__,_|\___|_|\_\ |\__,_|\___|_|\_\\
      |  \/ K|                            _/ |                
      `------'                           |__/           
"""
                   


def deal_card():
    cards = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]
    card = random.choice(cards)
    return card




def calculate_score(cards):

    
    if sum(cards) == 21 and len(cards) == 2:
        return 0

      
        if 11 in cards and sum(cards) > 21:
            cards.remove(11)
            cards.append(1)
    return sum(cards)

def compare(user_score,computer_score):
  if user_score == computer_score:
     return "it's Draw 😶 "
  elif computer_score == 0:
    return "lose ,oppnent has a blackjack 😭"
  elif user_score ==0:
    return "win with Blackjack 🤩 "
  elif user_score>21:
    return "you went over so you Lose 😢!"
  elif computer_score>21:
    return "opponent went over ,You win 😎  "
  elif user_score >computer_score:
    return "You Win! 😁 "
  else:
    return "You Lose! 😤 "

def play_again():
  print(logo)
  user_cards = []
  computer_cards = []
  game_over = False
  for _ in range(2):
      user_cards.append(deal_card())
      computer_cards.append(deal_card())
  
 
  while not game_over:
  

      user_score = calculate_score(user_cards)
      computer_score = calculate_score(computer_cards)
      print(f" Your cards:{user_cards},current_score: {user_score}")
      print(f" Computer's first card:{computer_cards[0]}")
  
      if user_score == 0 or computer_score == 0 or user_score > 21:
          game_over = True
      else:

          user_deal = input("Type 'y' to get another card, type 'n'to pass: ")
          if user_deal == "y":
              user_cards.append(deal_card())
          else:
              game_over = True
  
 
  while computer_score != 0 and computer_score < 17:
      computer_cards.append(deal_card())
      computer_score = calculate_score(computer_cards)
  print(f"your final hand:{user_cards},final score:{user_score}.")
  print(f"computer's final hand:{computer_cards},final score:{computer_score}.")
  print(compare(user_score,computer_score))
  

game_continue = input("do you want the restart the game type'y' or 'n'")
if game_continue == "y":
  clear()
  play_again()
play_again()

