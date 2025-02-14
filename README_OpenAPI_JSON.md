# 🔍 OpenAPI (Swagger) dengan Format JSON di VS Code

## 📌 Persyaratan  
- **VS Code**  
- **Ekstensi OpenAPI (Swagger) Editor**  
- **CodeIgniter 3**  

---

## **1️⃣ Instalasi Ekstensi OpenAPI di VS Code**  
1. **Buka VS Code**  
2. **Masuk ke Extensions (`Ctrl + Shift + X`)**  
3. **Cari ekstensi**: `OpenAPI (Swagger) Editor`  
4. **Klik Install**  

---

## **2️⃣ Buat File OpenAPI dalam Format JSON**  
Buat file `swagger.json` di dalam folder `application/swagger/` dan isi dengan:  
```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "API CodeIgniter 3 dengan JWT",
    "description": "Dokumentasi API dengan JWT Authentication",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "http://localhost/your_project/api/"
    }
  ],
  "paths": {
    "/auth/login": {
      "post": {
        "summary": "Login untuk mendapatkan JWT Token",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "type": "object",
                "properties": {
                  "email": {
                    "type": "string",
                    "example": "user@example.com"
                  },
                  "password": {
                    "type": "string",
                    "example": "password123"
                  }
                }
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Berhasil mendapatkan token",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "token": {
                      "type": "string"
                    }
                  }
                }
              }
            }
          },
          "401": {
            "description": "Kredensial tidak valid"
          }
        }
      }
    },
    "/user/profile": {
      "get": {
        "summary": "Mendapatkan profil pengguna",
        "security": [
          {
            "bearerAuth": []
          }
        ],
        "responses": {
          "200": {
            "description": "Data pengguna"
          },
          "401": {
            "description": "Token tidak valid"
          }
        }
      }
    }
  },
  "components": {
    "securitySchemes": {
      "bearerAuth": {
        "type": "http",
        "scheme": "bearer",
        "bearerFormat": "JWT"
      }
    }
  }
}
```

---

## **3️⃣ Menampilkan Preview Swagger di VS Code**  
1. **Buka file `swagger.json`**  
2. Tekan **`Ctrl + Shift + P`** untuk membuka Command Palette  
3. Cari **"OpenAPI Preview"** dan pilih **"Preview Swagger File"**  
4. Swagger UI akan ditampilkan langsung di VS Code  

---

## **4️⃣ Menampilkan Swagger di Browser**  
Jika ingin melihat Swagger di browser:  
1. Jalankan server CodeIgniter  
2. Buka `public/swagger-ui/dist/index.html`  
3. Masukkan URL file JSON:  
   ```
   http://localhost/your_project/application/swagger/swagger.json
   ```  
4. Klik **"Explore"** untuk melihat dokumentasi API  

---

Sekarang Anda dapat menggunakan OpenAPI (Swagger) dalam format **JSON** dan melihat preview langsung di **VS Code** atau **browser**! 🚀  
