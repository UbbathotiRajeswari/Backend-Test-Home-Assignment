# Backend-Test-Home-Assignment

# Fetch Research Papers from PubMed

This project is a command-line tool to fetch research papers from PubMed based on a user-specified query. It filters papers to include with at least one author affiliated with a pharmaceutical or biotech company.

## Project Organization
- **pubmed_fetcher/**: Module containing functions to fetch and parse PubMed papers.
  - `__init__.py`: Marks the directory as a package.
  - `fetch.py`: Handles API requests to PubMed.
  - `parser.py`: Parses XML responses and extracts relevant information.
- **cli.py**: Command-line script that uses the module.
- **pyproject.toml**: Poetry configuration file for dependency management.
- **README.md**: Documentation file (this file).

## Installation and Setup
1. **Install Poetry** (if not already installed):
   ```sh
   pip install poetry
   ```
2. **Clone the repository**:
   ```sh
   git clone https://github.com/UbbathotiRajeswari(Username)/get-papers-list.git
   cd get-papers-list
   ```
3. **Install dependencies**:
   ```sh
   poetry install
   ```

## Publishing the Module to TestPyPI
To publish the module to TestPyPI:
1. **Build the package**:
   ```sh
   poetry build
   ```
2. **Publish to TestPyPI**:
   ```sh
   poetry publish -r testpypi
   ```

To install from TestPyPI:
```sh
pip install --index-url https://test.pypi.org/simple/ --no-deps pubmed-fetcher
```

## Usage
### Fetch Papers from PubMed
Run the command with a query string:
```sh
poetry run get-papers-list "cancer AND immunotherapy"
```

### Command-Line Options
- `-h, --help`: Display usage instructions.
- `-d, --debug`: Enable debug mode (prints additional logs).
- `-f, --file <filename>`: Specify a CSV filename to save results instead of printing them.

Example:
```sh
poetry run get-papers-list "COVID-19 vaccine" -f results.csv
```

## Dependencies
- `requests`: For making API calls to PubMed.
- `xml.etree.ElementTree`: For parsing XML responses.
- `csv`: For saving results in CSV format.
- `argparse`: For handling command-line arguments.
- `re`: For identifying non-academic authors based on email domains and keywords.

## Tools Used
- **PubMed API**: Fetches research papers.
  - Documentation: [NCBI E-utilities](https://www.ncbi.nlm.nih.gov/books/NBK25499/)
- **Poetry**: Dependency management.
  - Documentation: [Poetry](https://python-poetry.org/)
- **Regular Expressions (re module)**: Used for filtering non-academic authors based on heuristics.
- **GitHub Actions**: For CI/CD automation and testing.

## Identifying Non-Academic Authors
To determine if an author is affiliated with a pharmaceutical or biotech company, the program applies the following heuristics:
- **Email Domain Matching**: If an author's email contains domains like `@pfizer.com`, `@novartis.com`, etc., they are categorized as non-academic.
- **Affiliation Keyword Matching**: If an author's affiliation includes words such as `Inc.`, `Ltd.`, `Pharma`, `Biotech`, `Laboratories`, `Corporation`, etc., they are flagged as non-academic.
- **Exclusion of Academic Terms**: Affiliations containing terms like `University`, `Institute`, `College`, `School of Medicine`, etc., are excluded from non-academic categorization.

## Version Control
- Hosted on GitHub: [GitHub Repository](https://github.com/UbbathotiRajeswari/get-papers-list)
- Use Git for version control:
  ```sh
  git init
  git add .
  git commit -m "Initial commit"
  git branch -M main
  git remote add origin https://github.com/yourusername/get-papers-list.git
  git push -u origin main
  ```

## License
This project is open-source and licensed under the MIT License.
