# Life Stats Tracker

A minimalist life statistics tracker optimized for Kindle Paperwhite (600x800px) and deployable on GitHub Pages.

## Features

- 📊 **Dynamic Formula Support**: Calculate derived statistics from base values
- 📱 **Kindle Optimized**: Perfect display on 600x800 e-ink screens
- 🔄 **Easy Updates**: Just edit `stats.json` to update your stats
- 🎨 **Clean Design**: Minimalist, high-contrast design for e-ink displays
- 📝 **Descriptions**: Add context to your stats with optional descriptions

## Deployment on GitHub Pages

1. Go to your repository Settings → Pages
2. Under "Source", select `main` branch
3. Click Save
4. Your site will be available at `https://<your-username>.github.io/<repository-name>/`

## How to Update Your Stats

Edit the `stats.json` file with your data:

```json
{
  "lastUpdated": "2026-01-29T12:00:00Z",
  "stats": [
    {
      "id": "unique_id",
      "name": "Display Name",
      "value": 100,
      "description": "Optional description"
    }
  ]
}
```

### Basic Stat Properties

- **`id`** (optional): Unique identifier for use in formulas
- **`name`** (required): Display name for the stat
- **`value`** (optional): Numeric value for the stat
- **`description`** (optional): Small text shown below the name
- **`formula`** (optional): Mathematical expression using other stat IDs
- **`format`** (optional): How to format the result

### Using Formulas

Stats can reference other stats by their `id` in formulas:

```json
{
  "id": "books_read",
  "name": "Books Read",
  "value": 42
},
{
  "name": "Books per Month",
  "formula": "books_read / 12",
  "format": "decimal"
}
```

**Supported operations**: `+`, `-`, `*`, `/`, `()` (parentheses for order)

### Format Options

- **`percentage`**: Shows as "45.5%"
- **`decimal`**: Shows as "3.50" (2 decimal places)
- **`integer`**: Rounds to whole number
- *no format*: Shows raw value

## Examples

### Simple Tracking
```json
{
  "id": "weight",
  "name": "Current Weight (kg)",
  "value": 70.5,
  "description": "Morning weight"
}
```

### Calculated Stats
```json
{
  "id": "completed",
  "name": "Tasks Completed",
  "value": 150
},
{
  "id": "total",
  "name": "Total Tasks",
  "value": 200
},
{
  "name": "Completion Rate",
  "formula": "(completed / total) * 100",
  "format": "percentage",
  "description": "Tasks done this month"
}
```

### Complex Calculations
```json
{
  "id": "daily_calories",
  "name": "Daily Calories",
  "value": 2000
},
{
  "id": "days_tracked",
  "name": "Days Tracked",
  "value": 30
},
{
  "name": "Monthly Calories",
  "formula": "daily_calories * days_tracked",
  "format": "integer"
}
```

## Tips for Kindle Paperwhite

- Keep stat names concise (the screen is only 600px wide)
- Use high-contrast text (black on white works best)
- Limit to 10-15 stats per page for best readability
- Update the `lastUpdated` timestamp when you modify data

## File Structure

- `index.html` - Main page with JavaScript logic
- `styles.css` - Kindle-optimized styling
- `stats.json` - Your data and formulas
- `_config.yml` - Jekyll configuration for GitHub Pages

## License

Free to use and modify!