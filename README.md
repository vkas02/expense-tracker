# Vue Transaction Tracker App

A simple Vue.js application to track income and expenses. Users can add, delete, and view transactions, as well as see their balance, income, and expenses.

## Features

- **Add Transactions**: Users can add new transactions (both income and expenses).
- **Delete Transactions**: Users can delete transactions from the list.
- **Balance Calculation**: The app calculates and displays the total balance based on income and expenses.
- **Income and Expense Breakdown**: Displays the total income and expenses separately.
- **Persistent Storage**: Transactions are saved to `localStorage` so that the data persists even after the page is refreshed.

## Technology Stack

- **Vue.js**: A progressive JavaScript framework used for building the user interface.
- **Vue Toastification**: Used for showing success notifications when transactions are added or deleted.
- **LocalStorage**: Data is stored in the browser's local storage for persistence across sessions.

## Project Structure

```bash
src/
  ├── components/
  │   ├── AddTransaction.vue   # Component for adding a new transaction
  │   ├── Balance.vue          # Component displaying the balance
  │   ├── Header.vue           # Header component
  │   ├── IncomeExpenses.vue   # Component showing income and expense breakdown
  │   ├── TransactionList.vue  # Component for displaying the list of transactions
  └── App.vue                  # Main app component
  └── main.js                  # Entry point for Vue instance
