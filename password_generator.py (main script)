import secrets
import string


def generate_password(length=12, use_uppercase=True, use_numbers=True, use_symbols=True):
    """
    Generate a strong random password with customizable complexity.

    Parameters:
    - length: Length of the password (default: 12)
    - use_uppercase: Include uppercase letters (default: True)
    - use_numbers: Include numbers (default: True)
    - use_symbols: Include symbols (default: True)

    Returns:
    - A strong random password
    """

    # Define character sets
    lowercase = string.ascii_lowercase
    uppercase = string.ascii_uppercase if use_uppercase else ''
    digits = string.digits if use_numbers else ''
    symbols = '!@#$%^&*()_+-=[]{}|;:,.<>?' if use_symbols else ''

    # Combine all allowed characters
    all_chars = lowercase + uppercase + digits + symbols

    # Verify at least one character set is selected
    if not all_chars:
        raise ValueError("At least one character set must be selected")

    # Generate password ensuring at least one character from each selected set
    password = []

    # Ensure at least one lowercase
    password.append(secrets.choice(lowercase))

    # Ensure at least one from other selected sets
    if use_uppercase:
        password.append(secrets.choice(uppercase))
    if use_numbers:
        password.append(secrets.choice(digits))
    if use_symbols:
        password.append(secrets.choice(symbols))

    # Fill the rest with random choices from all allowed characters
    for _ in range(length - len(password)):
        password.append(secrets.choice(all_chars))

    # Shuffle the list to avoid predictable patterns
    secrets.SystemRandom().shuffle(password)

    # Convert list to string
    return ''.join(password)


def get_user_preferences():
    """Get password generation preferences from user input."""
    try:
        length = int(input("Enter password length (8-64): "))
        length = max(8, min(64, length))  # Enforce reasonable bounds

        uppercase = input("Include uppercase letters? (y/n): ").lower() == 'y'
        numbers = input("Include numbers? (y/n): ").lower() == 'y'
        symbols = input("Include symbols? (y/n): ").lower() == 'y'

        return length, uppercase, numbers, symbols
    except ValueError:
        print("Invalid input. Using default settings.")
        return 12, True, True, True


def main():
    print("=== Secure Password Generator ===")
    print("This tool creates strong, random passwords for enhanced security.\n")

    # Get user preferences
    length, uppercase, numbers, symbols = get_user_preferences()

    # Generate and display password
    try:
        password = generate_password(length, uppercase, numbers, symbols)
        print("\nGenerated Password:", password)

        # Calculate possible combinations (entropy measurement)
        char_set_size = 26  # lowercase
        if uppercase: char_set_size += 26
        if numbers: char_set_size += 10
        if symbols: char_set_size += 20  # approx symbol count

        combinations = char_set_size ** length
        print(f"\nPassword Strength:")
        print(f"- Length: {length} characters")
        print(f"- Character set size: {char_set_size} possible characters")
        print(f"- Possible combinations: {combinations:,}")

        # Basic strength assessment
        if length >= 16 and uppercase and numbers and symbols:
            print("- Rating: Excellent")
        elif length >= 12 and (uppercase or numbers or symbols):
            print("- Rating: Good")
        else:
            print("- Rating: Fair (consider increasing length or complexity)")

        print("\nNote: Always store passwords securely using a password manager.")
    except ValueError as e:
        print(f"Error: {e}")


if __name__ == "__main__":
    main()
