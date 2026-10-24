# Bias_Bounty_explore_Challenge
Notebook Overview: Working with Overture Extracts

This notebook demonstrates how to interactively access, query, and visualize geographic datasets hosted on a public AWS S3 bucket for the Bias Bounties @ Scale challenge. The primary layers include Overture Maps data (buildings, roads, rail, infrastructure, POIs) and US Census ACS housing tract data across four specific regions (maricopa-az, northern-ca, eastern-ok, south-central-tx).

Key Capabilities Covered:
Cloud-Native Data Access: Opening remote Parquet files using DuckDB (via HTTPS and the httpfs/spatial extensions) and GeoPandas (via S3FileSystem using anonymous access) without downloading full datasets locally.
Handling Nested Schemas: Working with complex, nested Overture data types (such as struct and list attributes like names, categories, and sources) using DuckDB dot-access and Pandas/Arrow-backed accessors.
Interactive Map Interface: A custom IPywidgets + Lonboard map dashboard that dynamically streams only the features within your current viewport from the S3 bucket. It also features a geocoding search bar (powered by Photon) and an interactive bounding-box tool that auto-generates copy-pasteable DuckDB/Lonboard Python snippets.
System & Software Requirements
To run the notebook successfully, you need Python >= 3.12 and the specific locked library versions defined in the script metadata:

duckdb==1.5.4: For performing SQL queries on remote Parquet files.
geopandas==1.1.4 & pyarrow==24.0.0: For vector spatial data manipulation and IO.
lonboard==0.16.0: A high-performance Python library for rendering large spatial datasets on interactive maps in Jupyter/Colab notebooks.
geoarrow-rust-io==0.6.1 & arro3-core==0.8.1: For fast, native Arrow-based geometry conversions.
obstore==0.11.0: Used to stream metadata and query the remote object storage efficiently.
ipywidgets==8.1.8: Drives the interactive controls, dropdowns, and status layout.
Note: On Google Colab, the environment setup is handled programmatically in cell 0d0ac722 using uv to speed up the installation of these pinned dependencies.
