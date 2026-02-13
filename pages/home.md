---
name: Home
assetId: 7ce7e5f5-9d8f-4208-9a43-2afc916a9ef5
type: page
---

# Sales Dashboard

{% big_value
  data="demo_daily_orders"
  value="sum(total_sales)"
  fmt="usd1m"
  title="Total Revenue"
  date_range={
    date="date"
    range="2024-01-01 to 2024-12-31"
  }
  comparison={
    compare_vs="prior year"
  }
/%}

{% big_value
  data="demo_daily_orders"
  value="sum(transactions)"
  fmt="#,##0"
  title="Total Transactions"
  date_range={
    date="date"
    range="2024-01-01 to 2024-12-31"
  }
  comparison={
    compare_vs="prior year"
  }
/%}

{% big_value
  data="demo_daily_orders"
  value="avg(avg_transaction_value)"
  fmt="usd2"
  title="Avg Transaction Value"
  date_range={
    date="date"
    range="2024-01-01 to 2024-12-31"
  }
  comparison={
    compare_vs="prior year"
  }
/%}

## Revenue Trend

{% line_chart
  data="demo_daily_orders"
  x="date"
  y="sum(total_sales)"
  date_grain="month"
  y_fmt="usd1m"
  title="Monthly Revenue"
/%}

## Sales by Category

{% bar_chart
  data="demo_daily_orders"
  x="category"
  y="sum(total_sales)"
  y_fmt="usd1m"
  title="Revenue by Category"
  order="sum(total_sales) desc"
/%}

## Category Performance

{% table
  data="demo_daily_orders"
%}
  {% dimension
    value="category"
  /%}
  {% measure
    value="sum(total_sales)"
    title="Revenue"
    fmt="usd1m"
    date_range={
      range="2024-01-01 to 2024-12-31"
      date="date"
    }
    comparison={
      compare_vs="prior year"
    }
    viz="delta"
  /%}
  {% measure
    value="sum(transactions)"
    title="Transactions"
    fmt="#,##0"
    date_range={
      range="2024-01-01 to 2024-12-31"
      date="date"
    }
  /%}
  {% measure
    value="sum(total_sales) / sum(transactions) as avg_price"
    title="Avg Price"
    fmt="usd2"
    date_range={
      range="2024-01-01 to 2024-12-31"
      date="date"
    }
  /%}
{% /table %}
