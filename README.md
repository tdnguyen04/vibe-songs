# 🎵 Vibe Mapper (Backend)
Vibe Mapper is a tool that analyzes your Spotify playlist and visualizes it as a 3D galaxy based on `energy` and `valence` (happiness) of the song

## Prerequisites
Before you start, make sure you have these information
1. **Spotify:** Create an app at the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard) to get your `Client ID` and `Client Secret`.
2. **Last.fm:** Create an API account at [Last.fm API](https://www.last.fm/api/account/create) to get your `API Key`.

## Installation
1. Clone the repository to your local development area
    ```bash
    git clone https://github.com/tdnguyen04/vibe-mapper.git
    ```

2. Set up the Environment
    ```bash
    cp .env.example .env
    ```

3. Create a Virtual Environment (Recommended)

    It's best to isolate dependencies so they don't clash with your system.
   
    **Windows:**
    ```bash
    python -m venv venv
    .\venv\Scripts\activate
    ```

    **Mac/Linux**
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

4. Install dependencies
    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. Fetch Songs: Connects to Spotify and downloads your Liked Songs
    ``` bash
    python3 extract.py
    # Output: my_raw_songs.json
    ```
2. Analyze Vibes: Queries Last.fm to determine the energy/valence of each song.
    ```bash
    python3 refine.py
    # Output: my_refined_songs.json
    ```

## How it works
We use Spotify for the list, but since Audio features API is deprecated since November 2024, we use custom "data imputation strategy": we fetch crowd-sourced tags from Last.fm (e.g., "Death Metal", "Chillhop") and map them to numerical Vibe coordinates.