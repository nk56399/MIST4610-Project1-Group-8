# MIST 4610 Group 8
# Team Name:
Group 8
# Team Members:
1. Neha Kanakamedala @nk56399
2. Mason Lee @mlee1921
3. Vivienne Lin @
4. Daniel Mok @dlm90284-ai
# Scenario Description:
Our group is building a database for a Bookstore Management System designed to help manage the sale and inventory of books while maintaining records of customers, employees, and publishers. The system tracks detailed information about each book, including its author, publisher, and quantity, and allows customers to place and pay for orders. Each customer can purchase multiple books in a single orde. The system also records book reviews submitted by customers, providing insights into the books and customer satisfaction. Employees are stored in the database with their job titles and manager relationships. Publishers and authors are linked to the books they produce, supporting reporting on sales performance by publisher or author. This database demonstrates how a relational database can efficiently organize and connect business operations in a retail bookstore, ensuring accurate tracking of inventory, sales, payments, and customer feedback.
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

Order:
The Order entity records each purchase made by a customer, including the order date and total amount. A customer can place many orders, forming a one-to-many relationship between Customer and Order.

Order_Item:
Because each order can include multiple books, and each book can appear in many orders, the Order_Item entity serves as an associative entity between Order and Book. It includes attributes such as quantity and price paid.

Payment:
The Payment entity tracks payments associated with customer orders. Its attributes include payment amount and payment date. Each payment is linked to one order, forming a one-to-one relationship between Order and Payment.

Review:
The Review entity allows customers to leave feedback on books they’ve purchased. Each review links a Customer and a Book, representing a many-to-many relationship formed through this entity. Attributes include the rating, text, and date.

Employee:
The Employee entity contains details about the employees like their names, job titles, and managers. There is a one-to-many recursive relationship (Manager–Supervisor) that allows employees to report to other employees.

This database supports the storage and management of books, their authors, publishers, and inventory. It includes customer information, orders, payments, and reviews. The database also has the employee hierarchy and roles within the organization. It supports complex relationships such as many-to-many relationships between customers and books (through reviews and orders). One-to-many relationships between publishers and books and relationships between employees.

The database does not support supplier or shipping information. There is no store location or branch management because only one store is implied. There is no book categorization like genre or keywords. Also, if a customer wants to refund their book there is no return or refund tracking.
 
<img width="1712" height="1344" alt="image" src="https://github.com/user-attachments/assets/6e58c975-a0f0-47d3-98e0-bb812e414407" />

# Data Dictionary:
<img width="1492" height="484" alt="image" src="https://github.com/user-attachments/assets/1ee0cd4c-9706-4812-bf36-b7faf10e52e5" />
<img width="1462" height="400" alt="image" src="https://github.com/user-attachments/assets/89e6ce0c-3a25-4139-a340-072a494da54d" />
<img width="1490" height="432" alt="image" src="https://github.com/user-attachments/assets/453bf3a2-64e9-4340-9daa-4ee3a02bcc24" />
<img width="1488" height="384" alt="image" src="https://github.com/user-attachments/assets/81c33c4e-9442-4b1a-a649-93bfb3e02b3f" />
<img width="1482" height="478" alt="image" src="https://github.com/user-attachments/assets/862c2277-2bdf-4eeb-97c6-c8315542a188" />
<img width="1480" height="550" alt="image" src="https://github.com/user-attachments/assets/c09e4e9c-a8bc-4d3d-bd0c-80a4e0b8c9eb" />
<img width="1498" height="572" alt="image" src="https://github.com/user-attachments/assets/f72b8b32-6cf4-4c4d-99d2-30a9d0ab32ad" />
<img width="1506" height="606" alt="image" src="https://github.com/user-attachments/assets/fead99ff-067e-498e-9924-76c644b39670" />
<img width="1478" height="518" alt="image" src="https://github.com/user-attachments/assets/bb0d2b2f-0f16-4581-99fc-a224c65ed4d7" />
<img width="1502" height="434" alt="image" src="https://github.com/user-attachments/assets/62fd6993-b5ad-48d4-b9a4-8a93e9a74e38" />

# Queries:
1. Most Borrowed Actors
   
Question: Which authors were borrowed the most total units?

Query 1 allows managers to see which authors’ books have been borrowed or purchased the most overall. By calculating the total number of units sold for each author, managers can identify which authors are in the highest demand among customers. These insights help determine which authors’ books should be prioritized. Listing the results in descending order of total borrowed units makes it easy to see which authors generate the most interest and should receive the most attention.

Managerial Justification: Helps identify high demand authors for acquisition and promotion.

2. Customers With Orders but No Payments
   
Question: Which customers placed orders but have not made any payments?

Query 2 allows managers to identify customers who have placed orders but have not yet made any payments. By comparing the Order and Payment tables, the query finds all customers linked to existing orders that do not appear in the payment records. Listing the results by last and first name makes it easy for staff to locate and contact the appropriate customers for resolution.

Managerial Justification: Allows managers to monitor unpaid orders and follow up for overdue
payments.


3. Books Priced Below Average Payment
   
Question: Which books are priced below the overall average payment amount and have been
borrowed at least once?

Query 3 allows managers to identify books that are priced below the average payment amount but have still been borrowed or purchased at least once. By comparing each book’s price to the overall average payment, the query highlights titles that are both affordable and actively circulating. This helps managers recognize books that perform well, supporting decisions about pricing strategies, promotions, and restocking. Listing the results by book title makes it easy to review and select titles.

Managerial Justification: Helps managers identify affordable titles with active circulation.

4. Low Inventory Alert
   
Question: Which books have fewer than five copies available?

Query 4 allows managers to identify books with fewer than five copies remaining in inventory, signaling titles that may soon go out of stock. By joining the Book and Inventory tables, the query retrieves each book’s title, ISBN, and current stock level to provide a clear view of low inventory items. This helps managers take action by ordering additional copies of popular or essential books before they run out. Listing the results in ascending order of stock quantity and then by book title makes it easy to prioritize restocking efforts efficiently.

Managerial Justification: Enables proactive restocking of popular or low stock titles.

5. Monthly Payment Totals
    
Question: What is the total payment amount collected each month?

Query 5 allows managers to view the total payment amounts collected each month, providing a picture of monthly revenue trends. By grouping payment data by month and summing the total amounts, the query helps identify patterns in sales performance over time. This information supports managers to make informed decisions about marketing, staffing, and inventory based on periods of high or low revenue. Listing the results in chronological order allows for easy tracking.

Managerial Justification: Tracks monthly revenue trends to support financial planning.

6. Loyal Customers
    
Question: Which customers have placed at least five orders and how much have they paid in
total?

Query 6 allows managers to identify loyal customers who have placed five or more orders and to see the total amount each has paid. By joining the Customer, Order, and Payment tables, the query calculates both the number of distinct orders per customer and their total spending. This helps managers recognize people who contribute significantly to sales. Sorting by total amount paid and number of orders highlights the most valuable customers first for targeted engagement.

Managerial Justification: Helps identify loyal patrons for rewards or membership incentives.

7. Manager and Staff Counts
    
Question: How many direct reports does each manager have?

Query 7 allows managers to see how many employees directly report to each manager. By performing a self-join on the Employee table, the query links each manager to their direct reports and counts how many staff members fall under their supervision. This information helps with balancing, planning, and performance evaluations, ensuring that management responsibilities are distributed effectively. Sorting the results by the number of direct reports highlights managers overseeing the largest teams, allowing leadership to assess the teams.

Managerial Justification: Assists in workload balancing and team size analysis.

8. Top Rated Books
    
Question: Which books have an average rating above 4.5 and at least ten reviews?

Query 8 allows managers to identify top-rated books that have received an average rating above 4.5 and at least ten reviews. This helps managers pinpoint high-quality, well-reviewed books that are popular among customers. Such insights can be used to promote these titles, feature them in marketing campaigns, or prioritize them for restocking. Sorting the results by highest average rating and review count ensures the most positively reviewed books appear first for easy recognition.

Managerial Justification: Identifies high quality titles worth recommending or featuring.

9. Inactive Customers
    
Question: Which customers have never placed an order?

Query 9 allows managers to identify customers who have never placed an order, helping pinpoint inactive users. By checking for customers that do not appear in the Order table, the query isolates those who have registered but have not made any purchases. This information supports targeted marketing aimed at encouraging these customers to place their first order through discounts, recommendations, or promotional emails. Sorting the results alphabetically by last and first name makes it easy for staff to review and contact potential customers for engagement efforts.

Managerial Justification: Supports targeted outreach campaigns to encourage engagement.

10.  Most Borrowed Publishers
    
Question: Which publishers have the most borrowed books overall?

Query 10 allows managers to determine which publishers’ books have been borrowed or sold the most overall by summing the total quantities of books associated with each publisher. By joining the Publisher, Book, and Order_Item tables, the query connects each publisher to the books they produce, and the number of units borrowed. The insights support decisions related to performance reviews, purchasing agreements, and partnership negotiations. Sorting results in descending order of total borrowed units ensures that the most successful publishers are highlighted first for strategic focus.

Managerial Justification: Helps evaluate publisher performance and negotiate partnerships.

# Database Information:

<img width="760" height="393" alt="image" src="https://github.com/user-attachments/assets/873930eb-ddd5-4252-ac02-f5a5293a7ca7" />






