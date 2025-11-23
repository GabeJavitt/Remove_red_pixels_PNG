import numpy as np
from PIL import Image

def desaturate_red_blocks_high_quality(input_path, output_path, new_color=(220, 220, 220)):
    # 1. Open image
    img = Image.open(input_path).convert('RGB')
    
    # Capture the original DPI (dots per inch) metadata if it exists
    # This ensures if you print it for a paper, it stays sharp.
    original_dpi = img.info.get('dpi', (300, 300)) 
    
    data = np.array(img)

    # 2. Define Channels
    red_channel = data[:, :, 0]
    green_channel = data[:, :, 1]
    blue_channel = data[:, :, 2]

    # 3. Create Mask (Detect Red)
    # Adjust these thresholds if it's missing pixels
    is_red_pixel = (red_channel > 150) & (green_channel < 100) & (blue_channel < 100)

    # 4. Apply Color
    data[is_red_pixel] = new_color

    # 5. Save with Quality Settings
    new_img = Image.fromarray(data)
    
    # 'optimize=True' reduces file size without losing pixel quality
    # 'dpi=original_dpi' ensures it prints at the same physical size
    new_img.save(output_path, format='PNG', dpi=original_dpi, optimize=True)
    
    print(f"Saved high-quality PNG to: {output_path}")

# --- Usage ---
# Ensure your output filename ends in .png
desaturate_red_blocks_high_quality('input_image.png', 'output_image.png')
