# Random-Username-Generator
import random
import string
adjectives = ["Cool", "Happy", "Brave", "Wild", "Mighty", "Speedy", "Quiet", "Fierce", "Bold", "Silly"]
nouns = ["Tiger", "Dragon", "Panther", "Wizard", "Ninja", "Phoenix", "Lion", "Zebra", "Shark", "Falcon"]
def generate_username(add_numbers=False, add_special_chars=False, username_length=None):
    # Randomly choose an adjective and a noun
    adjective = random.choice(adjectives)
    noun = random.choice(nouns)
    username = adjective + noun
    if add_numbers:
        username += str(random.randint(1, 99)) 
    if add_special_chars:
        special_chars = random.choice(string.punctuation)
        username += special_chars
    if username_length:
        username = username[:username_length]
    return username
def save_usernames_to_file(usernames, filename="usernames.txt"):
    with open(filename, 'w') as file:
        for username in usernames:
            file.write(username + '\n')
    print(f"Usernames saved to {filename}")
def main():
    print("Welcome to the Random Username Generator!")
    add_numbers = input("Would you like to add numbers to the username? (yes/no): ").lower() == "yes"
    add_special_chars = input("Would you like to add special characters to the username? (yes/no): ").lower() == "yes"
    username_length_input = input("Would you like to set a maximum length for the username? (yes/no): ").lower()
    username_length = None
    if username_length_input == "yes":
        username_length = int(input("Enter the maximum length of the username: "))
    num_usernames = int(input("How many usernames would you like to generate?: "))
    generated_usernames = []
    for _ in range(num_usernames):
        username = generate_username(add_numbers, add_special_chars, username_length)
        generated_usernames.append(username)
    print("\nGenerated Usernames:")
    for username in generated_usernames:
        print(username)
    save_to_file = input("\nWould you like to save the usernames to a file? (yes/no): ").lower() == "yes"
    if save_to_file:
        save_usernames_to_file(generated_usernames)
if __name__ == "__main__":
    main()
