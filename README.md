Deduplication Logic

The goal of this project was to deduplicate a large, semi-structured dataset of product records by consolidating multiple partial entries into a single, enriched record per product. The chosen key for deduplication was the `product_name`, as it offered the most reliable and interpretable representation of a unique product across vendors and platforms.

Each group of duplicate records was processed to extract and preserve **maximum available information**. Instead of discarding duplicates or selecting an arbitrary row, the approach merged values across all 31 attributes using custom logic per field type. For textual fields like `product_title` or `description`, the solution combined distinct, non-null entries to create a more comprehensive summary. Structured fields, such as `color` or `power_rating`, which contained serialized lists or dictionaries, were parsed, flattened, and deduplicated before recombination. Sparse fields (like `eco_friendly` or `energy_efficiency`) were preserved if any useful values existed, while numeric or categorical fields were resolved by choosing the most frequent value across the group. This ensured each product output retained the most informative version of every attribute.

The solution emphasized data preservation, uniqueness, and scalability—key pillars for any production-grade enrichment pipeline.
