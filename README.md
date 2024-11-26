# API Documentation

## **Base URL:** `/api/v1`

---

## **General Endpoints**

### **Health Check**
- **Method:** `GET`
- **Endpoint:** `/health/`
- **Description:** Check the status of the API.
- **Request Parameters:** None
- **Response:**
  ```json
  {
    "status": "healthy"
  }
  ```

---

## **User Endpoints**

### **Get User Data**
- **Method:** `GET`
- **Endpoint:** `/user`
- **Description:** Fetch the profile data of the logged-in user.
- **Request Parameters:** None
- **Response:**
  ```json
  {
    "id": "12345",
    "name": "John Doe",
    "email": "john.doe@example.com",
    "role": "user"
  }
  ```

### **Update User Profile**
- **Method:** `PATCH`
- **Endpoint:** `/user`
- **Description:** Update the profile of the logged-in user.
- **Request Body:**
  ```json
  {
    "name": "New Name",
    "email": "new.email@example.com"
  }
  ```
- **Response:**
  ```json
  {
    "message": "Profile updated successfully",
    "data": {
      "id": "12345",
      "name": "New Name",
      "email": "new.email@example.com"
    }
  }
  ```

---

## **Site Data Endpoints**

### **Get All Site Data**
- **Method:** `GET`
- **Endpoint:** `/siteData`
- **Description:** Retrieve all data related to the site.
- **Request Parameters:** None
- **Response:**
  ```json
  {
    "data": {
      "cases": 100,
      "users": 50,
      "other_field": "value"
    }
  }
  ```

### **Get Cases Count**
- **Method:** `GET`
- **Endpoint:** `/siteData/casesCount`
- **Description:** Fetch the total count of cases.
- **Request Parameters:** None
- **Response:**
  ```json
  {
    "cases_count": 100
  }
  ```

### **Get Specific Site Data**
- **Method:** `GET`
- **Endpoint:** `/siteData/{field_name}`
- **Description:** Retrieve specific data by field name.
- **Path Parameter:**
  - `field_name`: The name of the data field to retrieve.
- **Response:**
  ```json
  {
    "field_name": "users",
    "value": 50
  }
  ```

---

## **PDF Endpoints**

### **Download PDF**
- **Method:** `GET`
- **Endpoint:** `/pdf/download`
- **Description:** Download a PDF file.
- **Request Parameters:** None
- **Response:** Returns the PDF file as a download.

### **Upload PDF**
- **Method:** `POST`
- **Endpoint:** `/pdf/upload`
- **Description:** Upload a new PDF file.
- **Request Body:** `multipart/form-data`
  - `file`: PDF file to be uploaded.
- **Response:**
  ```json
  {
    "message": "PDF uploaded successfully",
    "file_url": "https://example.com/uploads/file.pdf"
  }
  ```

### **Protect PDF**
- **Method:** `GET`
- **Endpoint:** `/pdf/protected`
- **Description:** Protect a PDF with security features.
- **Request Parameters:** None
- **Response:**
  ```json
  {
    "message": "PDF is now protected"
  }
  ```

---

## **Case Endpoints**

### **Get All Cases**
- **Method:** `GET`
- **Endpoint:** `/cases`
- **Description:** Retrieve a list of all cases.
- **Request Parameters:** None
- **Response:**
  ```json
  {
    "cases": [
      {
        "id": "case_1",
        "title": "Case 1",
        "status": "open"
      },
      {
        "id": "case_2",
        "title": "Case 2",
        "status": "closed"
      }
    ]
  }
  ```

### **Get Case By UID**
- **Method:** `GET`
- **Endpoint:** `/case/{case_uid}`
- **Description:** Fetch details of a specific case by UID.
- **Path Parameter:**
  - `case_uid`: Unique identifier of the case.
- **Response:**
  ```json
  {
    "id": "case_1",
    "title": "Case 1",
    "status": "open",
    "details": "Details of the case"
  }
  ```

### **Get Cases By UIDs**
- **Method:** `GET`
- **Endpoint:** `/casesByUids`
- **Description:** Fetch multiple cases using their UIDs.
- **Request Parameters:** None
- **Response:**
  ```json
  {
    "cases": [
      {
        "id": "case_1",
        "title": "Case 1",
        "status": "open"
      },
      {
        "id": "case_2",
        "title": "Case 2",
        "status": "closed"
      }
    ]
  }
  ```

### **Get Case Detail**
- **Method:** `GET`
- **Endpoint:** `/caseDetail`
- **Description:** Fetch detailed information about a case.
- **Request Parameters:** None
- **Response:**
  ```json
  {
    "id": "case_1",
    "title": "Case 1",
    "details": "Details of the case",
    "attachments": ["attachment1.pdf", "attachment2.pdf"]
  }
  ```

---

## **Chat and Query Endpoints**

### **Chat**
- **Method:** `POST`
- **Endpoint:** `/chat`
- **Description:** Send a message and receive a response from the chat service.
- **Request Body:**
  ```json
  {
    "message": "What is the status of my case?"
  }
  ```
- **Response:**
  ```json
  {
    "response": "Your case is currently under review."
  }
  ```
