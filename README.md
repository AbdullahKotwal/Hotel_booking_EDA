# Hotel Booking Demand — Exploratory Data Analysis

Exploratory data analysis and cleaning of a hotel booking demand dataset, covering data quality issues, cleaning, feature engineering, and visual analysis of booking and cancellation patterns.

## 📁 Repository Structure

```
├── hotel_booking.csv           # Raw dataset (119,390 rows, 36 columns)
├── hotel_booking_eda.ipynb     # Full EDA notebook (cleaning + analysis + visuals)
├── hotel_booking_cleaned.csv   # Cleaned, analysis-ready dataset (87,229 rows, 35 columns)
└── README.md
```

## 📊 Dataset

The raw dataset contains booking records for a City Hotel and a Resort Hotel, including arrival dates, stay length, guest details, booking channel, cancellation status, and pricing (ADR — average daily rate).

## 🧹 Data Cleaning Steps

1. **Dropped PII columns** — `name`, `email`, `phone-number`, `credit_card` (synthetic, not useful for analysis, privacy risk).
2. **Removed hidden duplicates** — ~32,000 rows were true duplicate bookings, masked by fake per-row PII values.
3. **Dropped `company`** column (94%+ missing).
4. **Imputed missing values** — `agent` → 0 (no agent/direct booking), `country` → `'Unknown'`, `children` → 0.
5. **Removed invalid bookings** — rows with 0 total guests (adults + children + babies = 0).
6. **Fixed `adr` (average daily rate)** — removed negative values, capped extreme outliers at the 99.9th percentile.
7. **Converted `reservation_status_date`** to proper datetime type.

## ⚙️ Feature Engineering

| Feature | Description |
|---|---|
| `total_nights` | Weekend nights + week nights |
| `total_guests` | Adults + children + babies |
| `total_revenue` | ADR × total nights |
| `is_family` | 1 if booking includes children or babies |

## 📈 Key Insights

- **City Hotel** receives more bookings than **Resort Hotel**, but also has a **higher cancellation rate**.
- **Longer lead time** (booking made far in advance) is strongly associated with **higher cancellation likelihood**.
- **Market segment matters** — online/group bookings cancel far more often than corporate/direct bookings.
- Both booking volume and cancellations show **clear seasonality**, peaking in summer months.

## 🛠️ Tools Used

- Python, Pandas, NumPy
- Matplotlib, Seaborn
- Jupyter Notebook

## ▶️ How to Run

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook hotel_booking_eda.ipynb
```

## 👤 Author

Abdullah
