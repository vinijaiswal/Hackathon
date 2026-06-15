# Hackathon

Discord: https://discord.gg/xR38RFvW

## Setup

### 1. Install dependencies

Open `eda.ipynb` and run this in the first cell (installs into the notebook kernel):

```python
%pip install -r requirements.txt
```

### 2. Get your Databricks token

1. Open the Databricks workspace: https://dbc-7cdce5e8-6be4.cloud.databricks.com
2. Click your profile icon (top right) → **Settings** → **Developer**
3. Under **Access tokens**, click **Generate new token**
4. Give it a name (e.g. `hackathon`), set an expiry, and click **Generate**
5. Copy the token — you won't be able to see it again

### 3. Get your SQL Warehouse HTTP path

1. In the Databricks sidebar go to **SQL** → **SQL Warehouses**
2. Click your warehouse → **Connection details** tab
3. Copy the **HTTP path** (looks like `/sql/1.0/warehouses/abc123`)

### 4. Configure credentials

Copy the template and fill in your values:

```bash
cp config/databricks.yaml.example config/databricks.yaml   # if example exists, otherwise edit directly
```

Edit `config/databricks.yaml`:

```yaml
host: dbc-7cdce5e8-6be4.cloud.databricks.com
token: YOUR_TOKEN_HERE
http_path: /sql/1.0/warehouses/YOUR_WAREHOUSE_ID
```

> `config/databricks.yaml` is listed in `.gitignore` and will never be committed.

### 5. Run the notebook

Open `eda.ipynb` and run all cells.