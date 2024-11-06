# Fitness Unlimited Database Customization - Practice Mini Case Study for Schema Integration

This project demonstrates a database schema integration for **Fitness Unlimited**, a leading provider of fitness centers offering diverse programs and memberships. Fitness Unlimited’s operational efficiency relies on a retail database to track service and merchandise sales. In this assignment, I've customized the database design to align with the company's specific business requirements. 

## Revised Entity-Relationship Diagram (ERD)
The ERD revision includes entities and relationships tailored to capture essential business dimensions, such as member details, services, and sales.

### Key Project Deliverables:
1. **Dimensions & Hierarchies:** 
   - Mapped dimensions include **Product** (Merchandise and Service categories), **Member**, **Date**, and **Franchise**.
   - Hierarchies are defined within each dimension (e.g., ServiceCategory ID > Name > Price).

2. **Measures & Aggregation Properties:**
   - Measures include **dollar amounts**, **names**, and **counts** in the Sales and Contains tables. Aggregations are designed to support both data mining and typical reporting needs.

3. **Grain Identification:**
   - The **Sales** table grain specifies each transaction, with each row representing a unique purchase of a product or service by a member, tracked by date and location.

4. **Star Schema Design for Inventory Analysis:**
   - A star schema with one central fact table, `FactSale`, and supporting dimension tables (`DimMember`, `DimFranchise`, `DimTime`, `DimMerchandise`, and `DimServiceCategory`) optimizes data retrieval.

### SQL Code for Database Setup:
```sql
-- Dimension Table: DimMember
CREATE TABLE DimMember (
    MmbrId INT PRIMARY KEY,
    MmbrName VARCHAR(100),
    MmbrZip VARCHAR(10),
    MmbrEmail VARCHAR(100),
    MmbrDate DATE,
    MemTypeId INT,
    MemTypeName VARCHAR(50),
    MemTypePrice DECIMAL(10, 2)
);

-- Additional dimension and fact tables omitted for brevity
