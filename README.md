---

# **Case Navigator API Documentation**

### **Overview**
The Case Navigator API allows users to manage cases, retrieve detailed case information, interact via notes and chat, handle PDFs, manage bookmarks, and perform advanced queries. All endpoints require an `idToken` as a Bearer token in the `Authorization` header for authentication and access control.

**Header Requirement**:  
```http
Authorization: Bearer <idToken>
```

---

## **General**
### **Health Check**
- **Endpoint**: `GET /api/v1/health/`
- **Description**:  
  Checks if the service is operational. This endpoint can be used to verify that the API is accessible and functional.  
- **Authentication**: Required.

---

## **User Management**
### **Get User Data**
- **Endpoint**: `GET /api/v1/user`
- **Description**:  
  Retrieves the profile information of the currently logged-in user. This includes details like name, email, and any additional metadata.  
- **Authentication**: Requires `idToken`.

### **Update User Profile**
- **Endpoint**: `PATCH /api/v1/user`
- **Description**:  
  Updates the user's profile information. Only the fields specified in the request body will be updated, allowing partial updates (e.g., updating just the name or email).  
- **Authentication**: Requires `idToken`.

---

## **Site Data**
### **Get All Site Data**
- **Endpoint**: `GET /api/v1/siteData`
- **Description**:  
  Retrieves comprehensive data about the site, including statistics, metadata, or other relevant details related to cases and site operations.  
- **Authentication**: Requires `idToken`.

### **Get Cases Count**
- **Endpoint**: `GET /api/v1/siteData/casesCount`
- **Description**:  
  Provides the total number of cases available in the system. Useful for analytics and overview purposes.  
- **Authentication**: Requires `idToken`.

### **Get Site Data by Field**
- **Endpoint**: `GET /api/v1/siteData/{field_name}`
- **Description**:  
  Fetches specific site data corresponding to the provided field name. This can be used to retrieve targeted information or configuration settings.  
- **Path Parameter**:  
  - `field_name`: Name of the field for which data is requested.  
- **Authentication**: Requires `idToken`.

---

## **PDF Management**
### **Download PDF**
- **Endpoint**: `GET /api/v1/pdf/download`
- **Description**:  
  Allows users to download a PDF file from the system. The specific PDF to download is identified via query parameters.  
- **Authentication**: Requires `idToken`.

### **Upload PDF**
- **Endpoint**: `POST /api/v1/pdf/upload`
- **Description**:  
  Enables users to upload PDF files into the system for processing or storage.  
- **Request Body**: The uploaded file as a `multipart/form-data`.  
- **Authentication**: Requires `idToken`.

### **Protect PDF**
- **Endpoint**: `GET /api/v1/pdf/protected`
- **Description**:  
  Secures a PDF by applying protection features such as password encryption or access controls.  
- **Authentication**: Requires `idToken`.

---

## **Case Management**
### **Get All Cases**
- **Endpoint**: `GET /api/v1/cases`
- **Description**:  
  Retrieves a list of all cases, including metadata such as case IDs, names, and statuses.  
- **Authentication**: Requires `idToken`.

### **Get Case by UID**
- **Endpoint**: `GET /api/v1/case/{case_uid}`
- **Description**:  
  Fetches detailed information about a specific case identified by its unique ID.  
- **Path Parameter**:  
  - `case_uid`: Unique identifier for the case.  
- **Authentication**: Requires `idToken`.

### **Get Cases by UIDs**
- **Endpoint**: `GET /api/v1/casesByUids`
- **Description**:  
  Retrieves detailed information for multiple cases using their unique identifiers.  
- **Request Body**: A list of case UIDs.  
- **Authentication**: Requires `idToken`.

### **Get Case Details**
- **Endpoint**: `GET /api/v1/caseDetail`
- **Description**:  
  Provides comprehensive details about a specific case, including involved parties, timelines, and status updates.  
- **Authentication**: Requires `idToken`.

---

## **Chat Management**
### **Chat**
- **Endpoint**: `POST /api/v1/chat`
- **Description**:  
  Facilitates interaction through a chat interface related to a specific case. This can be used for queries, discussions, or retrieving insights about the case.  
- **Request Body**: Chat input or query details.  
- **Authentication**: Requires `idToken`.

---

## **Query and Embeddings**
### **Query**
- **Endpoint**: `POST /api/v1/query`
- **Description**:  
  Submits a query for data retrieval or analysis within the system.  
- **Request Body**: Query parameters and search criteria.  
- **Authentication**: Requires `idToken`.

### **Create Embeddings**
- **Endpoint**: `POST /api/v1/createEmbeddings`
- **Description**:  
  Generates embeddings for advanced data processing and machine learning models. Useful for improving search and recommendations.  
- **Authentication**: Requires `idToken`.

---

## **Bookmarks**
### **Get Bookmarks**
- **Endpoint**: `GET /api/v1/bookmark`
- **Description**:  
  Retrieves a list of cases or documents bookmarked by the user.  
- **Authentication**: Requires `idToken`.

### **Add Bookmark**
- **Endpoint**: `POST /api/v1/bookmark`
- **Description**:  
  Adds a new bookmark to the user's account.  
- **Request Body**: Details of the case or document to bookmark.  
- **Authentication**: Requires `idToken`.

### **Delete Bookmark**
- **Endpoint**: `DELETE /api/v1/bookmark`
- **Description**:  
  Removes an existing bookmark from the user's account.  
- **Authentication**: Requires `idToken`.

---

## **Notes Management**
### **Get Notes**
- **Endpoint**: `GET /api/v1/note`
- **Description**:  
  Retrieves notes related to cases. Notes may include user comments, observations, or case-specific annotations.  
- **Authentication**: Requires `idToken`.

### **Add Notes**
- **Endpoint**: `POST /api/v1/note`
- **Description**:  
  Adds a new note to a case.  
- **Request Body**: Note details, including the associated case ID and content.  
- **Authentication**: Requires `idToken`.

### **Update Notes**
- **Endpoint**: `PATCH /api/v1/note`
- **Description**:  
  Updates an existing note.  
- **Request Body**: Note ID and updated content.  
- **Authentication**: Requires `idToken`.

### **Delete Notes**
- **Endpoint**: `DELETE /api/v1/note`
- **Description**:  
  Deletes a specific note.  
- **Request Body**: Note ID.  
- **Authentication**: Requires `idToken`.

---

## **Case Manager**
### **Get Case Manager Details**
- **Endpoint**: `GET /api/v1/case_manager`
- **Description**:  
  Fetches details about the assigned case manager, including contact information and case assignments.  
- **Authentication**: Requires `idToken`.

### **Add Case Manager Details**
- **Endpoint**: `POST /api/v1/case_manager`
- **Description**:  
  Adds a new case manager to the system.  
- **Request Body**: Case manager details.  
- **Authentication**: Requires `idToken`.

### **Update Case Manager Details**
- **Endpoint**: `PATCH /api/v1/case_manager`
- **Description**:  
  Updates information about an existing case manager.  
- **Request Body**: Case manager ID and updated details.  
- **Authentication**: Requires `idToken`.

### **Delete Case Manager Details**
- **Endpoint**: `DELETE /api/v1/case_manager`
- **Description**:  
  Removes a case manager from the system.  
- **Request Body**: Case manager ID.  
- **Authentication**: Requires `idToken`.

---

