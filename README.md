# spread sheet analysis project

import csv

# Read data from the spreadsheet
with open('sales.csv', 'r') as csv_file:
    csv_reader = csv.DictReader(csv_file)
    for row in csv_reader:
        print(row)

# Open the CSV file
with open('sales.csv', 'r') as file:
    reader = csv.reader(file)

    # Find the index of the "sales" column
    header = next(reader)
    sales_index = header.index('sales')

    # Collect the data from the "sales" column into a list
    sales_data = [row[sales_index] for row in reader]

print(sales_data)

# Output the total results across all months
def calculate_total_sales(csv_file):
    total_sales = 0

    with open(csv_file, 'r') as file:
        reader = csv.reader(file)
        next(reader)  # Skip the header row if present

        for row in reader:
            sales = float(row[sales_index])
            total_sales += sales

    return total_sales

total_sales = calculate_total_sales('sales.csv')
print(f'Total sales across all months: {total_sales}')
