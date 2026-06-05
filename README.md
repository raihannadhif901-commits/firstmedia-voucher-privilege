# First Media Privilege Vouchers Portal

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/raihannadhif901-commits/firstmedia-voucher-privilege)
[![.NET Core](https://img.shields.io/badge/.NET-8.0-blueviolet.svg)](https://dotnet.microsoft.com/download/dotnet/8.0)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4.0-38bdf8.svg)](https://tailwindcss.com/)
[![SQLite](https://img.shields.io/badge/SQLite-3.0-003b57.svg)](https://www.sqlite.org/)

<img width="881" height="424" alt="image" src="https://github.com/user-attachments/assets/a39611d9-8b2d-46c7-ab19-8c239f3abdf0" />


Exclusive Catalog & Privilege Voucher Management Portal for loyal customers of **First Media (PT Link Net Tbk)**. This application is designed with a modern, responsive (*mobile-first*), high-performance interface, and is equipped with user click tracking telemetry features and graphic analytics visualization on the admin side.

This project was built using **ASP.NET Core (Razor Pages)** and **Tailwind CSS v4** with a **SQLite** database to support easy portability of local demos without complex external database configurations.

---

## Main Features

### 1. Dynamic Promo Catalog (`/Promos`)
* **Modern Client Look**: Clean design with a unified orange theme typical of the Linknet brand, using a combination of attractive typography (**Space Grotesk** for the header & **Plus Jakarta Sans** for the body text).
* **Instant Category Filter**: Filter promotions (F&B, Entertainment, Shopping, Transport) dynamically using integrated query parameters.
* **Integrated Pagination**: Neatly divides the voucher catalog (default configuration: 6 vouchers per page) to optimize page load times on mobile devices.

### 2. Code Sensor & Auto Copy (`/VoucherDetail`)
* **Interactive Reveal Code**: The redeem code is visually disguised (*blurred*) when the page is first loaded to give an interactive impression.
* **Smart Action Button**: The unblur button dynamically transitions to a **"Copy Code"** (*Copy to Clipboard*) button with visual feedback "Copyed!" green after copying.

### 3. Admin Dashboard & Analytics Telemetry (`/Admin`)
* **Click Telemetry**: Every voucher code disclosure click is recorded asynchronously (*background fetch API*) into the SQLite database.
* **Summary Statistics (Stat Cards)**: Displays *real-time* metrics regarding Total Vouchers, Total Accumulative Clicks, and the names of the Most Popular Partners (along with the number of impressions).

* **Chart Visualization (Chart.js)**:
    * *Bar Chart* (Bar Graph) displays the **Top 5 Most Popular Vouchers** based on the highest number of clicks.
    * *Doughnut Chart* (Donut Chart) displays **Distribution Share of Clicks per Promo Category**.
* **CRUD Voucher Management**: New validated voucher creation form, complete with **Demo Image Templates** button to instantly populate Unsplash image URLs while testing.

---

## Technology Stack

| Components | Technology | Description |
| :--- | :--- | :--- |
| **Backend Framework** | ASP.NET Core (Razor Pages) | .NET 8.0 (LTS) Runtime - Server-Side Rendered (SSR) |
| **Database** | SQLite | File-based local database (`firstmedia_vouchers.db`) |
| **ORM / Data Access** | Entity Framework Core 8.0.12 | Secure data object mapping & SQL Injection protection |
| **Frontend Styling** | Tailwind CSS v4 | Utility-first CSS with fastest NPM CLI compilation |
| **Typography** | Space Grotesk & Plus Jakarta Sans | Google Fonts modern combination for high readability |
| **Analytics & Icons** | Chart.js & Lucide Icons | Interactive graphic visualization & SVG vector icons |

---

## Main Project Structure

```text
├── Data/
│   ├── AppDbContext.cs       # EF Core table configuration
│   └── DbInitializer.cs      # Automatic seeding of 12 initial dummy vouchers
├── Models/
│   └── Voucher.cs            # Voucher & Telemetry data model
├── Pages/
│   ├── Admin/
│   │   ├── Create.cshtml     # New voucher input form (admin)
│   │   └── Index.cshtml      # Visualization dashboards & CRUD tables
│   ├── Promos.cshtml         # Paginated catalog & filter categories
│   ├── VoucherDetail.cshtml  # Voucher details, unblur code & copy utility
│   └── Shared/_Layout.cshtml # Orange themed master layout & Google Fonts
├── Styles/
│   └── input.css             # Tailwind v4 configuration files & keyframes
├── wwwroot/
│   ├── css/site.css          # Tailwind CSS final compilation result
│   └── icon.png              # Linknet/First Media official logo file
└── Program.cs                # Application bootstrap entry-point & seeding
```

---

## How to Run on Local

### Prerequisites
1. **.NET 8.0 SDK** installed on your computer.
2. **Node.js & NPM** installed to build Tailwind CSS assets.

### Step 1: Clone & Go to Project Directory
```bash
git clone <your-repository-url>
cd firstmedia-voucher-privilege
```

### Step 2: Build Tailwind CSS Assets
Install Tailwind CLI dependencies and compile:
```bash
npm install
npm run build:css
```
*(Use `npm run watch:css` in a separate terminal if you want to modify the display so that the CSS compiles automatically when the file is changed).*

### Step 3: Run the Application
Run the following command to run the local server:
```bash
dotnet watch
```
Once the server is up, open your browser at the address: **`http://localhost:5000`** (or another port listed in the terminal).

---

## Portfolio Demo Testing Scenarios

1. **Catalog Access**: Go to the main page. You will immediately see a catalog containing 6 initial vouchers with a stunning Linknet orange theme. Click the **2** page button at the bottom to see the remaining vouchers.

2. **Code Disclosure Test**: Select *Starbucks Coffee* voucher, click **Show Code**. The voucher code will be smoothly blurred and the button will change to **Copy Code**. Click again to copy to clipboard.

3. **Admin Telemetry Verification**: 
    * Open the admin dashboard in the **Admin Dashboard** menu (`/Admin`).
    * Observe the **Total Clicks** statistics card and the Starbucks Coffee **Clicks / Reveal** column which increases to `1x`.
    * Pay attention to the **Bar Chart** and **Doughnut Chart** which also update the data graphically and dynamically instantly!

4. **Add New Voucher**: Click **Add New Voucher** in the top right corner, fill in the form, click the **F&B (Coffee)** demo image template, then click **Save & Publish**. Return to the main catalog page to verify that the voucher has appeared automatically.
