# PRODIGY-CS-02
mage Encryption &amp; Decryption Tool using Pixel Manipulation in Python Image Encryption &amp; Decryption Tool using Pixel Manipulation in Python
from PIL import Image
import sys

def xor_encrypt_decrypt(image_path, key, output_path):
    # Open the image
    img = Image.open(image_path)
    pixels = img.load()

    # Process each pixel
    for i in range(img.width):
        for j in range(img.height):
            r, g, b = pixels[i, j]

            # XOR each channel with the key
            r_enc = r ^ key
            g_enc = g ^ key
            b_enc = b ^ key

            pixels[i, j] = (r_enc, g_enc, b_enc)

    # Save the encrypted/decrypted image
    img.save(output_path)
    print(f"Processed image saved as {output_path}")

if __name__ == "__main__":
    if len(sys.argv) != 4:
        print("Usage: python encrypt_decrypt.py <input_image> <key(int)> <output_image>")
        sys.exit(1)

    input_image = sys.argv[1]
    key = int(sys.argv[2])
    output_image = sys.argv[3]

    xor_encrypt_decrypt(input_image, key, output_image)
