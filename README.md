Here's a simple image encryption tool using Python and the Pillow library:


from PIL import Image

def encrypt_image(image_path, output_path, operation):
    image = Image.open(image_path)
    pixels = image.load()

    for x in range(image.width):
        for y in range(image.height):
            r, g, b = pixels[x, y]

            if operation == 'swap':
                pixels[x, y] = (b, g, r)
            elif operation == 'add_10':
                pixels[x, y] = ((r + 10) % 256, (g + 10) % 256, (b + 10) % 256)
            elif operation == 'multiply_2':
                pixels[x, y] = ((r * 2) % 256, (g * 2) % 256, (b * 2) % 256)

    image.save(output_path)

def decrypt_image(image_path, output_path, operation):
    image = Image.open(image_path)
    pixels = image.load()

    for x in range(image.width):
        for y in range(image.height):
            r, g, b = pixels[x, y]

            if operation == 'swap':
                pixels[x, y] = (b, g, r)
            elif operation == 'add_10':
                pixels[x, y] = ((r - 10) % 256, (g - 10) % 256, (b - 10) % 256)
            elif operation == 'multiply_2':
                pixels[x, y] = ((r // 2) % 256, (g // 2) % 256, (b // 2) % 256)

    image.save(output_path)

def main():
    while True:
        print("\nImage Encryption Tool")
        print("1. Encrypt Image")
        print("2. Decrypt Image")
        print("3. Quit")
        choice = input("Choose an option: ")

        if choice == "1":
            image_path = input("Enter the image path: ")
            output_path = input("Enter the output path: ")
            operation = input("Enter the operation (swap, add_10, multiply_2): ")
            encrypt_image(image_path, output_path, operation)
            print("Image encrypted successfully!")

        elif choice == "2":
            image_path = input("Enter the image path: ")
            output_path = input("Enter the output path: ")
            operation = input("Enter the operation (swap, add_10, multiply_2): ")
            decrypt_image(image_path, output_path, operation)
            print("Image decrypted successfully!")

        elif choice == "3":
            break

        else:
            print("Invalid option. Please choose a valid option.")

if __name__ == "__main__":
    main()
