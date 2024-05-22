# Loan-Calculator

This is a Flask-based loan calculator application that allows multiple users to manage loans. The application provides various functionalities such as adding users, adding loans, calculating total money borrowed, calculating the average income of users, determining the highest earning month for the company, and predicting future income using regression analysis.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Database Models](#database-models)
- [License](#license)

## Installation

1. **Clone the repository:**

    ```bash
    git clone https://github.com/yourusername/loan_calculator.git
    cd loan_calculator
    ```

2. **Set up a virtual environment:**

    On **Windows**:

    ```bash
    python -m venv venv
    venv\Scripts\activate
    ```

    On **macOS/Linux**:

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3. **Install the dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

4. **Set up the database:**

    In a Python shell or in your Jupyter Notebook, run:

    ```python
    from app import db, app
    with app.app_context():
        db.create_all()
    ```

5. **Run the application:**

    ```bash
    python app.py
    ```

    The application will be available at `http://127.0.0.1:5000`.

## Usage

You can interact with the application using API endpoints. Below is a list of available endpoints and their descriptions.

## API Endpoints

- **Add a User**

    ```http
    POST /user
    ```

    **Request Body:**

    ```json
    {
        "name": "John Doe",
        "income": 5000
    }
    ```

    **Response:**

    ```json
    {
        "message": "User added successfully"
    }
    ```

- **Add a Loan**

    ```http
    POST /loan
    ```

    **Request Body:**

    ```json
    {
        "amount": 1000,
        "user_id": 1,
        "date_borrowed": "2023-05-01"
    }
    ```

    **Response:**

    ```json
    {
        "message": "Loan added successfully"
    }
    ```

- **Get Total Borrowed Amount**

    ```http
    GET /total_borrowed
    ```

    **Response:**

    ```json
    {
        "total_borrowed": 5000
    }
    ```

- **Get Average Income**

    ```http
    GET /average_income
    ```

    **Response:**

    ```json
    {
        "average_income": 4500
    }
    ```

- **Get Highest Earning Month**

    ```http
    GET /highest_earning_month
    ```

    **Response:**

    ```json
    {
        "highest_earning_month": "2023-05"
    }
    ```

- **Get Predicted Income**

    ```http
    GET /predicted_income
    ```

    **Response:**

    ```json
    {
        "predicted_income": [1200.0, 1300.0, 1100.0]
    }
    ```

## Database Models

- **User**

    | Field  | Type   | Description               |
    |--------|--------|---------------------------|
    | id     | Integer| Primary Key               |
    | name   | String | Name of the user          |
    | income | Float  | Monthly income of the user|

- **Loan**

    | Field         | Type    | Description                          |
    |---------------|---------|--------------------------------------|
    | id            | Integer | Primary Key                          |
    | amount        | Float   | Loan amount                          |
    | user_id       | Integer | Foreign Key referencing User         |
    | date_borrowed | Date    | Date when the loan was borrowed      |
