import itertools
import string
from concurrent.futures import ThreadPoolExecutor

def generate_combinations(alphabet, length):
    for combination in itertools.product(alphabet, repeat=length):
        yield ''.join(combination)

def save_combinations_to_file(start_length, end_length, alphabet, filename):
    with open(filename, 'a', encoding='utf-8') as file:
        for length in range(start_length, end_length + 1):
            for combination in generate_combinations(alphabet, length):
                file.write(combination + '\n')

alphabet = string.ascii_lowercase + string.digits  # Lowercase letters and digits
max_length = 7
filename = "new_wordlist.txt"

# Clear the file before writing
with open(filename, 'w', encoding='utf-8') as file:
    pass

# Define the ranges for each worker
length_ranges = [(1, 2), (3, 4), (5, 6), (7, 7)]

# Run the workers in parallel
with ThreadPoolExecutor() as executor:
    futures = [executor.submit(save_combinations_to_file, start, end, alphabet, filename) for start, end in length_ranges]

# Wait for all workers to finish
for future in futures:
    future.result()
