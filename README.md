# Amazon GST & Pricing Calculator - Logic & Documentation

## Overview
This project is a specialized calculator designed to help e-commerce sellers (specifically on platforms like Amazon) determine the correct selling price for their products. It takes into account various costs, desired profit margins, and GST (Goods and Services Tax) to output a final "Shelf Price" or "Listing Price".

## Core Pricing Logic: Margin vs. Markup

One of the most critical aspects of this calculator is how it determines the selling price based on your desired profitability. We use **Margin** (specifically on the Selling Price before GST), not **Markup**.

### What is the difference?

*   **Markup** is calculated on your **Cost**.
    *   *Formula:* `Markup % = (Profit / Cost) * 100`
    *   *Example:* You buy a pen for ₹100 and want a 50% markup. You sell it for ₹150. Your profit is ₹50.

*   **Margin** is calculated on your **Selling Price**.
    *   *Formula:* `Margin % = (Profit / Selling Price) * 100`
    *   *Example:* You want a 50% margin on a pen that costs ₹100. You must sell it for ₹200.
        *   Selling Price (₹200) - Cost (₹100) = Profit (₹100).
        *   ₹100 Profit is exactly 50% of the ₹200 Selling Price.

### Why do we calculate Margin on "Selling Price before GST"?

We chose this specific method for three key business reasons:

#### 1. GST is a Pass-Through, Not Revenue
When you sell a product for ₹118 (₹100 Price + ₹18 GST), the ₹18 does not belong to you; it belongs to the government. Your actual revenue is only ₹100.
*   If you calculated margin on the *inclusive* price (₹118), you would be inflating your revenue base with money you can't keep.
*   By calculating margin on the **Selling Price before GST**, we ensure your profit percentage is based on the actual value you are capturing.

#### 2. Alignment with Financial Reporting
In professional accounting and P&L (Profit & Loss) statements, **Gross Margin** is always calculated as `(Revenue - COGS) / Revenue`.
*   "Revenue" in accounting is always Net Sales (excluding sales tax/GST).
*   By using this logic, the "20% Margin" you enter in this calculator directly translates to the "20% Gross Margin" you will see on your financial reports at the end of the year.

#### 3. It's "Easier" for Profit Planning
Using Margin is often considered "easier" or "safer" for business planning than Markup because it prevents underpricing.
*   **The Markup Trap:** If you want to keep 20% of the money you collect, and you just add a 20% markup to your cost, you will actually only make a 16.6% margin.
    *   *Cost 100 + 20% Markup = 120 Price. Profit 20. Margin = 20/120 = 16.6%.*
*   **The Margin Guarantee:** By using the Margin formula, if you want to keep 20% of the sale, the calculator mathematically ensures you get exactly that.
    *   *Cost 100 / (1 - 20%) = 125 Price. Profit 25. Margin = 25/125 = 20%.*

## The Formula Used

The calculator uses the following derivation to find your target price:

1.  **Total Cost** = Purchase + Shipping + Referral + Packaging
2.  **Selling Price (Before GST)** = `Total Cost / (1 - (Margin % / 100))`
3.  **GST Amount** = Selling Price (Before GST) * (GST Rate % / 100)
4.  **Final Selling Price** = Selling Price (Before GST) + GST Amount

*(Note: The Final Selling Price is rounded to the nearest whole number for cleaner pricing).*
