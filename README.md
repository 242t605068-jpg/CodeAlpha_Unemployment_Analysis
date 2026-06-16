import pandas as pd
import matplotlib.pyplot as plt

# Load Dataset
df = pd.read_csv("Unemployment_Rate_upto_11_2020.csv")

# Display Dataset Information
print("First 5 Rows:")
print(df.head())

# Clean Column Names
df.columns = df.columns.str.strip()

# Convert Date Column
df['Date'] = pd.to_datetime(df['Date'], dayfirst=True)

# Unemployment Trend Analysis
plt.figure(figsize=(10, 5))
plt.plot(df['Date'], df['Estimated Unemployment Rate (%)'])
plt.title("Unemployment Rate Trend")
plt.xlabel("Date")
plt.ylabel("Unemployment Rate (%)")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Covid-19 Impact Analysis
covid_data = df[df['Date'].dt.year == 2020]

plt.figure(figsize=(10, 5))
plt.plot(covid_data['Date'],
         covid_data['Estimated Unemployment Rate (%)'])
plt.title("Covid-19 Impact on Unemployment")
plt.xlabel("Date")
plt.ylabel("Unemployment Rate (%)")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Average Unemployment Rate
avg_rate = df['Estimated Unemployment Rate (%)'].mean()
print("\nAverage Unemployment Rate:", avg_rate)
