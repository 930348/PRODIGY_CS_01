def encrypt(text, shift):
    encrypted_text = ""
    for char in text:
        if char.isalpha():
            shifted = ord(char) + shift
            if char.islower():
                if shifted > ord('z'):
                    shifted -= 26
            elif char.isupper():
                if shifted > ord('Z'):
                    shifted -= 26
            encrypted_text += chr(shifted)
        else:
            encrypted_text += char
    return encrypted_text

def decrypt(encrypted_text, shift):
    decrypted_text = ""
    for char in encrypted_text:
        if char.isalpha():
            shifted = ord(char) - shift
            if char.islower():
                if shifted < ord('a'):
                    shifted += 26
            elif char.isupper():
                if shifted < ord('A'):
                    shifted += 26
            decrypted_text += chr(shifted)
        else:
            decrypted_text += char
    return decrypted_text

def main():
    while True:
        choice = input("Do you want to encrypt or decrypt? (e/d): ").lower()
        if choice not in ['e', 'd']:
            print("Invalid choice! Please enter 'e' for encrypt or 'd' for decrypt.")
            continue
        
        text = input("Enter your message: ")
        shift = int(input("Enter the shift value: "))
        
        if choice == 'e':
            encrypted_text = encrypt(text, shift)
            print("Encrypted message:", encrypted_text)
        elif choice == 'd':
            decrypted_text = decrypt(text, shift)
            print("Decrypted message:", decrypted_text)
        
        another = input("Do you want to perform another operation? (y/n): ").lower()
        if another != 'y':
            break

if __name__ == "__main__":
    main()
