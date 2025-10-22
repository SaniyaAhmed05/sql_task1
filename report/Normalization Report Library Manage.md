**Normalization Report: Library Management System**



**1. Unnormalized Form (UNF)**

 

**| BookID | Title          | Author     | MemberID | MemberName | IssueDate  | ReturnDate | FineAmount |**

**| ------ | -------------- | ---------- | -------- | ---------- | ---------- | ---------- | ---------- |**

| B001   | "Database 101" | John Smith | M001     | Alice      | 2025-09-01 | 2025-09-15 | 10         |

| B001   | "Database 101" | John Smith | M002     | Bob        | 2025-09-05 | 2025-09-19 | 5          |

| B002   | "SQL Basics"   | Jane Doe   | M001     | Alice      | 2025-09-10 | 2025-09-24 | 0          |



**Analysis:**



* Redundancy: Repeated information such as Title, Author, MemberName leads to unnecessary duplication.



* Anomalies: Updating member details requires changes in multiple rows, risking inconsistency.



**2.** **First Normal Form (1NF):** Ensure that each column contains atomic values and each record is unique.

* Books Table:



**| BookID | Title          | Author**     |

| ------ | -------------- | ---------- |

| B001   | "Database 101" | John Smith |

| B002   | "SQL Basics"   | Jane Doe   |



* Members Table:



| **MemberID | MemberName** |

| -------- | ---------- |

| M001     | Alice      |

| M002     | Bob        |



**3. Second Normal Form (2NF):**Eliminate partial dependencies; ensure that all non-key attributes are fully dependent on the primary key.

* Fines Table:



| FineID | TransactionID | FineAmount |

| ------ | ------------- | ---------- |

| F001   | T001          | 10         |

| F002   | T002          | 5          |

| F003   | T003          | 0          |

Analysis:



* In the Transactions table, FineAmount depends on TransactionID, not on the composite key (BookID, MemberID).



**4. Third Normal Form (3NF)**: Eliminate transitive dependencies; ensure that non-key attributes are not dependent on other non-key attributes.

Analysis:



* In the Members table, MemberName depends on MemberID, which is acceptable.



No transitive dependencies exist in the current schema.



**Final Normalized Schema**



**Books Table:**

| BookID | Title          | Author     |

| ------ | -------------- | ---------- |

| B001   | "Database 101" | John Smith |

| B002   | "SQL Basics"   | Jane Doe   |



**Members Table:**



| MemberID | MemberName |

| -------- | ---------- |

| M001     | Alice      |

| M002     | Bob        |



**Transactions Table:**



**| TransactionID | BookID | MemberID | IssueDate  | ReturnDate |**

**| ------------- | ------ | -------- | ---------- | ---------- |**

| T001          | B001   | M001     | 2025-09-01 | 2025-09-15 |

| T002          | B001   | M002     | 2025-09-05 | 2025-09-19 |

| T003          | B002   | M001     | 2025-09-10 | 2025-09-24 |



**Fines Table:**



**| FineID | TransactionID | FineAmount |**

| ------ | ------------- | ---------- |

| F001   | T001          | 10         |

| F002   | T002          | 5          |

| F003   | T003          | 0          |











