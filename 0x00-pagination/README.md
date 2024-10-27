# 0x00. Pagination

## Resources
- **Read or Watch**
  - REST API Design: Pagination
  - HATEOAS

## Learning Objectives
At the end of this project, you are expected to be able to explain to anyone, without the help of Google:
- How to paginate a dataset with simple page and page_size parameters.
- How to paginate a dataset with hypermedia metadata.
- How to paginate in a deletion-resilient manner.

## Requirements
- All your files will be interpreted/compiled on Ubuntu 18.04 LTS using Python 3 (version 3.7).
- All your files should end with a new line.
- The first line of all your files should be exactly `#!/usr/bin/env python3`.
- A `README.md` file at the root of the project folder is mandatory.
- Your code should use the `pycodestyle` style (version 2.5.*).
- The length of your files will be tested using `wc`.
- All your modules should have documentation (e.g., `python3 -c 'print(__import__("my_module").__doc__)'`).
- All your functions should have documentation (e.g., `python3 -c 'print(__import__("my_module").my_function.__doc__)'`).
- Documentation is not just a simple word; it’s a real sentence explaining the purpose of the module, class, or method (the length of it will be verified).
- All your functions and coroutines must be type-annotated.

## Setup
**Data File:** `Popular_Baby_Names.csv`

## Tasks

### 0. Simple Helper Function
**Mandatory**

Write a function named `index_range` that takes two integer arguments, `page` and `page_size`. The function should return a tuple of size two containing a start index and an end index corresponding to the range of indexes to return in a list for those particular pagination parameters. Page numbers are 1-indexed (i.e., the first page is page 1).

### 1. Simple Pagination
**Mandatory**

Copy `index_range` from the previous task and the following class into your code. Implement a method named `get_page` that takes two integer arguments: `page` (default value 1) and `page_size` (default value 10).

Use `assert` to verify that both arguments are integers greater than 0. Use `index_range` to find the correct indexes to paginate the dataset correctly and return the appropriate page of the dataset. If the input arguments are out of range for the dataset, an empty list should be returned.

### 2. Hypermedia Pagination
**Mandatory**

Replicate code from the previous task. Implement a `get_hyper` method that takes the same arguments (and defaults) as `get_page` and returns a dictionary containing the following key-value pairs:
- `page_size`: the length of the returned dataset page
- `page`: the current page number
- `data`: the dataset page (equivalent to the return from the previous task)
- `next_page`: number of the next page, or None if no next page
- `prev_page`: number of the previous page, or None if no previous page
- `total_pages`: the total number of pages in the dataset as an integer

Ensure to reuse `get_page` in your implementation.

### 3. Deletion-Resilient Hypermedia Pagination
**Mandatory**

Implement a method named `get_hyper_index` with two integer arguments: `index` (default value None) and `page_size` (default value of 10). The method should return a dictionary with the following key-value pairs:
- `index`: the current start index of the return page (the index of the first item in the current page).
- `next_index`: the next index to query with (the index of the first item after the last item on the current page).
- `page_size`: the current page size.
- `data`: the actual page of the dataset.

## Summary

This implementation provides a robust structure for paginating datasets in Python. Each method adheres to the requirements specified in your project brief:

- **Simple Helper Function** calculates indices based on parameters.
- **Simple Pagination** retrieves a specific slice of data.
- **Hypermedia Pagination** enriches responses with navigation metadata.
- **Deletion-Resilient Hypermedia Pagination** maintains consistency in response even when items are removed from the dataset.


