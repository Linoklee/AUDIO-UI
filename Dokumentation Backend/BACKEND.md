The backend will provide hearing-curve data to the Vue frontend, store evaluators’ ratings, and return statistics for comparing imputation methods.

Technology Stack

FastAPI for the REST API.
SQLAlchemy for database access and PostgreSQL for storing curves, imputation results, and ratings.
uv for managing Python dependencies.
Pytest for backend unit and integration tests.
Docker Compose to run the frontend, backend, and database together. The team’s CI pipeline will run automated tests.

Backend Responsibilities

Hearing-curve data: Import the supplied dataset into PostgreSQL. Link each original curve to its imputed versions and record which method produced each version. Store metrics such as R^2, RMSE, and high-frequency slope where available.
Curve selection and display: Return the configured number and types of curves for an evaluation. Provide the curve version ID and data points as JSON so the frontend can draw each curve.
Ratings: Receive the curve version ID and rating from the frontend, validate the rating against the agreed Likert scale, and save it to PostgreSQL.                                                                     
Statistics: Aggregate ratings by imputation method and return the rating counts and distributions for the frontend comparison view.
Testing and integration: Test that the API returns the correct curve data, saves valid ratings, rejects invalid ratings, and includes saved ratings in the statistics. Work with Kenzo on the browser end-to-end test.