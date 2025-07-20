# SmartTrash API

SmartTrash API is an intelligent waste management platform that enables data collection, analysis, and prediction from connected trash bins. It integrates advanced features such as fill level prediction, notification management, report generation, and collection route optimization.

## Main Features

- **Real-time data collection**: Synchronization with Firebase RTDB to retrieve and store trash bin data.
- **MongoDB storage**: Trash bin data is persisted in a MongoDB database for analysis and history.
- **Advanced predictions**:
  - Fill level prediction (`predictionLvl`)
  - Temperature/humidity prediction (`predictionTH`)
- **Smart notifications**: Sends notifications via Firebase Cloud Messaging when certain thresholds are reached.
- **Route optimization**: Calculates optimal routes for waste collection.
- **Report generation**: Creates PDF and Markdown reports on the status of the trash bin fleet and detected anomalies.
- **RESTful API**: Exposes multiple endpoints for data management, analysis, and consultation.
- **Web interface**: An HTML/JS dashboard to visualize and interact with data.

## Project Structure

- `run.py`: Main entry point for the FastAPI API.
- `routers/`: Contains routes for trash bin management, report generation, and predictions.
- `services/`: Business services (notifications, etc.).
- `others/`: Data models, database access, statistics, etc.
- `predictions/`: Prediction modules (level, temperature/humidity).
- `statics/`: Static files for the web interface (HTML, JS, CSS).
- `utils/`: Utility functions and constants.
- `reports/`: Report generation and advanced analytics.

## Main API Endpoints

- `/`: API home page.
- `/update/{bin_id}`: Updates data for a trash bin.
- `/read/{bin_id}`: Retrieves data for a trash bin.
- `/prediction/ht`: Temperature/humidity predictions.
- `/optimize`: Collection route optimization.
- `/generate-report`: Generates a PDF report.
- `/bin-analytics`: Advanced analytics on trash bins.
- `/api/population-by-bin`: Usage statistics by trash bin.

## Quick Start

1. **Install dependencies**:
   ```sh
   pip install -r requirements.txt
   ```

2. **Configure Firebase**:
   - Create a project on [Firebase Console](https://console.firebase.google.com/).
   - Go to "Project settings" > "Service accounts".
   - Click "Generate new private key" to get the JSON file.
   - Place this file as `firebase_key.json` in the `statics/` folder.
   - Set the database URL in the constants file (`utils/constants.py`).

3. **Start the server**:
   ```sh
   python run.py
   ```
   or
   ```sh
   uvicorn run:app --reload
   ```

4. **Access the web interface**:
   - Open `statics/index.html` in a browser.

## Technologies Used

- Python 3, FastAPI, Uvicorn
- MongoDB, Firebase RTDB & FCM
- Pandas, threading, asyncio
- HTML/JS/CSS for user interface


## Useful Links

- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Firebase Admin Python Documentation](https://firebase.google.com/docs/admin/setup)
- [MongoDB Python Documentation (PyMongo)](https://pymongo.readthedocs.io/en/stable/)
- [Uvicorn](https://www.uvicorn.org/)
- [Pandas](https://pandas.pydata.org/docs/)
- [Firebase Console](https://console.firebase.google.com/)
- [Python Documentation](https://docs.python.org/3/)

---

**SmartTrash**: Optimize urban waste management through data and artificial intelligence!

---