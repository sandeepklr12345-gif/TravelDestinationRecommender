# Travel Destination Recommender

A small web application that recommends a destination from a traveler's budget, preferred climate, and preferred place type. The recommendation API uses predefined rules.

## Features

- Choose a low, medium, or high budget.
- Choose a cold, moderate, or hot climate.
- Choose a beach, mountain, historical, or wildlife destination.
- Get a matching destination or a message when no rule matches.

## Tech stack

- Python with FastAPI
- HTML, CSS, and JavaScript

## Project structure

```text
backend/
  main.py                 # FastAPI application and recommendation rules
  data/
    destination_rules.csv # Data file included with the project
frontend/
  index.html              # Browser interface
```

The current API keeps its recommendation rules in `backend/main.py`; it does not load them from the CSV file.

## Run locally

1. Install Python and open a terminal in the project folder.
2. Install the backend packages:

   ```bash
   python -m pip install fastapi uvicorn
   ```

3. Start the API from the `backend` folder:

   ```bash
   cd backend
   python -m uvicorn main:app --reload
   ```

4. Open `frontend/index.html` in a browser. Keep the API running while using the page.

The API documentation is available at [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs).

## API

Send a `POST` request to `http://127.0.0.1:8000/recommend` with JSON such as:

```json
{
  "budget": "low",
  "climate": "hot",
  "place_type": "beach"
}
```

Example response:

```json
{
  "destination": "Goa, India"
}
```

Budget values are `low`, `medium`, and `high`; climate values are `cold`, `moderate`, and `hot`; place types are `beach`, `mountain`, `historical`, and `wildlife`. Only the combinations defined in the backend rules return a destination. Other combinations return a “No match found” message.
