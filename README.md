# Image-Resizer-Tool
# 🖼️ Image Resizer Tool

## 🚀 Objective
Resize and convert multiple images in batch using Python and Pillow.

## 🛠 Tools & Libraries
- Python 3
- Pillow (`PIL`)

## 📦 Installation
```bash
pip install pillow
import os
from PIL import Image

# === User Settings ===
input_folder = "input_images"      # Folder with original images
output_folder = "output_images"    # Folder for resized images
new_size = (800, 800)              # Desired size (width, height)
output_format = "PNG"              # Format for saved images (e.g., "PNG", "JPEG")

# === Create output folder if not exists ===
os.makedirs(output_folder, exist_ok=True)

# === Process each image ===
for filename in os.listdir(input_folder):
    try:
        file_path = os.path.join(input_folder, filename)

        # Only process files that are images
        if filename.lower().endswith(('.png', '.jpg', '.jpeg', '.bmp', '.gif', '.tiff')):
            with Image.open(file_path) as img:
                resized_img = img.resize(new_size)
                output_name = f"{os.path.splitext(filename)[0]}.{output_format.lower()}"
                output_path = os.path.join(output_folder, output_name)
                resized_img.save(output_path, output_format)
                print(f"✅ {filename} resized & saved as {output_name}")
        else:
            print(f"⚠️ Skipped (not an image): {filename}")

    except Exception as e:
        print(f"❌ Error processing {filename}: {e}")

print("\n🎉 All images processed successfully!")

