# GameFinder

**GameFinder** is a game recommendation system that helps users discover new titles. It processes a large dataset of game information offline to identify similarities, then presents personalized recommendations through a user-friendly web interface.

---

## How It Works

GameFinder operates in two main phases:

1.  **Data & Model Generation (Offline - Python):**

    -   A Python script connects to the **IGDB API** to fetch a large dataset of popular video games (including name, genres, keywords, summary, and cover art).
    -   This data is cleaned and transformed using **Pandas** and vectorized (e.g., **One-Hot Encoding**).
    -   **Cosine similarity** (from **Scikit-learn**) is calculated between all games to find resemblances.
    -   Finally, a **JSON file (`web/recommendations.json`)** is generated, mapping each game to its most similar counterparts.

2.  **Web Interface (Online - Frontend):**
    -   The web application (**HTML, CSS, and vanilla JavaScript**) is served statically (e.g., by opening `web/index.html` in a browser).
    -   The JavaScript loads the pre-generated `recommendations.json` file.
    -   When a user selects a game, the interface dynamically retrieves and displays its recommendations.

---

## Getting Started

Follow these steps to set up and run GameFinder locally:

### Prerequisites

-   **Python 3.x**
-   **Git**
-   **Twitch Developer Account:** Required for IGDB API access (obtain your `Client ID` and `Client Secret` [here](https://dev.twitch.tv/console/apps)).

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/GameFinder.git](https://github.com/YOUR_USERNAME/GameFinder.git)
    cd GameFinder
    ```
2.  **Set up Python environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: `venv\Scripts\activate`
    pip install -r requirements.txt # Requires `requests`, `pandas`, `scikit-learn` in your requirements.txt
    ```

### Data & Model Generation

1.  **Configure IGDB Credentials:**

    -   Open `scripts/igdb_extractor.py`.
    -   Replace `CLIENT_ID` and `CLIENT_SECRET` placeholders with your actual Twitch API credentials.
    -   **Important:** Keep your `CLIENT_SECRET` confidential. Do not share it publicly.

2.  **Extract Data & Generate Recommendations:**
    ```bash
    python scripts/igdb_extractor.py  # Fetches data and saves to data/popular_games_data.csv
    python scripts/recommender_model.py # Loads data, calculates similarity, generates web/recommendations.json
    ```

### Running the Web Interface

1.  **Open `index.html`:**
    -   Navigate to the `web/` directory.
    -   Open `index.html` in your web browser (e.g., `file:///path/to/GameFinder/web/index.html`).

---

## Author

-   [Your Name/GitHub Username] - [Link to your GitHub profile (Optional)]
