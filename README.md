def main():
    usage = {}

    print("Daily Internet Usage Tracker")
    print("Enter 'done' when finished.\n")

    while True:
        day = input("Day name: ").strip()

        if day.lower() == "done":
            break

        if not day:
            print("Day name cannot be empty.")
            continue

        if day in usage:
            print("This day is already registered.")
            continue

        try:
            amount = float(input("Usage in GB: "))

            if amount < 0:
                print("Usage cannot be negative.")
                continue

            usage[day] = amount

        except ValueError:
            print("Please enter a valid number.")

    if not usage:
        print("No usage data available.")
        return

    total = sum(usage.values())
    average = total / len(usage)

    highest_day = max(usage, key=usage.get)
    lowest_day = min(usage, key=usage.get)

    print("\n--- Internet Usage Report ---")

    for day, amount in usage.items():
        print(f"{day}: {amount:.2f} GB")

    print(f"\nTotal usage: {total:.2f} GB")
    print(f"Daily average: {average:.2f} GB")
    print(f"Highest usage: {highest_day} ({usage[highest_day]:.2f} GB)")
    print(f"Lowest usage: {lowest_day} ({usage[lowest_day]:.2f} GB)")

if __name__ == "__main__":
    main()
