
# OrangeLab

<div style="text-align:center">
  <img src="https://img.recraft.ai/wQ0kjs2kMmj5eWcJqeRcP_JMtDZ9DJN2Ma3v5sLdBDI/rs:fit:1024:1024:0/q:80/g:no/plain/abs://prod/images/15803871-d5b3-4b04-bc9e-7659de4894ab@avif" width="100" style="border-radius:15px" />
</div>
<br/>
The Python module developed for the Orange Python Tool Plugin serves a dual purpose, providing functionalities for both image processing using OpenCV and the generation of synthetic datasets through the Faker library.

[GitHub](https://github.com/NagiPragalathan/OrangeLab)
<br/>
<br/>
<br/>

# Fake Dataset Generator Documentation

## Introduction

The `generate_fake_dataset` function is designed to generate a fake dataset based on the provided configuration using the Faker library. This can be useful for testing, development, or generating sample data.

## Function Signature

```python
generate_fake_dataset(num_rows, path="fake_dataset.csv", none_values=True, table_head=None)
```

- `num_rows`: Number of rows to generate in the dataset.
- `path`: The path where the generated dataset will be saved. Default is "fake_dataset.csv".
- `none_values`: Whether to include None values in the generated dataset. Default is `True`.
- `table_head`: A dictionary specifying the columns and their configurations.

## Column Configuration

The `table_head` dictionary defines the columns of the dataset, where each key is the column name, and the value is a dictionary specifying the column configuration. Supported configurations include:

- `type`: Faker provider type (e.g., "name", "email", "passport_gender").
- `dtype`: Data type (e.g., "int").
- `range`: Range of values for integer columns (e.g., "1-100").
- `len`: Length of integer columns.

## Example Usage

```python
import pandas as pd
from faker import Faker

# Define the column configurations
table_head = {
    "name": {"type": "name"},
    "email": {"type": "email"},
    "gender": {"type": "passport_gender"},
    "age": {"dtype": "int", "range": "10-100"},
    "score": {"dtype": "int", "range": "10-100"},
    "time_s": {"dtype": "int", "range": "10-100"},
}

# Generate a fake dataset with 500 rows and save it to a CSV file
generate_fake_dataset(500, "sample.csv", True, table_head)
```

## Supported Faker Providers

The `Faker` library provides a wide range of providers for generating fake data. Some of the supported types include:

```python
Types = [ "aba", "add_provider", "address", "administrative_unit", "am_pm", "android_platform_token", "ascii_company_email", "ascii_email", "ascii_free_email", "ascii_safe_email", "bank_country", "basic_phone_number", "bban", "binary", "boolean", "bothify", "bs", "building_number", "cache_pattern", "catch_phrase", "century", "chrome", "city", "city_prefix", "city_suffix", "color", "color_hsl", "color_hsv", "color_name", "color_rgb", "color_rgb_float", "company", "company_email", "company_suffix", "coordinate", "country", "country_calling_code", "country_code", "credit_card_expire", "credit_card_full", "credit_card_number", "credit_card_provider", "credit_card_security_code", "cryptocurrency", "cryptocurrency_code", "cryptocurrency_name", "csv", "currency", "currency_code", "currency_name", "currency_symbol", "current_country", "current_country_code", "date", "date_between", "date_between_dates", "date_object", "date_of_birth", "date_this_century", "date_this_decade", "date_this_month", "date_this_year", "date_time", "date_time_ad", "date_time_between", "date_time_between_dates", "date_time_this_century", "date_time_this_decade", "date_time_this_month", "date_time_this_year", "day_of_month", "day_of_week", "del_arguments", "dga", "domain_name", "domain_word", "dsv", "ean", "ean13", "ean8", "ein", "email", "emoji", "enum", "factories", "file_extension", "file_name", "file_path", "firefox", "first_name", "first_name_female", "first_name_male", "first_name_nonbinary", "fixed_width", "format", "free_email", "free_email_domain", "future_date", "future_datetime", "generator_attrs", "get_arguments", "get_formatter", "get_providers", "hex_color", "hexify", "hostname", "http_method", "iana_id", "iban", "image", "image_url", "internet_explorer", "invalid_ssn", "ios_platform_token", "ipv4", "ipv4_network_class", "ipv4_private", "ipv4_public", "ipv6", "isbn10", "isbn13", "iso8601", "items", "itin", "job", "json", "json_bytes", "language_code", "language_name", "last_name", "last_name_female", "last_name_male", "last_name_nonbinary", "latitude", "latlng", "lexify", "license_plate", "linux_platform_token", "linux_processor", "local_latlng", "locale", "locales", "localized_ean", "localized_ean13", "localized_ean8", "location_on_land", "longitude", "mac_address", "mac_platform_token", "mac_processor", "md5", "military_apo", "military_dpo", "military_ship", "military_state", "mime_type", "month", "month_name", "msisdn", "name", "name_female", "name_male", "name_nonbinary", "nic_handle", "nic_handles", "null_boolean", "numerify", "opera", "optional", "paragraph", "paragraphs", "parse", "passport_dates", "passport_dob", "passport_full", "passport_gender", "passport_number", "passport_owner", "password", "past_date", "past_datetime", "phone_number", "port_number", "postalcode", "postalcode_in_state", "postalcode_plus4", "postcode", "postcode_in_state", "prefix", "prefix_female", "prefix_male", "prefix_nonbinary", "pricetag", "profile", "provider", "providers", "psv", "pybool", "pydecimal", "pydict", "pyfloat", "pyint", "pyiterable", "pylist", "pyobject", "pyset", "pystr", "pystr_format", "pystruct", "pytimezone", "pytuple", "random", "random_choices", "random_digit", "random_digit_above_two", "random_digit_not_null", "random_digit_not_null_or_empty", "random_digit_or_empty", "random_element", "random_elements", "random_int", "random_letter", "random_letters", "random_lowercase_letter", "random_number", "random_sample", "random_uppercase_letter", "randomize_nb_elements", "rgb_color", "rgb_css_color", "ripe_id", "safari", "safe_color_name", "safe_domain_name", "safe_email", "safe_hex_color", "sbn9", "secondary_address", "seed", "seed_instance", "seed_locale", "sentence", "sentences", "set_arguments", "set_formatter", "sha1", "sha256", "simple_profile", "slug", "ssn", "state", "state_abbr", "street_address", "street_name", "street_suffix", "suffix", "suffix_female", "suffix_male", "suffix_nonbinary", "swift", "swift11", "swift8", "tar", "text", "texts", "time", "time_delta", "time_object", "time_series", "timezone", "tld", "tsv", "unique", "unix_device", "unix_partition", "unix_time", "upc_a", "upc_e", "uri", "uri_extension", "uri_page", "uri_path", "url", "user_agent", "user_name", "uuid4", "vin", "weights", "windows_platform_token", "word", "words", "xml", "year", "zip", "zipcode", "zipcode_in_state", "zipcode_plus4"]
```

Also you can use `supported_types()` function to find the supported types.

For a complete list of supported providers, refer to the `Faker` documentation or use the `Faker.providers` module to explore available options.

# OCR Installation and Tesseract Path Finder

## Introduction

The provided Python script includes functions to install an OCR (Optical Character Recognition) tool from an installer executable and to find the path to the Tesseract OCR executable on the system.

## Functions

### 1. `install_ocr()`

This function installs an OCR tool using an installer executable. The installer file should be specified as `ocr.exe`. The function retrieves the current script's path, combines it with the installer filename to create the full installer path, and then attempts to run the installer using `subprocess.run()`.

#### Example Usage:

```python
# Example: Install OCR
install_ocr()
```

### 2. `find_tesseract()`

This function attempts to find the path to the Tesseract OCR executable. It first checks if Tesseract is installed in a specific path (`C:\Program Files\Tesseract-OCR\tesseract.exe`). If not found, it then tries to locate Tesseract in the system's PATH using `shutil.which("tesseract")`.

#### Example Usage:

```python
# Example: Find Tesseract Path
tesseract_path = find_tesseract()

if tesseract_path:
    print(f"Tesseract found at: {tesseract_path}")
else:
    print("Tesseract not found.")
```

## Important Note

- Ensure that the installer file (`ocr.exe`) is in the same directory as the script or provide the correct path to the installer in the `install_ocr()` function.
- For `find_tesseract()`, if Tesseract is not found in the specified path or in the system's PATH, it will return `None`.

## Recommendations

- Before using `install_ocr()`, verify that the installer file is compatible with your system.
- Make sure to have the necessary permissions to install software on the system.
- If you are installing from a source other than PyPI, ensure that it is trusted or has been verified by an individual who knows what they

# Image Processing and OCR Functions Documentation

The provided Python script includes various functions for image processing using OpenCV and image-to-text extraction using Tesseract OCR. Below is the documentation for each function along with example usages.

## Image Processing Functions

### 1. `read_image(image_path)`

Read an image from the specified path using OpenCV.

#### Example Usage:

```python
image = read_image('path/to/image.jpg')
```

### 2. `display_image(img, title='Image')`

Display the image using Matplotlib.

#### Example Usage:

```python
display_image(image, title='Original Image')
```

### 3. `convert_to_grayscale(img)`

Convert the image to grayscale.

#### Example Usage:

```python
gray_image = convert_to_grayscale(image)
```

### 4. `apply_blur(img, kernel_size=(5, 5))`

Apply Gaussian blur to the image.

#### Example Usage:

```python
blurred_image = apply_blur(image, kernel_size=(9, 9))
```

### 5. `edge_detection(img, low_threshold=50, high_threshold=150)`

Apply Canny edge detection to the image.

#### Example Usage:

```python
edges = edge_detection(gray_image, low_threshold=30, high_threshold=100)
```

### 6. `resize_image(img, new_size=(300, 300))`

Resize the image to the specified dimensions.

#### Example Usage:

```python
resized_image = resize_image(image, new_size=(500, 500))
```

### 7. `adjust_brightness_contrast(img, alpha=1.5, beta=30)`

Adjust the brightness and contrast of the image.

#### Example Usage:

```python
adjusted_image = adjust_brightness_contrast(image, alpha=2.0, beta=50)
```

### 8. `apply_threshold(img, threshold_value=128, max_value=255, threshold_type=cv2.THRESH_BINARY)`

Apply a binary threshold to the image.

#### Example Usage:

```python
thresholded_image = apply_threshold(gray_image, threshold_value=100, max_value=255, threshold_type=cv2.THRESH_BINARY)
```

### 9. `apply_dilation(img, kernel_size=(5, 5))`

Apply dilation to the image.

#### Example Usage:

```python
dilated_image = apply_dilation(thresholded_image, kernel_size=(3, 3))
```

### 10. `change_image_color(img, channel, value)`

Change the intensity of a specific color channel.

#### Example Usage:

```python
modified_image = change_image_color(image, channel=2, value=50)
```

### 11. `find_and_draw_contours(img)`

Find contours in the image and draw them.

#### Example Usage:

```python
contour_image = find_and_draw_contours(thresholded_image)
```

### 12. `most_used_color(img)`

Find the most used color in the image.

#### Example Usage:

```python
most_used_color_value = most_used_color(image)
```

### 13. `image_details(img)`

Get details about the image, including dimensions and pixel values.

#### Example Usage:

```python
details = image_details(image)
```

### 14. `image_to_ascii(img, scale_factor=0.1)`

Convert the image to ASCII art.

#### Example Usage:

```python
ascii_art = image_to_ascii(image, scale_factor=0.05)
print(ascii_art)
```

## OCR Function

### 15. `extract_text_from_image(image_path, tesseract_path)`

Extract text from an image using Tesseract OCR.

#### Example Usage:

```python
text = extract_text_from_image('path/to/image.png', 'path/to/tesseract.exe')
print(text)
```

**Note**: Ensure that Tesseract is installed and provide the correct path to the Tesseract executable in the `extract_text_from_image` function you can use install_ocr() for ocr installation.

The following are additional image processing functions that enhance the capabilities of the provided script. These functions can be used in combination with the existing ones to perform a wider range of image manipulations.

### 16. `rotate_image(img, angle)`

Rotate the image by a specified angle.

#### Function Signature:

```python
rotate_image(img, angle)
```

#### Parameters:

- `img`: The input image.
- `angle`: The angle by which to rotate the image.

#### Example Usage:

```python
rotated_image = rotate_image(image, angle=45)
```

### 17. `apply_mask(img, mask)`

Apply a binary mask to the image.

#### Function Signature:

```python
apply_mask(img, mask)
```

#### Parameters:

- `img`: The input image.
- `mask`: Binary mask with the same dimensions as the image.

#### Example Usage:

```python
# Assuming 'mask' is a binary mask with the same dimensions as the image
masked_image = apply_mask(image, mask)
```

### 18. `invert_image(img)`

Invert the colors of the image.

#### Function Signature:

```python
invert_image(img)
```

#### Parameters:

- `img`: The input image.

#### Example Usage:

```python
inverted_image = invert_image(image)
```

### 19. `add_noise(img, intensity=50)`

Add random noise to the image.

#### Function Signature:

```python
add_noise(img, intensity=50)
```

#### Parameters:

- `img`: The input image.
- `intensity`: Intensity of the noise.

#### Example Usage:

```python
noisy_image = add_noise(image, intensity=30)
```

### 20. `morphological_operations(img, operation='dilate', kernel_size=(5, 5))`

Apply morphological operations (dilation or erosion) to the image.

#### Function Signature:

```python
morphological_operations(img, operation='dilate', kernel_size=(5, 5))
```

#### Parameters:

- `img`: The input image.
- `operation`: Operation to perform ('dilate' or 'erode').
- `kernel_size`: Size of the kernel for the operation.

#### Example Usage:

```python
# Dilate the image
dilated_image = morphological_operations(image, operation='dilate', kernel_size=(3, 3))

# Erode the image
eroded_image = morphological_operations(image, operation='erode', kernel_size=(3, 3))
```
