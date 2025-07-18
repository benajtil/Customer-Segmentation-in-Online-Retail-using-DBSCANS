# PHP‑Based Customer Segmentation & Admin Dashboard

## Description

This full‑stack project, completed as part of our December 2024 thesis at Notre Dame of Marbel University, delivers a PHP‑powered web application with a comprehensive admin dashboard for managing all MySQL database tables and records—customers, orders, products, and users. Through a clean, responsive interface, administrators can filter, sort, search, and export data; monitor real‑time site metrics (total customers, sales, active sessions); and manage user accounts (create, edit, revoke access).

Beyond the classic LAMP‑stack front end, the repository includes a Python module (built on pandas and scikit‑learn) that preprocesses raw transaction data and applies the DBSCAN algorithm using both RFM and LRFMP feature sets to uncover natural customer clusters. These segmentation results can be visualized or fed back into the PHP dashboard for targeted marketing campaigns.

Although discontinued following our successful thesis defense, this codebase remains a complete example of integrating a PHP/MySQL dashboard with a modern data‑science backend for real‑world customer‑segmentation workflows.

## Features

- **Data Management**: View, filter, search, sort, and export customers, orders, products, and users.
- **Real‑Time Metrics**: Live display of total customers, sales volume, active sessions, etc.
- **User Administration**: CRUD operations on admin/staff accounts with role‑based access.
- **Customer Segmentation**: Python scripts for data preprocessing and DBSCAN clustering (RFM & LRFMP).
- **Visualization**: Interactive charts and cluster plots (via Matplotlib / Chart.js).

## Technologies

- **Backend**: PHP 7+, MySQL 5.7+
- **Frontend**: HTML5, CSS3, JavaScript (jQuery)
- **Data Science**: Python 3.8+, pandas, scikit‑learn, Matplotlib
- **Server**: Apache (XAMPP)

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/USERNAME/repo-name.git
   cd repo-name
   ```

2. **Set up the database**

   - Create a MySQL database named `your_db_name`.
   - Import `schema.sql` and `data_dump.sql` from the `/database` folder via phpMyAdmin or CLI:
     ```bash
     mysql -u root -p your_db_name < database/schema.sql
     mysql -u root -p your_db_name < database/data_dump.sql
     ```

3. **Configure PHP**

   - Copy `config/config.sample.php` to `config/config.php` and update DB credentials.
   - Ensure `uploads/` and `logs/` directories are writable.

4. **Install Python dependencies**

   ```bash
   cd segmentation
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

5. **Run the application**

   - Start Apache/PHP server (e.g., via XAMPP control panel).
   - Visit `http://localhost/your-app/` in your browser.

## Python Segmentation Module

Inside the `/segmentation` folder you'll find:

- `preprocess.py` – cleans and transforms raw transaction CSVs into feature matrices.
- `dbscan_segmentation.py` – applies DBSCAN with configurable `epsilon` and `min_samples`.
- `visualize_clusters.py` – generates 2D scatter plots of resulting clusters.

Run example:

```bash
cd segmentation
python preprocess.py --input ../data/transactions.csv --output cleaned.csv
python dbscan_segmentation.py --input cleaned.csv --eps 0.5 --min-samples 5 --output clusters.csv
python visualize_clusters.py --input clusters.csv --output ../screenshots/cluster-plot.png
```

## Usage

1. **Log in** as an admin (default creds in `config/config.sample.php`).
2. **Navigate** the sidebar to view Customers, Orders, Products, or Users.
3. **Use** the search bar and filters to refine data views.
4. **Generate** segmentation: click **Run Segmentation** under the **Analytics** menu to re‑compute clusters.

## Screenshots

### Admin Dashboard

![Alt text](/images/1.png)
![Alt text](/images/2.png)

### Customer List View and Segmentation

![Alt text](/images/3.png)
![Alt text](/images/4.png)
![Alt text](/images/5.png)

## License

This project is released under the MIT License. See [LICENSE](LICENSE) for details.
