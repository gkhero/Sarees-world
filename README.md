import sqlite3

# Connect to database
conn = sqlite3.connect('saree_business.db')
cursor = conn.cursor()

# Create inventory table
cursor.execute('''CREATE TABLE IF NOT EXISTS inventory (
                    id INTEGER PRIMARY KEY,
                    name TEXT,
                    color TEXT,
                    price REAL,
                    stock INTEGER)''')

# Function to add a saree
def add_saree(name, color, price, stock):
    cursor.execute('INSERT INTO inventory (name, color, price, stock) VALUES (?, ?, ?, ?)',
                   (name, color, price, stock))
    conn.commit()
    print(f'{name} added successfully!')

# Function to view inventory
def view_inventory():
    cursor.execute('SELECT * FROM inventory')
    for row in cursor.fetchall():
        print(row)

# Function to update stock
def update_stock(saree_id, new_stock):
    cursor.execute('UPDATE inventory SET stock = ? WHERE id = ?', (new_stock, saree_id))
    conn.commit()
    print('Stock updated successfully!')

# Function to delete a saree
def delete_saree(saree_id):
    cursor.execute('DELETE FROM inventory WHERE id = ?', (saree_id,))
    conn.commit()
    print('Saree deleted successfully!')

# Example usage
add_saree('Kanchipuram Silk', 'Gold', 3000, 5)
view_inventory()
update_stock(1, 3)
delete_saree(1)

# Close connection
conn.close()

