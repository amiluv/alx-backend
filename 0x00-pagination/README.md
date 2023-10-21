This project contains tasks for learning to paginate data.

## Tasks To Complete

- [x] 0. **Simple helper function**
     [0-simple_helper_function.py](0-simple_helper_function.py) contains a Python function named `index_range` that takes two integer arguments `page` and `page_size` and meets the following requirements:

  - The function should return a tuple of size two containing a start index and an end index corresponding to the range of indexes to return in a list for those particular pagination parameters.
  - Page numbers are 1-indexed, i.e. the first page is page 1.

- [x] 1. **Simple pagination**
     [1-simple_pagination.py](1-simple_pagination.py) contains a Python script that meets the following requirements:

  - Copy `index_range` from the previous task and the following class into your code.
  - Implement a method named `get_page` that takes two integer arguments `page` with default value 1 and `page_size` with default value 10.
    - You have to use this [CSV file](Popular_Baby_Names.csv).
    - Use `assert` to verify that both arguments are integers greater than 0.
    - Use `index_range` to find the correct indexes to paginate the dataset correctly and return the appropriate page of the dataset (i.e. the correct list of rows).
    - If the input arguments are out of range for the dataset, an empty list should be returned.

- [x] 2. **Hypermedia pagination**
     [2-hypermedia_pagination.py] contains a Python script that meets the following requirements:

  - Replicate code from the previous task.
  - Implement a `get_hyper` method that takes the same arguments (and defaults) as `get_page` and returns a dictionary containing the following key-value pairs:
    - `page_size`: the length of the returned dataset page.
    - `page`: the current page number.
    - `data`: the dataset page (equivalent to the return value from previous task).
    - `next_page`: number of the next page, `None` if no next page.
    - `prev_page`: number of the previous page, `None` if no previous page.
    - `total_pages`: the total number of pages in the dataset as an integer.
  - Make sure to reuse get_page in your implementation.
  - You can use the `math` module if necessary.

- [x] 3. **Deletion-resilient hypermedia pagination**
     [3-hypermedia_del_pagination.py](3-hypermedia_del_pagination.py) contains a Python script that meets the following requirements:
  - The user does not miss items from dataset when changing page if between two queries, certain rows are removed from the dataset.
  - Start [3-hypermedia_del_pagination.py] with the python code as specified in the file 3-hypermedia_del_pagination.py
  - Implement a `get_hyper_index` method with two integer arguments: `index` with a `None` default value and `page_size` with default value of 10.
    - The method should return a dictionary with the following key-value pairs:
    - `index`: the current start index of the return page. That is the index of the first item in the current page. For example if requesting page 3 with `page_size` 20, and no data was removed from the dataset, the current index should be 60.
    - `next_index`: the next index to query with. That should be the index of the first item after the last item on the current page.
    - `page_size`: the current page size.
    - `data`: the actual page of the dataset.
  - Use `assert` to verify that `index` is in a valid range.
  - If the user queries index 0, `page_size` 10, they will get rows indexed 0 to 9 included.
  - If they request the next index (10) with `page_size` 10, but rows 3, 6 and 7 were deleted, the user should still receive rows indexed 10 to 19 included.
