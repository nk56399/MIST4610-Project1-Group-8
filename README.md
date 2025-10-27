# MIST 4610 Group 8
# Team Name:
Group 8
# Team Members:
1. Neha Kanakamedala @nk56399
2. Mason Lee @mlee1921
3. Vivienne Lin @vivi0404
4. Daniel Mok @dlm90284-ai
# Scenario Description:
Our group is building a database for a Bookstore Management System designed to help manage the sale and inventory of books while maintaining records of customers, employees, and publishers. The system tracks detailed information about each book, including its author, publisher, and quantity, and allows customers to place and pay for orders. Each customer can purchase multiple books in a single order. The system also records book reviews submitted by customers, providing insights into the books and customer satisfaction. Employees are stored in the database with their job titles and manager relationships. Publishers and authors are linked to the books they produce, supporting reporting on sales performance by publisher or author. This database demonstrates how a relational database can efficiently organize and connect business operations in a retail bookstore, ensuring accurate tracking of inventory, sales, payments, and customer feedback.
# Data Model
Our data model represents the structure of a bookstore management system. It is designed to store and manage data related to books, their authors and publishers, customer orders, payments, reviews, and employees responsible for store operations.

Book:
The Book entity stores information about each book in the store, including the ISBN, title, publication year, and links to its Publisher and Author. Each book can be written by one author and published by one publisher.

Author:
The Author entity keeps details about book authors like their names. One author can write many books forming a one-to-many relationship between Author and Book.

Publisher:
The Publisher entity contains the publisher’s name and country. A publisher can produce many books, so there is a one-to-many relationship between Publisher and Book.

Inventory:
The Inventory entity tracks the quantity of each book are available. It connects to the Book table through a one-to-many relationship.

Customer:
The Customer entity stores the customer’s name, email, phone number, and age. Customers interact with the system by placing orders and writing reviews.

Orders:
The Orders entity records each purchase made by a customer, including the order date and total amount. A customer can place many orders, forming a one-to-many relationship between Customer and Orders.

Order_Item:
Because each order can include multiple books, and each book can appear in many orders, the Order_Item entity serves as an associative entity between Order and Book. It includes attributes such as quantity and price paid.

Payment:
The Payment entity tracks payments associated with customer orders. Its attributes include payment amount and payment date. Each payment is linked to one order, forming a one-to-one relationship between Orders and Payment.

Review:
The Review entity allows customers to leave feedback on books they’ve purchased. Each review links a Customer and a Book, representing a many-to-many relationship formed through this entity. Attributes include the rating, text, and date.

Employee:
The Employee entity contains details about the employees like their names, job titles, and managers. There is a one-to-many recursive relationship (Manager–Supervisor) that allows employees to report to other employees.

This database supports the storage and management of books, their authors, publishers, and inventory. It includes customer information, orders, payments, and reviews. The database also has the employee hierarchy and roles within the organization. It supports complex relationships such as many-to-many relationships between customers and books (through reviews and orders). One-to-many relationships between publishers and books and relationships between employees.

The database does not support supplier or shipping information. There is no store location or branch management because only one store is implied. There is no book categorization like genre or keywords. Also, if a customer wants to refund their book there is no return or refund tracking.
 
<img width="1118" height="934" alt="image" src="https://github.com/user-attachments/assets/e9e46bd6-a78e-483f-b6df-39b2f29ecb39" />

# Data Dictionary:
<img width="1476" height="516" alt="image" src="https://github.com/user-attachments/assets/1c381f84-df11-46cc-b943-78e90dbbbd53" />
<img width="1462" height="400" alt="image" src="https://github.com/user-attachments/assets/89e6ce0c-3a25-4139-a340-072a494da54d" />
<img width="1490" height="432" alt="image" src="https://github.com/user-attachments/assets/453bf3a2-64e9-4340-9daa-4ee3a02bcc24" />
<img width="1464" height="336" alt="image" src="https://github.com/user-attachments/assets/e8acc703-f013-4b4a-9e5f-1b65a9dd2668" />
<img width="1482" height="478" alt="image" src="https://github.com/user-attachments/assets/862c2277-2bdf-4eeb-97c6-c8315542a188" />
<img width="1302" height="502" alt="image" src="https://github.com/user-attachments/assets/2cc8a0f9-4255-40c1-bddd-08e5b437e87a" />
<img width="1312" height="532" alt="image" src="https://github.com/user-attachments/assets/7c288852-57d9-4b7b-b157-80249f7f2a33" />
<img width="1306" height="538" alt="image" src="https://github.com/user-attachments/assets/19cc90c7-9d3c-4b77-b870-507761b53e3f" />
<img width="1488" height="604" alt="image" src="https://github.com/user-attachments/assets/f225f7f1-ed4a-4aad-bbe0-a25ca5d1bdb6" />
<img width="1502" height="434" alt="image" src="https://github.com/user-attachments/assets/62fd6993-b5ad-48d4-b9a4-8a93e9a74e38" />

# Queries:
1. Most Borrowed Authors
   
Question: Which authors were borrowed the most total units?

<img width="658" height="958" alt="image" src="https://github.com/user-attachments/assets/87ac0114-3327-4b06-a833-f35700557ef3" />

Query 1 allows managers to see which authors’ books have been borrowed or purchased the most overall. By calculating the total number of units sold for each author, managers can identify which authors are in the highest demand among customers. These insights help determine which authors’ books should be prioritized. Listing the results in descending order of total borrowed units makes it easy to see which authors generate the most interest and should receive the most attention.

Managerial Justification: Helps identify high demand authors for acquisition and promotion.

2. Customers With Orders but No Payments
   
Question: Which customers placed orders but have not made any payments?

<img width="752" height="1294" alt="image" src="https://github.com/user-attachments/assets/033f7c62-8dd2-4ae4-b797-a7a1ed7c4cff" />

Query 2 allows managers to identify customers who have placed orders but have not yet made any payments. By comparing the Orders and Payment tables, the query finds all customers linked to existing s that do not appear in the payment records. Listing the results by last and first name makes it easy for staff to locate and contact the appropriate customers for resolution.

Managerial Justification: Allows managers to monitor unpaid s and follow up for overdue
payments.

3. Books Priced Below Average Payment
   
Question: Which books are priced below the overall average payment amount and have been
borrowed at least once?

<img width="746" height="724" alt="image" src="https://github.com/user-attachments/assets/058c5232-388c-4e1c-982f-0905290922ed" />

Query 3 allows managers to identify books that are priced below the average payment amount but have still been borrowed or purchased at least once. By comparing each book’s price to the overall average payment, the query highlights titles that are both affordable and actively circulating. This helps managers recognize books that perform well, supporting decisions about pricing strategies, promotions, and restocking. Listing the results by book title makes it easy to review and select titles.

Managerial Justification: Helps managers identify affordable titles with active circulation.

4. Low Inventory Alert
   
Question: Which books have fewer than five copies available?

<img width="654" height="436" alt="image" src="https://github.com/user-attachments/assets/69298acb-e46a-4a4c-bc08-864e5f88d45e" />

Query 4 allows managers to identify books with fewer than five copies remaining in inventory, signaling titles that may soon go out of stock. By joining the Book and Inventory tables, the query retrieves each book’s title, ISBN, and current stock level to provide a clear view of low inventory items. This helps managers take action by ordering additional copies of popular or essential books before they run out. Listing the results in ascending order of stock quantity and then by book title makes it easy to prioritize restocking efforts efficiently.

Managerial Justification: Enables proactive restocking of popular or low stock titles.

5. Books
    
Question:Which books contain the word “Fiction” in their titles and who wrote them?

<img width="894" height="528" alt="image" src="https://github.com/user-attachments/assets/3c555a92-b363-4586-a5ab-7f20d2e2addc" />

Query 5 identifies all books that contain the word "Fiction" in their titles along with the authors who wrote them. By joining the Book and Author tables, it connects each title to its corresponding author. The use of the REGEXP function allows flexible pattern matching to find any title that includes the word “Fiction,” regardless of position in the text. The results are sorted alphabetically by book title. This query helps managers track fiction titles and evaluate the fiction genre within the library’s collection.

Managerial Justification: Helps managers track fiction titles and analyze genre popularity among readers

6. Loyal Customers
    
Question: Which customers have placed at least five s and how much have they paid in
total?

<img width="1000" height="362" alt="image" src="https://github.com/user-attachments/assets/24c0140e-86a1-426e-9e32-e9334c3a5441" />

Query 6 allows managers to identify loyal customers who have placed five or more s and to see the total amount each has paid. By joining the Customer, , and Payment tables, the query calculates both the number of distinct orders per customer and their total spending. This helps managers recognize people who contribute significantly to sales. Sorting by total amount paid and number of orders highlights the most valuable customers first for targeted engagement.

Managerial Justification: Helps identify loyal patrons for rewards or membership incentives.

7. Manager and Staff Counts
    
Question: How many direct reports does each manager have?

<img width="832" height="276" alt="image" src="https://github.com/user-attachments/assets/50ece612-6efc-448e-b1fa-7108dad4d470" />

Query 7 allows managers to see how many employees directly report to each manager. By performing a self-join on the Employee table, the query links each manager to their direct reports and counts how many staff members fall under their supervision. This information helps with balancing, planning, and performance evaluations, ensuring that management responsibilities are distributed effectively. Sorting the results by the number of direct reports highlights managers overseeing the largest teams, allowing leadership to assess the teams.

Managerial Justification: Assists in workload balancing and team size analysis.

8. Top Rated Books
    
Question: Which books have an average rating above 4.5 and at least ten reviews?

<img width="716" height="262" alt="image" src="https://github.com/user-attachments/assets/149bb2e7-d71f-4e29-a041-e6055ced8ce6" />

Query 8 allows managers to identify top-rated books that have received an average rating above 4.5 and at least ten reviews. This helps managers pinpoint high-quality, well-reviewed books that are popular among customers. Such insights can be used to promote these titles, feature them in marketing campaigns, or prioritize them for restocking. Sorting the results by highest average rating and review count ensures the most positively reviewed books appear first for easy recognition.

Managerial Justification: Identifies high quality titles worth recommending or featuring.

9. Inactive Customers
    
Question: Which customers have never placed an order?

<img width="724" height="518" alt="image" src="https://github.com/user-attachments/assets/ed22dee4-6262-4de1-950c-c70dd30c69e5" />

Query 9 allows managers to identify customers who have never placed an order, helping pinpoint inactive users. By checking for customers that do not appear in the Orders table, the query isolates those who have registered but have not made any purchases. This information supports targeted marketing aimed at encouraging these customers to place their first order through discounts, recommendations, or promotional emails. Sorting the results alphabetically by last and first name makes it easy for staff to review and contact potential customers for engagement efforts.

Managerial Justification: Supports targeted outreach campaigns to encourage engagement.

10.  Most Borrowed Publishers
    
Question: Which publishers have the most borrowed books overall?

<img width="688" height="738" alt="image" src="https://github.com/user-attachments/assets/8f64a37d-cfd8-44d5-9c13-3e30221e16b0" />

Query 10 allows managers to determine which publishers’ books have been borrowed or sold the most overall by summing the total quantities of books associated with each publisher. By joining the Publisher, Book, and Order_Item tables, the query connects each publisher to the books they produce, and the number of units borrowed. The insights support decisions related to performance reviews, purchasing agreements, and partnership negotiations. Sorting results in descending order of total borrowed units ensures that the most successful publishers are highlighted first for strategic focus.

Managerial Justification: Helps evaluate publisher performance and negotiate partnerships.

# Database Information:

<img width="760" height="393" alt="image" src="https://github.com/user-attachments/assets/fc8af883-4120-4ceb-9258-58e8e6e7a351" />



Name of the Database: cs_mhl67797






