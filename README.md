# 2c Inventory Management System
## Requirements for the system: 

**Functional requirements:**
-	Adding, updating and deleting products
-	Tracking stock levels in real time
-	Generating stock and order reports
-	Users should have role-based access
-	Barcode scanning for quick product identification  
-	Mange multiple warehouse
-	Recording stock transactions
-	Order handling

**Functional requirements:**
-	It should have an intuitive and responsive UI
-	High availability with minimal downtime
-	The system has to be scalable to handle an increasing number of products and users
-	Response time should be under 1 second
# **Use Cases for Inventory Management System**
![image](https://github.com/user-attachments/assets/2efdd081-bf68-4cf7-b112-b9b40c5f0737)
## **Actors**
- **Admin** – manages users, settings, warehouses.
- **Warehouse Staff** – receives/releases stock, scans barcodes.
- **System** – automates stock checks, reports.

---

## **1. Manage Products**
**Actors:** Admin  
**Steps:**  
1. Add, update, or delete a product.  
2. System saves changes.  

**Alternative Flows:**  
- Invalid input → error message.  

---

## **2. Track Stock Levels**
**Actors:**  Warehouse Staff  
**Steps:**  
1. Request stock report.  
2. System displays availability.  

**Alternative Flows:**  
- Out of stock → "Not available" message.  

---

## **3. Process Orders**
**Actors:** Warehouse Staff  
**Steps:**  
1. Create an order, select products.  
2. Confirm; system updates stock.  

**Alternative Flows:**  
- Insufficient stock → warning.  

---

## **4. Generate Reports**
**Actors:** Admin 
**Steps:**  
1. Select report type & period.  
2. System generates report.  

**Alternative Flows:**  
- No data → "No data available" message.  

---

## **5. User Authentication & Roles**
**Actors:** Admin, System  
**Steps:**  
1. User logs in.  
2. System grants access based on role.  

**Alternative Flows:**  
- Wrong credentials → error.  

## UML diagram 
![image](https://github.com/user-attachments/assets/a93116f4-21e9-43b4-b984-3c583bee3447)
```java
class Product {
    private Long id;
    private String SKU;
    private String title;
    private String category;
    private BigDecimal unitPrice;
    private Barcode barcode;
    
    public void assignBarcode(Barcode barcode) {
        this.barcode = barcode;
    }
    public void updatePrice(BigDecimal price) {
        this.unitPrice = price;
    }
}

class Barcode {
    private Long id;
    private String type;
}

class Warehouse {
    private Long id;
    private String location;
    private int capacity;
    private Map<String, Integer> stock;
    
    public void addStock(Product product, int quantity) {}
    public void removeStock(Product product, int quantity) {}
    public int getAvailableSpace() { return 0; }
}

class Order {
    private Long id;
    private String status;
    private List<Product> products;
    
    public void addItem(Product product) {
        products.add(product);
    }
    public void completeOrder() {}
}

class User {
    private Long id;
    private String name;
    private String role;
    
    public void auth(String password) {}
}

class InventoryTransaction {
    private Long id;
    private String type;
    private int quantity;
    private User user;
    private Product product;
    private LocalDateTime timestamp;
    
    public void logTransaction() {}
}

class ReportGenerator {
    public void generateStockReport(Warehouse warehouse) {}
    public void generateOrderReport(Order order) {}
}
```
