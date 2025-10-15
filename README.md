# Backlog Breaker

A Python tool that automatically extracts game names from your Windows shortcuts and retrieves completion time statistics from HowLongToBeat.com, helping you estimate how long it will take to complete games in your library.

## Why I Built This

I built this tool because my game library had grown overwhelming. Every Steam sale, every "must-play" recommendation added another game to the pile. I found myself buying games faster than I could play them, always worried I was missing out on something great while other games collected digital dust.

My hope is that this helps you rediscover the joy in your game library. Stop feeling guilty about unplayed games. Stop buying more when you haven't finished what you have. Start playing with intention.

## Features

- 📁 **Automatic Game Detection**: Scans a folder for game shortcuts (.lnk and .url files)
- 🎮 **HowLongToBeat Integration**: Fetches accurate completion time data for each game
- 📊 **Multiple Completion Metrics**: Tracks Main Story, Main + Extra, Completionist, and All Styles times
- 🎯 **Smart Matching**: Filters out DLC entries and matches the best full game result
- 📈 **Excel Export**: Outputs all data to a formatted Excel file for easy analysis
- 🔍 **Year Identification**: Includes release year for each game to ensure accurate matches

## Installation

### Prerequisites

- Python 3.7 or higher
- pip package manager

### Dependencies

Install the required Python packages:

```bash
pip install howlongtobeatpy pandas
```

## Usage

### Step 1: Configure Paths

Open `HLTB Games.ipynb` and update the following paths in the first cell:

```python
folder_path = r"Path\To\Your\Shortcuts\Folder"  # Your game shortcuts folder
output_file_path = r"Shortcuts.csv"             # Temporary CSV file path
```

### Step 2: Run the Notebook

Execute the notebook cells in order:

1. **Cell 1**: Extracts shortcut names from your folder and creates a CSV file
2. **Cell 2**: Queries HowLongToBeat.com and generates an Excel file with completion times

### Step 3: View Results

The final output will be saved as `modified_file.xlsx` containing:

| Column | Description |
|--------|-------------|
| GameName | Official game title from HowLongToBeat |
| ReleaseYear | Game's release year |
| MainStory | Hours to complete main story |
| MainExtra | Hours for main story + extras |
| Completionist | Hours to 100% complete |
| AllStyles | Average across all play styles |

## Example Output

```
Search results for 'The Witness 2016': 17.17,24.46,39.74,22.85
Search results for 'Stray 2022': 5.1,6.49,10.1,6.36
Search results for 'Cuphead 2017': 10.44,15.88,26.05,15.22
```

## How It Works

1. **Shortcut Extraction**: Scans the specified folder for `.lnk` and `.url` files, extracting the base filename as the game name
2. **API Query**: Uses the `howlongtobeatpy` library to search HowLongToBeat's database
3. **Smart Filtering**: Removes DLC entries and selects the best match based on similarity score
4. **Data Compilation**: Aggregates completion times and metadata into a structured format
5. **Excel Export**: Saves the final dataset for easy viewing and analysis

## Use Cases

- 📚 **Backlog Planning**: Estimate how long it will take to clear your game backlog
- ⏱️ **Time Management**: Choose games based on available time
- 📊 **Library Analysis**: Get insights into your game collection
- 🎯 **Goal Setting**: Plan completionist runs or speedruns

## Troubleshooting

**No results found for a game:**
- Check if the shortcut name closely matches the official game title
- Try manually editing the CSV after Cell 1 to fix game names
- Some games may not be in the HowLongToBeat database

## License

This project is open source and available under the MIT License.

## Acknowledgments

- [HowLongToBeat.com](https://howlongtobeat.com/) for providing game completion time data
- [howlongtobeatpy](https://github.com/ScrappyCocco/HowLongToBeat-PythonAPI) library for API access