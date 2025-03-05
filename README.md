### **📌 Step 1: Create a README File**  
A `README.md` file helps new users set up and use the project without confusion.

---

### **📄 `README.md`**
📍 Save this file in your project directory (`C:\solr_project\README.md`):

```md
# 📌 Apache Solr Data Indexing & Metadata Extraction

## 🚀 Overview
This project provides an **interactive Streamlit UI** for indexing JSON data into **Apache Solr**, extracting metadata, and retrieving random documents. It simplifies Solr operations with an easy-to-use interface.

---

## 📂 Project Structure

```
C:\solr_project\
│── app.py                   # Streamlit UI for Solr
│── solr_metadata_extractor.py # Python script to extract metadata
│── solr_json_transformer.py  # Transforms complex JSON data for Solr
│── data.json                 # Sample data for indexing
│── solr_fixed.json           # Transformed JSON for Solr indexing
│── solr_metadata.json        # Metadata output file
│── solr_metadata2.json       # Sample complex metadata
│── solr_metrics.db           # Solr database (if applicable)
│── requirements.txt          # Dependencies
│── README.md                 # Documentation
```

---

## 🔹 **1. Install Apache Solr**
### **📥 Step 1: Download & Install**
1. Download Apache Solr from the official website:  
   👉 [https://solr.apache.org/downloads.html](https://solr.apache.org/downloads.html)
2. Extract it to a directory (e.g., `C:\Users\acer\Downloads\solr-9.8.0`).
3. Open **Command Prompt** and navigate to the Solr `bin` directory:
   ```sh
   cd C:\Users\acer\Downloads\solr-9.8.0\bin
   ```

### **▶ Step 2: Start Solr**
Run:
```sh
solr start
```
To run Solr in the foreground for debugging:
```sh
solr start -f
```

### **📌 Step 3: Verify Solr is Running**
Open the browser and go to:  
👉 **[http://localhost:8983/solr](http://localhost:8983/solr)**  
If Solr is running, the admin UI should be visible.

### **📌 Step 4: Create a Core**
A **core** is where Solr stores indexed data. Create a core named `mycore`:
```sh
solr create -c mycore
```
To list existing cores:
```sh
solr list
```

---

## 🔹 **2. Index Data into Solr**
### **📥 Step 1: Prepare JSON Data**
Use `data.json` as an example:
```json
[
    {
        "id": "1",
        "title": "First Document",
        "author": "Alice",
        "category": "Tech"
    },
    {
        "id": "2",
        "title": "Second Document",
        "author": "Bob",
        "category": "Science"
    }
]
```

### **📌 Step 2: Upload JSON Data to Solr**
Run:
```sh
Invoke-WebRequest -Uri "http://localhost:8983/solr/mycore/update?commit=true" `
    -Method Post `
    -Headers @{"Content-Type" = "application/json"} `
    -InFile "C:\solr_project\data.json"
```
Check indexed data:
```sh
Invoke-WebRequest -Uri "http://localhost:8983/solr/mycore/select?q=*:*&wt=json&indent=true" | Select-Object -ExpandProperty Content
```

---

## 🔹 **3. Extract Solr Metadata Using Python**
### **📌 Step 1: Install Dependencies**
Run:
```sh
pip install -r C:\solr_project\requirements.txt
```

### **📌 Step 2: Run the Metadata Extraction Script**
```sh
python C:\solr_project\solr_metadata_extractor.py
```
This will generate `solr_metadata.json` containing:
```json
{
    "core_name": "mycore",
    "index_size_bytes": 10538,
    "num_documents": 4,
    "sample_documents": [
        {
            "id": "2",
            "title": ["Second Document"],
            "author": ["Bob"],
            "category": ["Science"]
        },
        {
            "id": "3",
            "title": ["Third Document"],
            "author": ["Charlie"],
            "category": ["History"]
        }
    ]
}
```

---

## 🔹 **4. Run Streamlit UI**
### **📌 Step 1: Start the UI**
Run:
```sh
cd C:\solr_project
streamlit run app.py
```
This opens an interactive web app in your browser.

### **📌 Step 2: Features of the UI**
- **Fetch Solr Metadata** 📊
- **Extract Sample Documents** 📝
- **Upload and Index JSON Data** 📂
- **Secure Login with Authentication** 🔑

---

## 🔹 **5. Transform Complex JSON for Solr**
For complex JSON data, use `solr_json_transformer.py`:
```sh
python C:\solr_project\solr_json_transformer.py
```
This converts `solr_metadata2.json` into `solr_fixed.json` for indexing.

---

## 🔹 **6. Troubleshooting**
### ❌ **Solr Not Starting?**
Try:
```sh
solr restart
```
Or check logs:
```sh
solr status
```

### ❌ **Cannot Connect to Solr?**
Make sure Solr is running and accessible at:
```sh
http://localhost:8983/solr
```

### ❌ **Dependencies Not Found?**
Reinstall:
```sh
pip install -r requirements.txt
```

---

## **📌 Summary**
✔ **Installed Solr & Created a Core**  
✔ **Indexed JSON Data into Solr**  
✔ **Extracted Metadata using Python**  
✔ **Launched a Streamlit UI for Solr**  
✔ **Transformed & Indexed Complex JSON Data**  

---

## 🎯 **Next Steps**
- Improve **Streamlit UI** with real-time updates 📊
- Automate **batch indexing of JSON files** 🔄
- Add **advanced search filters** for querying data 🔍

---

## **💡 Contributing**
Want to improve this project? Feel free to **fork** and contribute! 🤝

---

## **📄 License**
This project is licensed under **Apache License 2.0**.

---

**🎉 Happy Searching with Solr! 🚀**
```

---

### **📌 Step 2: Save & Share the README**
1. **Save the above content as `README.md`** in your project folder (`C:\solr_project\README.md`).
2. **New users can now follow the step-by-step setup without confusion!** ✅

🚀 Let me know if you need any improvements! 😊