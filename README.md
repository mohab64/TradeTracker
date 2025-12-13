# TradeTracker
Advanced Telegram Trading Journal Bot by Questionist. 🚀 Automates PnL calculations, tracks Long/Short positions, and generates Daily/Weekly/Monthly reports. Built with high-performance Python Asyncio &amp; PostgreSQL. The smart way to journal trades.


# TradeTracker Bot 🚀

**Your Ultimate Personal Trading Journal on Telegram**

Stop wasting time with messy Excel sheets or manual calculations. **TradeTracker Bot**, developed by **Questionist**, is a powerful, high-performance Telegram bot designed to automate your trading journal, verify your trades, and track your PnL (Profit & Loss) with absolute precision.

Whether you are a scalper or a swing trader, this bot helps you stay disciplined by keeping a clean record of every single trade, calculating your exact risk/reward, and summarizing your performance over time.

## 🌟 Why TradeTracker?

- **⚡ Instant Math:** No more calculators. Just input your entry, targets, and lots. The bot handles the complex PnL math for both Long and Short positions, including split entries and multiple take-profit targets.
- **📊 Professional Reports:** Instantly generate Daily, Weekly, and Monthly reports. Know exactly how much you made (or lost) in a specific period.
- **🛡️ Data Integrity:** Uses a robust PostgreSQL database to store every trade securely. Your data is yours.
- **🚀 Async Performance:** Built with Python's `asyncio` and `telebot`, it handles multiple requests lightning fast without blocking.
- **🎯 Split Targets Support:** Have a complex strategy with 2 entries and 2 TP levels? We got you. The bot calculates the weighted average result automatically.

## 🛠️ Features Explained

Here is a breakdown of the core functions, just like an API documentation:

### `calculate_pnl_value(entry, target, lots, trade_type)`
Calculates the raw dollar value of a trade based on entry and exit points.
- **Input:** Entry price, Target price, Lots size, Trade type (Long/Short).
- **Logic:** Automatically adjusts for Short positions where a lower target means profit.
- **Output:** Returns the exact profit or loss in USD.

### `calculate_balance_percent(balance, pnl)`
Determines the percentage impact of a trade on the current account balance.
- **Input:** Current Account Balance, Calculated PnL.
- **Output:** Returns the percentage growth or drawdown (e.g., +2.5% or -1.2%).

### `create_keyboard(items, page_number, mode)`
Generates a dynamic, paginated inline keyboard for navigating through trade history.
- **Input:** List of items (trades), current page number, mode (daily/weekly/monthly).
- **Features:** Efficiently handles lists with 100+ items by splitting them into pages of 10, preventing UI clutter.

### `save_new_report_flow` (State Machine)
An intelligent step-by-step conversation handler that guides the user.
- **Logic:** Instead of one complex command, it asks for data piece by piece (Currency -> Balance -> Lots...).
- **Validation:** Ensures inputs are valid numbers and logically correct before saving to the database.

## 🚀 Installation & Setup

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/Questionist/TradeTracker.git
    cd TradeTracker
    ```

2.  **Install Dependencies:**
    First, try installing all requirements at once:
    ```bash
    pip install -r requirements.txt
    ```
    If you encounter version conflicts, you can install the core libraries manually:
    ```bash
    pip install pyTelegramBotAPI psycopg2-binary
    ```

3.  **Database Configuration:**
    *   Make sure you have PostgreSQL installed and running.
    *   Create a database named `postgres` (or change it in the code).
    *   Update the `DB_USER`, `DB_PASS`, and `DB_HOST` variables in `main_en.py`.

4.  **Bot Token:**
    *   Get your token from @BotFather on Telegram.
    *   Paste it into the `TOKEN` variable in `main_en.py`.

5.  **Run the Bot:**
    ```bash
    python main_en.py
    ```

## 📸 Example Workflow

1.  **Start the Bot:** `/start`
2.  **New Trade:** Click **New Report**.
3.  **Input Details:**
    *   *Currency:* `XAUUSD`
    *   *Balance:* `10000` (First time only)
    *   *Lots:* `0.1`
    *   *Type:* `Short`
    *   *Entry:* `2035.50`
    *   *Target:* `2030.00`
    *   *Stop Loss:* `2040.00`
4.  **Result:**
    > **Saved.**
    > **PnL:** $55.00
    > **New Balance:** $10,055.00

## 📝 Configuration

TradeTracker is built to be flexible. You can easily modify the following in `main_en.py`:

*   **`SUDOS`**: Add your Telegram User ID to this tuple to grant yourself access.
*   **`PER_PAGE`**: Change pagination size (default is 10 items).

## 🤝 Contributing

We love open source! If you have ideas for new features (like chart generation, CSV export, or AI analysis), feel free to fork the repo and submit a pull request.

---
*Built with ❤️ by Questionist.* (Check us out at [Questionist.ir](https://questionist.ir))
