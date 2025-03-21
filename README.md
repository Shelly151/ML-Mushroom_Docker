# **🚀 ML Model Deployment Using Docker 🧠🐳**  

This project demonstrates how to **build and deploy** a Machine Learning (ML) model using **Docker**.  
The model is trained on the **mushrooms dataset**, and we use **Streamlit** to create an interactive web UI for predictions.  

---

## **📚 Prerequisites**  

Before you begin, make sure you have the following installed:  

✅ **Docker** 🐳  
✅ **Python (3.9+)** 🐖  
✅ **ML Dependencies** (listed in `requirements.txt`)  

---

## **📌 Installation & Setup**  

### **1️⃣ Verify Docker & Python Installation**  

Check if **Docker** and **Python** are installed by running:  

```bash
docker --version  
python --version  
```

---

### **2️⃣ Clone the Repository & Prepare Files**  

Clone the **GitHub repository** containing the ML model (`app.py`) and dataset (`mushrooms.csv`):  

```bash
git clone https://github.com/yourusername/ml-docker-project.git  
cd ml-docker-project  
```

Create a `requirements.txt` file to manage dependencies:  

```bash
pip freeze > requirements.txt  
```

---

### **3️⃣ Create the Dockerfile**  

A **Dockerfile** defines the environment for running the ML model. Here’s an optimized version:  

```dockerfile
# Use a lightweight Python image  
FROM python:3.9-slim  

# Set the working directory  
WORKDIR /app  

# Copy necessary files  
COPY app.py /app  
COPY requirements.txt /app  
COPY mushrooms.csv /app  

# Upgrade pip and install dependencies  
RUN python -m pip install --upgrade pip  
RUN pip install -r requirements.txt  

# Expose the port for Streamlit  
EXPOSE 8501  

# Run the application using Streamlit  
ENTRYPOINT ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]  
```

---

### **4️⃣ Build the Docker Image**  

Run the following command to build the Docker image:  

```bash
docker build -t ml-model .
```

Verify the image creation:  

```bash
docker images  
```

---

### **5️⃣ Run the ML Model in a Docker Container**  

Start the container and expose it on port **8501**:  

```bash
docker run -p 8501:8501 ml-model  
```

---

### **6️⃣ Access the Web Interface**  

Once the container is running, open your browser and go to:  

🔗 **http://localhost:8501**  

You should now see the ML model’s **interactive UI** built with **Streamlit**! 🎉  

---

## **🚀 Pushing the Container to Docker Hub**  

### **1️⃣ Log in to Docker Hub**  

```bash
docker login  
```

### **2️⃣ Tag the Docker Image**  

Replace `yourdockerhubusername` with your **actual** Docker Hub username:  

```bash
docker tag ml-model yourdockerhubusername/ml-model  
```

### **3️⃣ Push the Image to Docker Hub**  

```bash
docker push yourdockerhubusername/ml-model  
```

---

## **🏆 Conclusion**  

💠 You have successfully **containerized** and **deployed** an ML model using **Docker**!  
This setup ensures **scalability**, **portability**, and **easy deployment** in production environments.  

🔹 **Next Steps**:  
- Deploy the container on **cloud platforms** (AWS, GCP, Azure) 🌍  
- Optimize performance using **GPU acceleration** 🚀  
- Extend functionality with **REST APIs (FastAPI, Flask)** 🔦  

---

💡 **Happy Coding!** 💡 🚀🐳🧠
