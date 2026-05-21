This repository contains sample Apache Parquet files of the Medical Hindi Image Dataset. The dataset includes sample medical images stored in compressed binary format for efficient machine learning workflows, computer vision research, dataset evaluation, and AI model development.

Convert Parquet Back to Images

# Requirements

Install dependencies:

```bash
pip install pandas pyarrow pillow
```

Use the following Python script to extract images from the Parquet dataset.
```python
import os
import io
import pandas as pd
from PIL import Image

PARQUET_FILE = r"FILE_PATH"

OUTPUT_FOLDER = r"OUTPUT_FOLDER_PATH"

os.makedirs(OUTPUT_FOLDER, exist_ok=True)

print("Reading Parquet File...\n")

df = pd.read_parquet(PARQUET_FILE)

print("Total Images Found:", len(df))

for index, row in df.iterrows():

    try:

        image_bytes = row["image"]

        file_name = row["file_name"]

        image = Image.open(
            io.BytesIO(image_bytes)
        )

        output_path = os.path.join(
            OUTPUT_FOLDER,
            file_name
        )

        image.save(output_path)

        print("Extracted:", file_name)

    except Exception as e:

        print("Error:", e)

print("\nCompleted")
print("Extracted Images Saved In:")
print(OUTPUT_FOLDER)
```


# Considerations

These Parquet files contain a sample of the complete dataset corpus and are provided for preview, evaluation, testing, and research purposes. The files are optimized in the Apache Parquet format for efficient storage and fast loading.

Please note that the uploaded files do not represent the full dataset collection. They include only a limited portion of the overall corpus intended to demonstrate the dataset structure, schema, and content quality.

For access to the full dataset, custom data delivery, commercial usage, or enterprise licensing options, please visit [InfoBay AI](https://infobay.ai/) or contact us directly for further information.

    -Ph: (91) 8303174762
    -Email: datareq@infobay.ai
