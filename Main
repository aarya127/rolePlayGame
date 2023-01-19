#          
#=======================================================          
#   Aarya Shah        
#=======================================================          
#   

import check
import math

class Character:
  ''' 
  Fields: 
     name(Str) 
     st(Nat)
     hp(Nat)
     max_hp(Nat)
     mp(Nat)
     max_mp(Nat)
     level(Nat)
     
  Requires:  
     st, max_hp are both strictly greater than 0.
  '''
  def __init__(self, new_name, strength, 
               maximumHP, maximumMP):
    '''
    Initializes a Character object self with 
    name new_name, st strength,
    hp and max_hp of maximumHP, and
    mp and max_mp of maximumMP, and
    level should start at 1.
    
    Effects: Mutates self
    
    __init__: Character Str Nat Nat Nat -> None
    Requires
      0 < strength, maximumHP, level
      maximumHP > hp
      maximumMP > mp
    '''
    self.name = new_name
    self.st = strength
    self.hp = maximumHP
    self.max_hp = maximumHP
    self.mp = maximumMP
    self.max_mp = maximumMP
    self.level = 1
    
  def __eq__(self, other):
    '''
    Returns True if self and other are equal and False otherwise
    
    __eq__: Character Any -> Bool
    '''
    return isinstance(other, Character) and\
           self.name == other.name and\
           self.st == other.st and\
           self.hp == other.hp and\
           self.max_hp == other.max_hp and\
           self.mp == other.mp and\
           self.max_mp == other.max_mp and\
           self.level == other.level
  
  def __repr__(self):
    '''
    Returns a string representation of self
    
    __repr__: Character -> Str
    '''
    x = "{0.name}\nLevel: {0.level}\nStrength: {0.st}\nHP: {0.hp}/{0.max_hp}\nMP: {0.mp}/{0.max_mp}"
    return x.format(self)

  
  def cast_spell(self, cost, damage, enemy):
    '''
    Casts a spell if self is able that requires cost mp to cast and
    deals damage to enemy. A message is printed if the enemy is 
    defeated or there was not enough mp to cast the spell.
    
    Effects: 
       Prints to screen
       Mutates self
       Mutates enemy
    
    cast_spell: Character Nat Nat Character -> None
    
    Examples:
       c = Character("Test", 1, 4, 5)
       e = Character("Test", 1, 4, 5)
       c.cast_spell(3, 10, e) => None
       and e.hp is mutated to 0
       and c.mp is mutated to 2
       and "Enemy defeated" is printed (no quotes).
       
       c = Character("Test", 1, 4, 5)
       e = Character("Test", 1, 4, 5)
       c.cast_spell(13, 10, e) => None
       and "Not enough MP" is printed (no quotes).
       
       c = Character("Test", 1, 4, 5)
       e = Character("Test", 1, 4, 5)
       c.cast_spell(3, 2, e) => None
       and e.hp is mutated to 2
       and c.mp is mutated to 2
    '''
    error_msg = "Not enough MP"
    defeated_msg = "Enemy defeated"
    if self.mp >= cost:
      self.mp = self.mp - cost
      enemy.hp = enemy.hp - damage
      if enemy.hp <= 0:
        enemy.hp = 0
        print(defeated_msg)
    else:
      print(error_msg)
    

  def level_up(self):
    '''
    Performs a level-up for self. Increase stats 10% plus 1
    via mutation of self.
    
    Effects: Mutates self
    
    level_up: Character -> None
    
    Examples:
       c = Character("Test", 1, 4, 5)
       c.level_up() => None
       and c.level is mutated to 2
       and c.st is mutated to 2
       and c.hp is mutated to 5
       and c.max_hp is mutated to 5
       and c.mp is mutated to 6
       and c.max_mp is mutated to 6
    '''
    self.level = self.level + 1
    self.st = self.st + (1 + math.floor(self.st * 0.1))
    self.hp = self.hp + (1 + math.floor(self.hp * 0.1))
    self.max_hp = self.max_hp + (1 + math.floor(self.max_hp * 0.1))
    self.mp = self.mp + (1 + math.floor(self.mp * 0.1))
    self.max_mp = self.max_mp + (1 + math.floor(self.max_mp * 0.1))
    
  

def all_punch(players, enemy):
  '''
  all_punch(players, enemy) consumes and mutates a (listof Character) in 
  players and a single Character in enemy, returns None but simulates all the 
  players punching an enemy. 
  
  Effects: Mutates players
  
  all_punch: (listOf Characters) Character -> None
  
  Examples:
    c1 = Character("Celso", 12, 10, 11)
    e1 = Character("E1", 2, 5, 10)
    print(c1)
    print(e1)
    c1.cast_spell(20, 10, e1) => None
    c1.level_up()
    print(c1)
    d1 = Character("C1", 10, 10, 10)
    d2 = Character("C2", 1, 10, 10)
    d3 = Character("C3", 20, 20, 10)
    e2 = Character("E2", 20, 20, 10)
    L = [d1, d2, d3]
    all_punch(L, e2) => None
    
    and the following is printed
    Celso
    Level: 1
    Strength: 12
    HP: 10/10
    MP: 11/11
    E1
    Level: 1
    Strength: 2
    HP: 5/5
    MP: 10/10
    Not enough MP
    Celso
    Level: 2
    Strength: 14
    HP: 12/12
    MP: 13/13
    and all of d1, d2, d3 have levelled up and e2's hp is now 0.
  '''
  for player in players:
    enemy.hp = enemy.hp - (2 * player.st)
    if enemy.hp <= 0:
      enemy.hp = 0
      for player in players:
        player.level_up()
      return None

##Examples      
c1 = Character("Celso", 12, 10, 11)
e1 = Character("E1", 2, 5, 10)
print(c1)
print(e1)
c1.cast_spell(20, 10, e1)
c1.level_up()
check.expect("Level", c1.level, 2)
check.expect("St", c1.st, 14)
check.expect("HP", c1.hp, 12)
check.expect("MP", c1.mp, 13)
check.expect("HP", e1.hp, 5)
print(c1)     
d1 = Character("C1", 10, 10, 10)
d2 = Character("C2", 1, 10, 10)
d3 = Character("C3", 20, 20, 10)
e2 = Character("E2", 20, 20, 10)
L = [d1, d2, d3]
check.expect("Example 1", all_punch(L, e2), None)
check.expect("Level", d1.level, 2)
check.expect("St", d1.st, 12)
check.expect("HP", d1.hp, 12)
check.expect("MP", d1.mp, 12)
check.expect("Level", d2.level, 2)
check.expect("St", d2.st, 2)
check.expect("HP", d2.hp, 12)
check.expect("MP", d2.mp, 12)
check.expect("Level", d3.level, 2)
check.expect("St", d3.st, 23)
check.expect("HP", d3.hp, 23)
check.expect("MP", d3.mp, 12)
check.expect("HP", e2.hp, 0)

##Tests
a1 = Character("Aarya", 17, 9, 14)
b1 = Character("Shah", 8, 4, 2)
print(a1)
print(b1)
c1.cast_spell(10, 5, b1)
c1.level_up()
check.expect("Level", a1.level, 1)
check.expect("St", a1.st, 17)
check.expect("HP", a1.hp, 9)
check.expect("MP", a1.mp, 14)
check.expect("HP", b1.hp, 0)
print(a1)  
d1 = Character("C1", 5, 5, 5)
d2 = Character("C2", 1, 15, 10)
d3 = Character("C3", 25, 20, 10)
e2 = Character("E2", 15, 30, 10)
L = [d1, d2, d3]
check.expect("Example 1", all_punch(L, e2), None)
check.expect("Level", d1.level, 2)
check.expect("St", d1.st, 6)
check.expect("HP", d1.hp, 6)
check.expect("MP", d1.mp, 6)
check.expect("Level", d2.level, 2)
check.expect("St", d2.st, 2)
check.expect("HP", d2.hp, 17)
check.expect("MP", d2.mp, 12)
check.expect("Level", d3.level, 2)
check.expect("St", d3.st, 28)
check.expect("HP", d3.hp, 23)
check.expect("MP", d3.mp, 12)
check.expect("HP", e2.hp, 0)
