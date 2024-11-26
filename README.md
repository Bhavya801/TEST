### **Get All Site Data**
- **Method:** `GET`
- **Endpoint:** `/siteData`
- **Description:** Retrieve comprehensive data related to the application’s site, including metadata, configuration, and summary statistics.
- **Request Parameters:** None.
- **Authentication:** Required. Pass the JWT token in the `Authorization` header.
  ```http
  Authorization: Bearer <token>
  ```
- **Response:**
  ```json
  {
    "site_name": "Example Site",
    "total_users": 1500,
    "total_cases": 200,
    "settings": {
      "allow_guest_access": false,
      "max_upload_size": "10MB"
    }
  }
  ```
- **Error Codes:**
  - `401 Unauthorized`: If the token is missing or invalid.
  - `500 Internal Server Error`: If there’s an issue fetching site data.
- **Use Case:** Use this endpoint to fetch high-level application data for dashboards or system administrators.

---

### **Get Site Data by Field Name**
- **Method:** `GET`
- **Endpoint:** `/siteData/{field_name}`
- **Description:** Fetch specific site data based on a given field name. This allows for focused queries, improving performance when only a subset of data is required.
- **Path Parameters:**
  - `field_name` (string): The key of the field you wish to retrieve.
- **Authentication:** Required. Pass the JWT token in the `Authorization` header.
- **Response:**
  ```json
  {
    "field_name": "total_users",
    "value": 1500
  }
  ```
- **Error Codes:**
  - `400 Bad Request`: If the `field_name` is invalid or missing.
  - `404 Not Found`: If the requested field does not exist.
- **Use Case:** Fetching specific data, such as user counts, for lightweight API calls or dynamic UI updates.

---

## **PDF Management Endpoints**

### **Download PDF**
- **Method:** `GET`
- **Endpoint:** `/pdf/download`
- **Description:** Download a PDF document stored in the system. The PDF file will be streamed as a response.
- **Request Parameters:** 
  - **Query Parameters:**
    - `file_id` (string): The unique identifier of the PDF to download.
- **Authentication:** Required.
- **Response:** A binary stream of the requested PDF file.
- **Headers:**
  ```http
  Content-Disposition: attachment; filename="example.pdf"
  ```
- **Error Codes:**
  - `400 Bad Request`: If `file_id` is missing or invalid.
  - `404 Not Found`: If the specified file does not exist.
  - `401 Unauthorized`: If authentication fails.
- **Use Case:** Enable users to download case-related documents or reports.

---

### **Upload PDF**
- **Method:** `POST`
- **Endpoint:** `/pdf/upload`
- **Description:** Upload a new PDF file to the system. This endpoint accepts multi-part form data for file uploads.
- **Request Headers:**
  ```http
  Authorization: Bearer <token>
  Content-Type: multipart/form-data
  ```
- **Request Body:**
  - `file` (file): The PDF file to upload.
  - Optional Metadata:
    ```json
    {
      "case_id": "12345",
      "description": "Legal document for case 12345"
    }
    ```
- **Response:**
  ```json
  {
    "message": "File uploaded successfully",
    "file_id": "abc123",
    "url": "/pdf/abc123"
  }
  ```
- **Error Codes:**
  - `400 Bad Request`: If the file is missing or not a valid PDF.
  - `401 Unauthorized`: If the token is missing or invalid.
  - `413 Payload Too Large`: If the file exceeds the maximum allowed size.
- **Use Case:** Allow users to upload case-related documents for storage or sharing.

---

### **Protect PDF**
- **Method:** `GET`
- **Endpoint:** `/pdf/protected`
- **Description:** Apply a security layer to a specific PDF document, such as password protection or restricted viewing.
- **Request Parameters:**
  - **Query Parameters:**
    - `file_id` (string): The unique identifier of the PDF to protect.
    - `password` (string, optional): The password to apply to the PDF.
- **Authentication:** Required.
- **Response:**
  ```json
  {
    "message": "PDF protected successfully",
    "file_id": "abc123"
  }
  ```
- **Error Codes:**
  - `400 Bad Request`: If the file ID is invalid or the protection parameters are incomplete.
  - `401 Unauthorized`: If authentication fails.
- **Use Case:** Provide added security for sensitive documents.

---

## **Case Management Endpoints**

### **Get Cases**
- **Method:** `GET`
- **Endpoint:** `/cases`
- **Description:** Retrieve a list of all cases in the system, with optional filters for pagination and searching.
- **Request Parameters:**
  - **Query Parameters:**
    - `page` (integer, optional): Page number for pagination.
    - `size` (integer, optional): Number of cases per page.
    - `status` (string, optional): Filter by case status (e.g., open, closed).
- **Authentication:** Required.
- **Response:**
  ```json
  {
    "total_cases": 500,
    "cases": [
      {
        "id": "case1",
        "title": "Case Title 1",
        "status": "open",
        "created_at": "2024-01-01T12:00:00Z"
      },
      {
        "id": "case2",
        "title": "Case Title 2",
        "status": "closed",
        "created_at": "2024-02-01T12:00:00Z"
      }
    ]
  }
  ```
- **Error Codes:**
  - `401 Unauthorized`: If the token is missing or invalid.
  - `500 Internal Server Error`: If there is an issue retrieving the cases.
- **Use Case:** Fetch cases for case management dashboards or listings.

---

Would you like me to continue expanding on the other endpoints, or focus on any specific API?
