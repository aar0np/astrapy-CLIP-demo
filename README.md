# astrapy-CLIP-demo

Uses the Sentence Transformer library to implement the CLIP model to process image files for searching. Underlying vector embeddings and metadata are stored in DataStax Astra DB, which is facilitated via the [astrapy](https://github.com/datastax/astrapy) library.

## Requirements

 - A vector-enabled [Astra DB](https://astra.datastax.com) database
 - An Astra DB application token
 - An Astra DB API endpoint
 - Environment variables defined for: `ASTRA_DB_APPLICATION_TOKEN`, and `ASTRA_DB_API_ENDPOINT`:

```
export ASTRA_DB_APPLICATION_TOKEN=AstraCS:GgsdfSnotrealHqKZw:SDGSDDSG6a36d8526BLAHBLAHBLAHc18d40
export ASTRA_DB_API_ENDPOINT=https://b9aff773-also-not-real-d3088ea14425-us-east1.apps.astra.datastax.com
```

 - A local `images/` directory containing JPEGs or PNGs to embed.
 - Python dependencies: sentence-transformers, astrapy, and matplotlib

```
pip install sentence-transformers
pip install astrapy
pip install matplotlib
```

## Functionality

Descriptions and examples for each script in the project.

### astrapyCLIPLoader.py

 - Creates a new collection named `car_images` using astrapy.
 - Cycles through all files in the `images/` directory.
 - Generates embeddings for each image file.
 - Stores vector embeddings and metadata in Astra DB.

Usage:

```
python3 astrapyCLIPLoader.py
```

### astrapyCLIPSearch.py

 - Takes text input from a terminal window.
 - Generates an embedding from the search text.
 - Runs an approximate nearest neighbor (ANN) vector search with a limit of 1.
 - Displays the (local) image file associated with the result.
 - Quits when the user enters `exit`.

Usage:

```
python3 astrapyCLIPSearch.py
Next search? tesla
Next search? blue tesla
Next search? exit
```
_Image results not shown_

### astrapySearchByImage.py

 - Takes the file location of an image as an argument on the command line.
 - Displays the image and its vector embedding.
 - Runs an approximate nearest neighbor (ANN) vector search with a limit of 1.
 - Displays the (local) image file associated with the result.

Usage:

```
python3 astrapySearchByImage.py ~/Pictures/my_car_w_ladder.jpg
```
_Image and vector results not shown_
