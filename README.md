# encryptionSim
#    #     #     ###### #    #                 ###### #####  #   #   #
#    #    # #    #      #    #  by             #        #   # # # #  #
######   #####   ###### ######    Kyle Franke  ######   #   #  #  #  #
#    #  #     #       # #    #                      #   #   #     #   
#    # #       # ###### #    #                 ###### ##### #     #  #

import random

def passHash(s):
    gibberish = [".x9d%", "g,e3Kb", "!7cmj,", "&xc|!", "dsgX/&", ";cv|BN+",\
                 "Lcc/;", "n@c|Vo", ")E2@d", "7(AABr"]
    hashed = ''
    for ch in s:
        random.seed(len(s))
        rand = random.randint(0, 9)
        try:
            hashed = hashed + gibberish[rand] + ch
        except:
            hashed = hashed + gibberish[0] + ch
        del gibberish[0]
    print(hashed)

def hashPass(s):
    gibberish = [".x9d%", "g,e3Kb", "!7cmj,", "&xc|!", "dsgX/&", ";cv|BN+",\
                 "Lcc/;", "n@c|Vo", ")E2@d", "7(AABr"]
    for el in gibberish:
        if el in s:
            s = s.replace(el, '')
    print(s)
                
def taskDelegation():
    about = open("about.txt", 'r')
    print("Welcome to Kyle's password encryption simulator!")
    print("\n")
    print("INSTRUCTIONS: press 'a' to input a password and receive its hashed"\
          + " string \nequivalent, press 'b' to input a hashed string and " +\
          "receive its plain text\nequivalent, press 'c' to learn more about "\
          + "this program, or press 'd' to\nexit the program.")
    ui = input("\nWhat'll it be, captain? ")
    while ui.lower() != 'd':
        if ui.lower() == 'a':
            s = input("Please enter the plain text to be converted to hash: ")
            passHash(s)
            ui = input("\nWhat do you want to do next? ")
        elif ui.lower() == 'b':
            s = input("Please enter hashed string to be converted to PT: ")
            hashPass(s)
            ui = input("\nWhat do you want to do next? ")
        elif ui.lower() == 'c':
            print("\n")
            for line in about:
                print(line.rstrip("\n"))
            print("\n")
            ui = input("What do you want to do next? ")
        elif ui.lower() != 'a' or ui.lower() != 'b' or ui.lower() != 'c' or \
           ui.lower() != 'd':
            print("You didn't enter a, b, c, or d. Try again.")
            ui = input("\nWhat do you want to do? ")
    print("\nThanks for using my program.")
    about.close()

def main():
    taskDelegation()

main()
